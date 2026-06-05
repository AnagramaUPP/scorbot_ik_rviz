# Scorbot IK RViz for ROS 2 Jazzy

## Description

This package implements the inverse kinematics of a Scorbot robotic manipulator in ROS 2 Jazzy and visualizes the resulting motion in RViz.

The package receives a desired end-effector pose defined by Cartesian coordinates and orientation parameters, computes the corresponding joint values using inverse kinematics, and publishes the resulting joint states to the robot model.

The robot model is visualized using RViz and Robot State Publisher.

---

## Features

* Inverse kinematics implementation for the Scorbot manipulator.
* Real-time visualization in RViz.
* Joint state publication through `/joint_states`.
* Cartesian command interface through ROS 2 topics.
* Compatible with ROS 2 Jazzy.
* Modular structure for future integration with:

  * Neural Networks
  * Genetic Algorithms
  * Particle Swarm Optimization (PSO)
  * Trajectory Planning
  * Reinforcement Learning

---

## Package Structure

```text
scorbot_ik_rviz/
├── config/
├── launch/
│   └── display.launch.py
├── meshes/
├── rviz/
├── scripts/
│   └── scorbot_ik_publisher.py
├── urdf/
│   └── scorbot.urdf
├── CMakeLists.txt
├── package.xml
└── README.md
```

---

## Dependencies

* ROS 2 Jazzy
* RViz2
* Robot State Publisher
* Joint State Publisher
* NumPy

---

## Build

```bash
cd ~/ros2_ws

colcon build --packages-select scorbot_ik_rviz

source install/setup.bash
```

---

## Launch RViz

```bash
ros2 launch scorbot_ik_rviz display.launch.py
```

---

## Run the Inverse Kinematics Node

```bash
ros2 run scorbot_ik_rviz scorbot_ik_publisher.py
```

---

## Desired Pose Topic

The node subscribes to:

```text
/scorbot/desired_pose
```

Message type:

```text
std_msgs/msg/Float64MultiArray
```

Data format:

```text
[x, y, z, delta]
```

Example:

```bash
ros2 topic pub --once /scorbot/desired_pose \
std_msgs/msg/Float64MultiArray \
"{data: [0.40, 0.10, 0.20, -1.5708]}"
```

where:

* x : desired end-effector X position [m]
* y : desired end-effector Y position [m]
* z : desired end-effector Z position [m]
* delta : desired wrist orientation [rad]

---

## Verification

The end-effector pose can be verified using:

```bash
ros2 run tf2_ros tf2_echo base_link link_5
```

This command displays the transformation between the robot base and the end-effector frame.

---

## Future Work

* Forward kinematics validation.
* Trajectory generation.
* ROS 2 Control integration.
* Gazebo simulation.
* Neural network inverse kinematics approximation.
* Metaheuristic optimization methods.
* Digital twin implementation.

---

## Author
Dr. Mitchell Angel Gomez Ortega

Professor and Researcher

Universidad Politécnica de Pachuca (UPP)
