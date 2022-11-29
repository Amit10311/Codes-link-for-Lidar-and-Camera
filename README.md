# Codes and Research paper links for Lidar and Camera
Codes links for implementation on LiDAR and Camera

* https://modelnet.cs.princeton.edu/


## LiDAR

1. Codes for "Learning Lightweight Lane Detection CNNs by Self Attention Distillation" 
    * https://github.com/cardwing/Codes-for-Lane-Detection
    
2. Spatial CNN for Traffic Lane Detection 
   * https://github.com/XingangPan/SCNN 
   
3. See Eye to Eye: A Lidar-Agnostic 3D Detection Framework for Unsupervised Multi-Target Domain Adaptation
   * https://arxiv.org/pdf/2111.09450.pdf
   * `Code :` https://github.com/darrenjkt/SEE-MTDA
   
4. Simultaneous Location of Rail Vehicles and Mapping of Environment with Multiple LiDARs
   * https://arxiv.org/pdf/2112.13224.pdf 

5. Point-to-Voxel Knowledge Distillation for LiDAR Semantic Segmentation (CVPR 2022)
   * https://github.com/cardwing/Codes-for-PVKD

6. V2X-ViT: Vehicle-to-Everything Cooperative Perception with Vision Transformer (ECCV 2022)
   * https://github.com/DerrickXuNu/v2x-vit



## LiDAR-Inertial Odometry
Father of LIDAR and IMU integration  
  * https://www.researchgate.net/profile/Fu-Zhang-14

1. **LIO-Livox** (A Robust LiDAR-Inertial Odometry for Livox LiDAR)
   * `Code:` https://github.com/Livox-SDK/LIO-Livox


2. **LIO-mapping:** A Tightly Coupled 3D Lidar and Inertial Odometry and Mapping Approach --  ICRA 2019
   * `Code:` https://github.com/hyye/lio-mapping
     
     
3. LOAM_NOTED
   * `Code:` https://github.com/cuitaixiang/LOAM_NOTED

4. **FAST-LIO** Robust Real-time LiDAR-inertial Initialization 
   * `Code:` https://github.com/hku-mars/FAST_LIO
   * Fast LiDAR-Inertial Odometry is a computationally efficient and robust LiDAR-inertial odometry package. 
     * It fuses LiDAR feature points with IMU data using a tightly-coupled iterated extended Kalman filter to allow robust navigation in fast-motion, noisy or cluttered environments where degeneration occurs. 

5. **FAST-LIO2**: Fast Direct LiDAR-inertial Odometry 
   * https://arxiv.org/pdf/2107.06829.pdf 
   * `Code :` https://github.com/hku-mars/FAST_LIO  (2021-07-05 Update) 


## Camera
1. zed-examples
   * `Code:` https://github.com/Amit10311/zed-examples



## LiDAR-Camera
1. A Deep Learning Approach for LiDAR Resolution-Agnostic Object Detection 
   * https://hal.archives-ouvertes.fr/hal-03485613/document  (2021)
   * ![image](https://user-images.githubusercontent.com/20908007/204545251-ece1f16f-ff77-417d-818c-ddfbb045c227.png)

2. Camera LiDAR Calibration ROS Package Tutorial 
   * The full paper is accessible at: https://arxiv.org/abs/2103.12287
   * The code is available at: https://github.com/acfr/cam_lidar_calibration

 


## Point Cloud

1. **Voxel-Based Methods** 

* **VFF**: Voxel Field Fusion for 3D Object Detection
   * VFF aims to maintain cross-modality consistency by representing and Image fusing augmented image features as a ray in the voxel field.
   * `Code:` https://github.com/dvlab-research/VFF
   
* **PIXOR :** Real-time 3D Object Detection from Point Clouds
   * https://arxiv.org/pdf/1902.06326.pdf
   * `Code :` https://github.com/philip-huang/PIXOR

*  **PointPillars :** Fast Encoders for Object Detection from Point Clouds
   * https://arxiv.org/pdf/1812.05784.pdf
   *  `Code :` https://github.com/nutonomy/second.pytorch
   *  https://github.com/NVIDIA-AI-IOT/CUDA-PointPillars
   
2. **Point-base Methods :** Suitable for in-door scenes (high object density) not for out-door ( large scale point clouds) 

* **PointNet++ :** Deep Hierarchical Feature Learning on Point Sets in a Metric Space - 2017 
   * https://arxiv.org/pdf/1706.02413.pdf
   * `Code :` https://github.com/charlesq34/pointnet2 
   
* **PointRCNN :** 3D Object Proposal Generation and Detection from raw Point Cloud  
   *  https://arxiv.org/pdf/1812.04244.pdf 
   *  The whole framework is composed of two stages: stage-1 for the bottom-up 3D proposal generation and stage-2 for refining proposals in the canonical coordinates to obtain the final detection results. 
   * `Code :` https://github.com/sshaoshuai/PointRCNN 
   
3. 3D Machine Learning 201 Guide: Point Cloud Semantic Segmentation
   * https://lnkd.in/dv88uk39 
   
4. General-Purpose Point Cloud Feature Extractor
   * `Code:` https://github.com/WDot/G3DNet
   
5. **VoxelNet**: End-to-End Learning for Point Cloud Based 3D Object Detection
   * `Code:` https://github.com/qianguih/voxelnet
 
6. **OpenPCDet**
   * OpenPCDet is a clear, simple, self-contained open source project for LiDAR-based 3D object detection.
   * `Code:` https://github.com/open-mmlab/OpenPCDet

 
## DEEP-LEARNING
1. FUNDAMENTALS OF DEEP LEARNING
   * https://github.com/Amit10311/FUNDAMENTALS-OF-DEEP-LEARNING

2. FUNDAMENTALS OF COMPUTING WITH CUDA C/C++
   * https://github.com/Amit10311/FUNDAMENTALS-OF-COMPUTING-WITH-CUDA-C-C-
 
3. Deep-Learning-for-Robotics
   * https://github.com/Amit10311/Deep-Learning-for-Robotics
  
4. NVIDIA Deep Learning Examples for Tensor Cores
   * https://github.com/NVIDIA/DeepLearningExamples

5. PyTorch Tutorial to Object Detection.
   * https://github.com/sgrvinod/a-PyTorch-Tutorial-to-Object-Detection



## Robots 
1. Ros_Summit_XL_basics
   * `Code:` https://github.com/Amit10311/Ros_Summit_XL_basics
  
    
  
## Simulators 
1. TensorFlow Implementation for Computing a Semantically Segmented Bird's Eye View (BEV) Image Given the Images of Multiple Vehicle-Mounted Cameras.
   * https://github.com/ika-rwth-aachen/Cam2BEV

2. Open-RMF (www.open-rmf.org)
   * Open-RMF ROSCon Workshop slides  https://lnkd.in/gvnaeXnx
   * https://github.com/open-rmf/rmf-web
   * https://github.com/open-rmf/rmf_demos
   * https://vimeo.com/405803151
  
3. Robust and efficient coverage paths for autonomous agricultural vehicles
   * https://github.com/Fields2Cover/Fields2Cover 

  
## Working with Drone 
1. Intelligent Quads Tutorials
   * https://github.com/Intelligent-Quads/iq_tutorials

2. mav_trajectory_generation
   * Tools for polynomial trajectory generation and optimization. 
   * https://github.com/ethz-asl/mav_trajectory_generation



## Programming 

1. Classic Programming Books
   * https://github.com/jobbole/awesome-programming-books 


