# AMR Industrial Multi-Sensor SLAM

## Abstract

This repository presents a ROS 2-based multi-sensor SLAM framework for industrial autonomous mobile robots (AMRs). The system integrates LiDAR, vision, and inertial sensing to enable robust localization and mapping in dynamic and unstructured environments such as smart factories and warehouses. The proposed framework combines state-of-the-art open-source tools with custom-developed modules to achieve reliable perception and navigation performance.

---

## System Overview

<p align="center">
  <img src="images/RABO1.png" width="600"/>
</p>

The system architecture integrates multiple perception and navigation components, enabling robust SLAM through sensor fusion and graph-based optimization.

---

## Framework Architecture

The proposed system is built upon the integration of the following open-source frameworks:

* **Linorobot2**: Provides the base platform for AMR modeling, kinematics, and robot description.
* **RTAB-Map**: Core framework for multi-sensor SLAM, loop closure detection, and graph-based optimization.
* **Kinematic-ICP**: (Future integration) Enhances odometry estimation using kinematic constraints.

Additionally, the following custom modules have been developed:

* **amr_main**: Central orchestration package for launching and managing the full system.
* **laser_fusion**: Multi-LiDAR fusion module for combining measurements from multiple 2D LiDAR sensors.

---

## Key Features

* Multi-sensor fusion (LiDAR, stereo vision, IMU)
* Graph-based SLAM using RTAB-Map
* Visual-Inertial and LiDAR-based odometry
* Multi-LiDAR fusion for enhanced perception
* ROS 2 (Humble) based architecture
* Scalable to real-world industrial AMR platforms

---

## Configuration and Customization

The system is designed to be modular and configurable:

### SLAM Configuration

Modify RTAB-Map parameters:

```bash
code ~/AMR_Industrial_SLAM/src/rtabmap_ros/rtabmap_launch/launch/rtabmap.launch.py
```

### Robot and Sensor Configuration

Customize robot structure and sensors:

```bash
code ~/AMR_Industrial_SLAM/src/linorobot2/linorobot2_description/urdf/4wd_properties.urdf.xacro
code ~/AMR_Industrial_SLAM/src/linorobot2/linorobot2_description/urdf/robots/4wd.urdf.xacro
code ~/AMR_Industrial_SLAM/src/linorobot2/linorobot2_description/urdf/sensors/laser_new.urdf.xacro
code ~/AMR_Industrial_SLAM/src/linorobot2/linorobot2_description/urdf/sensors/stereo_camera.urdf.xacro
code ~/AMR_Industrial_SLAM/src/linorobot2/linorobot2_description/urdf/sensors/imu.urdf.xacro
```

### LiDAR Fusion Module

```bash
code ~/AMR_Industrial_SLAM/src/laser_fusion/laser_fusion/combine_laser_measurements.py
```

---

## Experimental Setup

The system supports multiple sensing configurations:

* Single or multi-LiDAR setups (front, rear, or combined)
* Stereo vision (front camera, extendable to multi-camera setups)
* IMU integration for motion estimation

In the demonstrated setup:

* Front LiDAR is used for mapping
* Stereo camera provides visual odometry
* SLAM is performed using graph-based optimization with loop closure detection

---

## Installation and Usage

### Requirements

* Ubuntu 22.04
* ROS 2 Humble
* Python 3.10

---

### Installation

```bash
git clone https://github.com/kaveh-hooshmandi/AMR_Industrial_SLAM.git
cd AMR_Industrial_SLAM
```

```bash
rosdep update && rosdep install --from-path src --ignore-src -y
```

```bash
colcon build
source install/setup.bash
```

---

### Run the System

```bash
ros2 launch amr_main launch_all.launch.py
```

---

## Research Contributions

* Adapted and extended a multi-sensor SLAM framework for industrial AMR applications
* Designed and implemented a LiDAR fusion pipeline for multi-sensor perception
* Integrated visual, inertial, and LiDAR sensing for robust localization
* Enhanced system modularity for real-world deployment in dynamic environments

---

## Future Work

* Integration of Kinematic-ICP with RTAB-Map
* Incorporation of learning-based navigation (DRL)
* Multi-camera and thermal sensing integration
* Deployment on embedded platforms (e.g., NVIDIA Jetson)

---

## Acknowledgment

This work is based on the following open-source projects:

* https://github.com/linorobot/linorobot2
* https://github.com/introlab/rtabmap
* https://github.com/PRBonn/kinematic-icp

The original contributions of the respective authors are gratefully acknowledged.
