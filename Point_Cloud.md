## Point Cloud Documentation and References

**What is a Point Cloud?**

A point cloud is a collection of data points in 3D space, often representing the external surface of an object or environment. 
Each point contains coordinates (x, y, z) and may also include additional information such as intensity, color, or normal vectors.

**Point Cloud Formats**

1. **.PCD** (Point Cloud Data) : Native format for the Point Cloud Library.
2. **.PLY** (Polygon File Format) : Widely supported format with additional support for color and other attributes.
3. **.LAS/.LAZ** : Common formats for Lidar point cloud data.
4. **.OBJ** : Often used for 3D models that include surfaces.
      
## 1. **Popular Libraries for Handling Point Clouds**

1. **Point Cloud Library (PCL) tutorials**
    - A comprehensive library for working with 3D point clouds.
    - **Link :** https://pcl.readthedocs.io/projects/tutorials/en/master/
    - **Link :** https://pointclouds.org/
    - **Link : https://github.com/oxon-612/PointCloud_Tutorial**
    - Features:
        - Filtering, segmentation, and surface reconstruction.
        - Point cloud registration and alignment.
        - Point feature extraction.

2. **Open3D**:
    - A modern library for 3D data processing.
    - Website: http://www.open3d.org/
    - Features:
        - Visualization.
        - Point cloud manipulation.
        - Integration with machine learning tools.
          

3. **Pytorch3D**:
    - A library for deep learning with 3D data, including point clouds.
    - Website: https://pytorch3d.org/


## 2. PCL with ROS 2

1. **Full PCL Tutorial for Robotics in ROS / Master Point Cloud Processing for Industrial Applications**
   - **https://www.youtube.com/watch?v=_FbbCxYjvoc**

2. **Tutorial for using Point Cloud Library (PCL) with ROS 2.**
   - `GitHub :` https://github.com/adrian-soch/pcl_tutorial
  
3. **PCL basic introduction and usage tutorial examples** (imp)*
   - `GitHub :` https://gitee.com/gwmunan/pcl_tutorials

4. **A template ROS2 C++ node to test a PCL Pointcloud2 processing**
   - `GitHub :` https://github.com/GitRepJo/pcl_example

5. **pointcloud_to_grid ROS 2 package**
   - `GitHub :` https://github.com/jkk-research/pointcloud_to_grid
      
6. **Point Cloud Registration: Papers and Codes**
   - `GitHub :` https://github.com/GeorgeDu/point-cloud-registration
  
7. **ROS2 Point Cloud Clustering and Segmentation for Autonomous Behaviour**
   - `GitHub :` https://github.com/noshluk2/ROS2-Point-Cloud-Clustering-and-Segmentation-for-Autonomous-Behaviour 

## 3. Aligning and registering 3D point clouds

1. Iterative Closest Point (ICP)

2. Normal Distributions Transform (NDT)

3. Generalized Iterative Closest Point (GICP) algorithm
    - A collection of GICP-based fast point cloud registration algorithms
    - https://github.com/koide3/fast_gicp

4. This package provides an OpenMP-boosted Normal Distributions Transform (and GICP) algorithm derived from pcl.
    - https://github.com/koide3/ndt_omp 


  
## **4. Algorithms and Methods for Point Cloud Processing**

### **4.1. Voxel-Based Methods**

These methods utilize voxel grids for efficient 3D object detection and processing.

- **Voxel Field Fusion (VFF): Voxel Field Fusion for 3D Object Detection**
    - **Description**: Maintains cross-modality consistency by representing and fusing augmented image features as rays in the voxel field.
    - **Code**: VFF Repository (https://github.com/dvlab-research/VFF)
     * ![image](https://user-images.githubusercontent.com/20908007/216046489-825042e2-4e59-4bdc-80f9-572b55d68cd9.png)

- **PIXOR**: Real-time 3D Object Detection from Point Clouds
    - **Paper**: https://arxiv.org/pdf/1902.06326.pdf
    - **Code**: https://github.com/philip-huang/PIXOR
      
- **PointPillars**: Fast Encoders for Object Detection from Point Clouds
    - **Paper**: PointPillars Paper (https://arxiv.org/pdf/1812.05784.pdf)
    - **Code**:
        - Second.pytorch (https://github.com/nutonomy/second.pytorch)
        - CUDA-PointPillars (https://github.com/NVIDIA-AI-IOT/CUDA-PointPillars)

### **4.2. Point-Based Methods**
* Suitable for in-door scenes (high object density) not for out-door ( large scale point clouds). 
* These methods process raw point clouds directly and are often suitable for high-density, indoor scenes.

- **PointNet++**: Deep Hierarchical Feature Learning on Point Sets in a Metric Space (2017)
    - **Paper**: PointNet++ Paper (https://arxiv.org/pdf/1706.02413.pdf)
    - **Code**: PointNet++ Repository (https://github.com/charlesq34/pointnet2)
      
- **PointRCNN**: 3D Object Proposal Generation and Detection from Raw Point Cloud
    - **Paper**: PointRCNN Paper (https://arxiv.org/pdf/1812.04244.pdf)
    - **Description**: Two-stage framework: bottom-up 3D proposal generation and proposal refinement for final detection.
    - **Code**: PointRCNN Repository (https://github.com/sshaoshuai/PointRCNN)

### **4.3. Other Tools and Frameworks**

Additional frameworks and resources for advanced point cloud processing.

- **VoxelNet**: End-to-End Learning for Point Cloud-Based 3D Object Detection
    - **Code**: VoxelNet Repository (https://github.com/qianguih/voxelnet)
      
- **OpenPCDet**: LiDAR-Based 3D Object Detection
    - **Description**: Open-source project for LiDAR-based detection.
    - **Code**: OpenPCDet Repository (https://github.com/open-mmlab/OpenPCDet)
      
- **General-Purpose Point Cloud Feature Extractor (G3DNet)**
  
    - **Code**: G3DNet Repository (https://github.com/WDot/G3DNet)
- 3D Machine Learning 201 Guide: Point Cloud Semantic Segmentation
    - https://lnkd.in/dv88uk39





## **References for Learning and Documentation**

1. **Books**:
    - "3D Point Cloud Processing: Advances in Machine Learning and Signal Processing" by Zhiyong Yuan and Weiwei Wan.
    - "Point Cloud Data Analysis" by Masatoshi Kaneko.
      
2. **Courses**:
    - **Coursera**: [Computer Vision and Lidar Sensor Fusion](https://www.coursera.org/learn/sensor-fusion-perception).
    - **Udemy**: Point Cloud Processing with Python.
      
3. **Research Papers**:
    - **"PointNet: Deep Learning on Point Sets for 3D Classification and Segmentation"** by Qi et al.
    - **"PointNet++: Deep Hierarchical Feature Learning on Point Sets in a Metric Space"** by Qi et al.


