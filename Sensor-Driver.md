## Official ROS Driver

**1. Official ROS driver for Ouster sensors**
  * GitHub Link : https://github.com/ouster-lidar/ouster-ros/tree/ros2
  * The driver supports the following list of Ouster sensors:
    * OS0
    * OS1
    * OS2
    * OSDome
  * Driver Parameters
    The driver has several parameters that allow you to customize its behavior, all of these parameters are defined with the `driver_params.yaml` file found under `config` folder.
    The only required parameter is `sensor_hostname` which sets the sensor hostname or ip that you want to connect to through ouster-ros driver.

    Other notable parameters include:
  * **point_type**: This parameter allows to customize the point cloud that thE driver produces through its `/ouster/points` topics. Choose one of the following values:
      - `original`: This uses the original point representation `ouster_ros::Point` of the ouster-ros driver.
      - `native`: directly maps all fields as published by the sensor to an equivalent point cloud representation with the additon of ring and timestamp fields.
      - `xyz`: the simplest point type, only has {x, y, z}
      - `xyzi`: same as `xyz` point type but adds intensity (signal) field. thiS type is not compatible with the low data profile.
      - `xyzir`: same as `xyzi` type but adds ring (channel) field. this type is same as Velodyne point cloud type this type is not compatible with the low data profile.


