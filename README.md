# pal_robotiq_gripper

The `pal_robotiq_gripper` repository contains the necessary files for working with Robotiq grippers in both ROS1 and ROS2 environments. It includes description files, URDFs, configurations, and controller setups for different gripper models, such as the Robotiq 140 and 85 grippers, along with specialized configurations for Gazebo simulations and ROS controllers.

## Table of Contents
1. [ROS Control - Hardware Interface](#1-ros-control---hardware-interface)
2. [C++ API](#2-c-api)
3. [Configuration Files](#3-configuration-files)
4. [Launch Files](#4-launch-files)
5. [Example Usage](#5-example-usage)
6. [Dependencies](#6-dependencies)

---

## 1. ROS Control - Hardware Interface

### Effort Command, Position State, Velocity State
This repository interfaces with the Robotiq gripper hardware via ROS Control. The gripper hardware interface supports:
- **Effort Command**: Allows controlling the force applied by the gripper.
- **Position State**: Provides feedback on the gripper's current position.
- **Velocity State**: Reports the speed of the gripper’s movement.

## 2. C++ API

The C++ API for the Robotiq gripper is used to communicate and control the hardware via ROS control interfaces. The implementation abstracts the hardware details and provides an interface for higher-level control systems.

## 3. Configuration Files

Configuration files are included to set up parameters such as port names, hardware filters, and controller parameters.

### Key Configurations:
- **URDF Files**: Located in `pal_robotiq_140_description/urdf`, they define the robot description for the Robotiq gripper, including transmission and joint settings.
    - `robotiq_140_gripper.urdf.xacro`
    - `robotiq_140_gripper.transmission.xacro`

- **Meshes**: 3D models used for visualization and collision detection in simulations. Located under `pal_robotiq_140_description/meshes/collision` and `meshes/visual`.

### Config Folder:
- Defines port names and other parameters essential for interfacing with the gripper hardware.
- **Example files**:
    - `hardware_config.yaml`
    - `controller_config.yaml`

## 4. Launch Files

Several launch files are provided for different use cases, including hardware bring-up, simulation, and display configurations. These launch files help to streamline the process of launching and configuring the gripper in both real and simulated environments.

### Important Launch Files:
- **`upload.launch`**: Loads the URDF model for the Robotiq gripper into the ROS parameter server.
- **`display.launch`**: Launches RViz to visualize the Robotiq gripper model.
- **`default_controllers.launch`**: Brings up the necessary controllers for interfacing with the gripper.

Example:
```bash
roslaunch pal_robotiq_140_description upload.launch
```

## 5. Example Usage

### Bringing up the Robotiq 140 Gripper:
To bring up the Robotiq 140 gripper in a simulated or real environment, the following steps can be followed:

1. Load the URDF:
   ```bash
   roslaunch pal_robotiq_140_description upload.launch
   ```

2. Visualize the gripper model in RViz:
   ```bash
   roslaunch pal_robotiq_140_description display.launch
   ```

3. Launch the gripper controller:
   ```bash
   roslaunch pal_robotiq_controller_configuration default_controllers.launch
   ```

## 6. Dependencies

This repository relies on the following dependencies, which can be installed via the `rosdep` command or manually:

### Core Dependencies:
- **ROS (Melodic, Noetic, or later)**: The primary dependency for controlling and simulating the gripper.
- **URDF and Xacro**: For defining the robot description and models.
- **RViz**: For visualization of the gripper models.
- **Controller Manager**: For managing the gripper controllers in ROS control.

### Installing Dependencies:
To install the necessary dependencies, run:
```bash
rosdep install --from-paths src --ignore-src -r -y
```

---

This repository provides the essential components to interface with Robotiq grippers in ROS1/ROS2 environments.
