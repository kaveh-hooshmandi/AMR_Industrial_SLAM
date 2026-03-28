# AMR Industrial Multi-Sensor SLAM

**A framework for industrial autonomous mobile robots (AMRs) to perform robust SLAM using multi-sensor fusion in challenging environments**

---

## 📌 Introduction

In this repository, a complete framework is developed by integrating multiple state-of-the-art tools to build a functional **industrial AMR** capable of performing **robust SLAM** in smart factories and similar real-world environments.

The system combines LiDAR, vision, and inertial sensing to achieve reliable localization and mapping under dynamic and uncertain conditions.

---

## 🖼️ System Overview

![rtab](https://github.com/user-attachments/assets/36dca959-9468-4c7c-ad9a-43100fb4f004)

---

## 🧩 Framework Components

For the AMR development, the following open-source repositories are utilized:

1. **[Linorobot2](https://github.com/linorobot/linorobot2?tab=readme-ov-file)**
   Base framework for AMR modeling and robot structure

2. **[RTAB-Map](https://github.com/introlab/rtabmap)**
   Core framework for SLAM, sensor fusion, and graph-based optimization

3. **[Kinematic-ICP](https://github.com/PRBonn/kinematic-icp)** *(Future Work)*
   For enhancing ICP-based odometry accuracy

---

## 🛠️ Custom Packages

In addition, the following custom packages are developed:

1. **amr_main**
   Main package for launching and coordinating the full system

2. **laser_fusion**
   A custom module for **2D LiDAR fusion**, enabling integration of multiple LiDAR sensors

---

## ⚠️ Work in Progress

This project is actively being developed. While the current system is functional, further improvements are planned, including:

* Integration of **Kinematic-ICP** with RTAB-Map
* Enhanced sensor fusion strategies
* Improved robustness in dynamic environments

---

## ⚙️ Main Files (Customization)

### 1. RTAB-Map Parameters

Modify SLAM configuration and sensor selection:

```bash
code ~/AMR_Industrial_SLAM/src/rtabmap_ros/rtabmap_launch/launch/rtabmap.launch.py
```

---

### 2. Robot and Sensor Configuration

Modify or extend robot and sensor models:

```bash
code ~/AMR_Industrial_SLAM/src/linorobot2/linorobot2_description/urdf/4wd_properties.urdf.xacro
code ~/AMR_Industrial_SLAM/src/linorobot2/linorobot2_description/urdf/robots/4wd.urdf.xacro
code ~/AMR_Industrial_SLAM/src/linorobot2/linorobot2_description/urdf/sensors/laser_new.urdf.xacro
code ~/AMR_Industrial_SLAM/src/linorobot2/linorobot2_description/urdf/sensors/stereo_camera.urdf.xacro
code ~/AMR_Industrial_SLAM/src/linorobot2/linorobot2_description/urdf/sensors/imu.urdf.xacro
```

---

### 3. LiDAR Fusion Module

```bash
code ~/AMR_Industrial_SLAM/src/laser_fusion/laser_fusion/combine_laser_measurements.py
```

---

## 🎥 Demo

![amr\_rtab\_gif\_2](https://github.com/user-attachments/assets/d0d5b713-1a9e-42c4-9ad8-94e54d0f8753)

In this demonstration:

* A **front LiDAR** is used for mapping
* A **front stereo camera** is used for perception
* The system performs:

  * Visual-Inertial Odometry (VIO)
  * ICP-based odometry
  * Visual and LiDAR loop closures

SLAM is performed using **graph-based optimization (RTAB-Map)** to generate a 2D map.

* In this demo, I have used only the **front LiDAR** (not both). I have also used the **front stereo camera**. Here, I'm performing **VIO** and **ICP odometry**, as well as **visual** and **laser** **loop closures** to create a **2D map**. Additionally, RTAB-Map uses **graph-based SLAM**.

---
## ⚙️ Installation and Usage

This project requires **ROS 2 (Recommended: ROS 2 Humble)**.

### 1. Clone the Repository

```bash
git clone https://github.com/kaveh-hooshmandi/AMR_Industrial_SLAM.git
cd AMR_Industrial_SLAM
```

---

### 2. Install Dependencies

```bash
rosdep update
rosdep install --from-path src --ignore-src -y
```

---

### 3. Build the Workspace

```bash
colcon build
source install/setup.bash
```

---

### 4. Launch the System

```bash
ros2 launch amr_main launch_all.launch.py
```

---

## 📬 Contact

If you have any questions or suggestions, feel free to reach out.
