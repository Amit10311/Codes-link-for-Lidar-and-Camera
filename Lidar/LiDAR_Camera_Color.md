# The Translation of the Distorted Image on the Undistorted Lidar Image

```python
#!/usr/bin/env python3
"""
Colorize a LiDAR point cloud using a calibrated camera image.

Inputs:
  - point cloud (any Open3D-readable format: .pcd, .ply, .xyz, ...)
  - image (.png/.jpg)
  - pinhole intrinsics (fx, fy, cx, cy) + distortion (k1, k2, p1, p2, k3)
  - T_lidar_camera : 4x4, lidar <- camera

Outputs:
  - colored point cloud (.ply)
"""

import argparse
import numpy as np
import cv2
import open3d as o3d


def load_point_cloud(path):
    """Load point cloud as (N, 3) float64 numpy array."""
    pcd = o3d.io.read_point_cloud(path)
    pts = np.asarray(pcd.points)
    if pts.size == 0:
        raise RuntimeError(f"No points loaded from {path}")
    return pts


def colorize(
    points_lidar,  # (N, 3) in lidar frame
    image_bgr,  # (H, W, 3) uint8
    K,  # (3, 3) intrinsics
    dist,  # (5,)   [k1, k2, p1, p2, k3]
    T_lidar_camera,  # (4, 4) lidar <- camera
    default_color=(0, 0, 0),  # for points without a valid pixel
    keep_uncolored=False,  # if False, drop points without a color
):
    H, W = image_bgr.shape[:2]

    # We need T_camera_lidar to bring points from lidar -> camera frame.
    T_camera_lidar = np.linalg.inv(T_lidar_camera)
    R = T_camera_lidar[:3, :3]
    t = T_camera_lidar[:3, 3]

    # 1. Transform points: P_cam = R * P_lidar + t
    pts_cam = points_lidar @ R.T + t  # (N, 3)

    # 2. Drop points behind the camera (z <= 0)
    z = pts_cam[:, 2]
    in_front = z > 0.05  # small margin to avoid div-by-zero
    pts_cam = pts_cam[in_front]
    valid_indices = np.where(in_front)[0]

    # 3. Project with cv2.projectPoints (handles distortion correctly)
    #    cv2.projectPoints expects (N, 1, 3). rvec/tvec = 0 because pts are already in camera frame.
    pts_cam_reshaped = pts_cam.reshape(-1, 1, 3).astype(np.float64)
    img_pts, _ = cv2.projectPoints(
        pts_cam_reshaped,
        rvec=np.zeros(3),
        tvec=np.zeros(3),
        cameraMatrix=K,
        distCoeffs=dist,
    )
    img_pts = img_pts.reshape(-1, 2)  # (N_in_front, 2)  pixel coords (u, v)

    # 4. Keep only points that fall inside the image rectangle
    u = img_pts[:, 0]
    v = img_pts[:, 1]

    # Round to integer pixel coords, THEN bounds-check.
    u_int = np.round(u).astype(np.int32)
    v_int = np.round(v).astype(np.int32)
    inside = (u_int >= 0) & (u_int < W) & (v_int >= 0) & (v_int < H)

    # 5. Sample colors
    colors = np.full((points_lidar.shape[0], 3), default_color, dtype=np.float64)

    u_in = u_int[inside]
    v_in = v_int[inside]
    bgr = image_bgr[v_in, u_in]  # (M, 3) uint8 in BGR

    # Open3D wants RGB float in [0, 1]
    rgb = bgr[:, ::-1].astype(np.float64) / 255.0

    colored_global_idx = valid_indices[inside]
    colors[colored_global_idx] = rgb

    if keep_uncolored:
        return points_lidar, colors, colored_global_idx

    # Drop points without a color
    mask = np.zeros(points_lidar.shape[0], dtype=bool)
    mask[colored_global_idx] = True
    return points_lidar[mask], colors[mask], colored_global_idx


def main():
    ap = argparse.ArgumentParser()
    ap.add_argument("--cloud", required=True, help="input point cloud (.pcd/.ply/.xyz)")
    ap.add_argument("--image", required=True, help="input camera image")
    ap.add_argument("--out", required=True, help="output colored .ply")
    ap.add_argument("--fx", type=float, required=True)
    ap.add_argument("--fy", type=float, required=True)
    ap.add_argument("--cx", type=float, required=True)
    ap.add_argument("--cy", type=float, required=True)
    ap.add_argument(
        "--dist", nargs=5, type=float, default=[0, 0, 0, 0, 0], metavar=("k1", "k2", "p1", "p2", "k3")
    )
    ap.add_argument("--extrinsic", required=True, help="4x4 T_lidar_camera as a .npy or .txt file")
    ap.add_argument(
        "--keep-uncolored", action="store_true", help="keep points outside the image (colored black)"
    )
    args = ap.parse_args()

    # --- load inputs ---
    points = load_point_cloud(args.cloud)
    image = cv2.imread(args.image, cv2.IMREAD_COLOR)
    if image is None:
        raise RuntimeError(f"Failed to load image: {args.image}")

    K = np.array(
        [
            [args.fx, 0.0, args.cx],
            [0.0, args.fy, args.cy],
            [0.0, 0.0, 1.0],
        ]
    )
    dist = np.array(args.dist, dtype=np.float64)

    if args.extrinsic.endswith(".npy"):
        T_lidar_camera = np.load(args.extrinsic)
    else:
        T_lidar_camera = np.loadtxt(args.extrinsic)
    assert T_lidar_camera.shape == (4, 4), "extrinsic must be 4x4"

    print(f"Loaded {points.shape[0]} points and image {image.shape[1]}x{image.shape[0]}")

    # --- colorize ---
    pts_out, colors_out, idx = colorize(
        points,
        image,
        K,
        dist,
        T_lidar_camera,
        keep_uncolored=args.keep_uncolored,
    )
    print(f"Colored {len(idx)} of {points.shape[0]} points ({100.0 * len(idx) / points.shape[0]:.1f}%)")

    # --- save ---
    out_pcd = o3d.geometry.PointCloud()
    out_pcd.points = o3d.utility.Vector3dVector(pts_out)
    out_pcd.colors = o3d.utility.Vector3dVector(colors_out)
    o3d.io.write_point_cloud(args.out, out_pcd)
    print(f"Wrote {args.out}")


if __name__ == "__main__":
    main()
```

