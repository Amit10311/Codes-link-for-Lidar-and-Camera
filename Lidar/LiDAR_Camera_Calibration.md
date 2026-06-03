**Awesome LiDAR Camera Calibration**

* https://github.com/Deephome/Awesome-LiDAR-Camera-Calibration


## Sensor Calibration Toolbox

### Toolbox Overview

| **Toolbox** | **Introduction** | **Note** |
|-------------|------------------|----------|
| [Apollo Sensor Calibration Tools](https://github.com/ApolloAuto/apollo/blob/master/docs/quickstart/apollo_2_0_sensor_calibration_guide.md) | Targetless method, no source code provided. | [CN](https://blog.csdn.net/learning_tortosie/article/details/82351553?utm_medium=distribute.pc_relevant.none-task-blog-baidujs_baidulandingword-0&spm=1001.2101.3001.4242) |
| [OpenCalib or SensorsCalibration toolbox](https://github.com/PJLab-ADG/SensorsCalibration) | Supports both target-based and target-less methods. Manual calibration is supported. | OpenCalib: A Multi-sensor Calibration Toolbox for Autonomous Driving |
| [tier4/CalibrationTools](https://github.com/tier4/CalibrationTools) | Target-based, manual calibration. | * |


1. **Apollo Sensor Calibration Tools**: This tool provides a **targetless calibration method** and is integrated into Apollo’s autonomous driving system. You can follow the official guide to use it, but note that the source code is not available.
   
2. **OpenCalib**: OpenCalib offers both **target-based and target-less calibration methods**. It is a more flexible solution for sensor calibration in autonomous vehicles. You can find detailed documentation and source code in the [OpenCalib GitHub repository](https://github.com/PJLab-ADG/SensorsCalibration)https://library.iterable.com/3110/20487/4646455447c643a9a24940b38f1e46af-306x160-1-copy-7.png.

3. **tier4/CalibrationTools**: This set of tools from **Tier 4** is designed for **target-based calibration** and includes manual methods. It's useful for fine-tuning sensor configurations in autonomous driving platforms. You can find the source code and documentation on the [Tier4 CalibrationTools GitHub repository](https://github.com/tier4/CalibrationTools).

Calibrate their LiDAR with cameras (RGB and thermal ones)
* https://github.com/Titou2222/calibration_pkg

4. **Automatic calibration between high-resolution LiDAR and camera in targetless scenes.**
   * Lidar Data Collection → Segmentation on Point Cloud → Edge Extraction → Rough Calibration  → Fine Calibration (Converged)
   * https://github.com/hku-mars/livox_camera_calib
   * https://github.com/yeyiru/livox_camera_calib_ros2
   * <img width="2109" height="674" alt="image" src="https://github.com/user-attachments/assets/8796242a-c1e3-448b-9906-f170f14dc68f" />


5. **`direct_visual_lidar_calibration`**
   * This package provides a toolbox for LiDAR-camera calibration.
   * **`Note:`** Works good in static Environment. Tested.
   * <img width="1979" height="506" alt="image" src="https://github.com/user-attachments/assets/51351c81-d0d6-4725-b234-de2f11cd97e2" />


6. **`ros2_calib` is a Multi-Sensor Calibration Tool using ROS2 mcap recordings with direct URDF export.**
   * https://github.com/ika-rwth-aachen/ros2_calib
   * Lidar - Lidar calib
   * Lidar - Camera Calib
   * **`Note:` Good for Manual Calib and development like product**