Command 

```bash
python3 colorize_cloud.py \
--cloud   input_bag_25_06_10_30_3_0.db3.ply \
--image   input_bag_25_06_10_30_3_0.db3.png \
--out     colored.ply \
--fx 796.911879 --fy 797.153541 --cx 640.098823 --cy 362.052892 \
--dist -0.373066 0.192653 -0.000307 -0.000207 -0.059007 \
--extrinsic ../scene_1_18_06_14_18_near_ir/T_lidar_camera.txt.txt

python3 colorize_cloud_undistorted.py \
--cloud   input_bag_25_06_10_30_3_0.db3.ply \
--image   left0000.jpg \
--out     colorize_cloud_undistorted.ply \
--fx 796.911879 --fy 797.153541 --cx 640.098823 --cy 362.052892 \
--dist -0.373066 0.192653 -0.000307 -0.000207 -0.059007 \
--extrinsic T_lidar_camera.txt


0.321071  0.127532 -0.938429  0.14397800
0.939477 -0.167994  0.298599  0.50876100
-0.119569 -0.977504 -0.173751 -0.13095400
0         0         0         1
```

```bash
python3 -c "import open3d as o3d; o3d.visualization.draw_geometries([o3d.io.read_point_cloud('colored.ply')])"

python3 -c "import open3d as o3d; o3d.visualization.draw_geometries([o3d.io.read_point_cloud('colorize_cloud_undistorted.ply')])"
```
