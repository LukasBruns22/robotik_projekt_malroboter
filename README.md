# Autonomous Drawing Robot with UR5e

**Institute of Robotics and Autonomous Systems · University of Lübeck**

![C++](https://img.shields.io/badge/C%2B%2B-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![ROS2](https://img.shields.io/badge/ROS2-Humble-22314E?style=for-the-badge&logo=ros&logoColor=white)
![MoveIt2](https://img.shields.io/badge/MoveIt2-Planning-orange?style=for-the-badge)

---

## Demo

> 📺 **[Watch the full drawing pipeline on YouTube](https://your-youtube-link-here)**

![UR5e Drawing Process](path/to/your/drawing.gif)
*The UR5e executing a multi-color drawing — including automated tool-switching between pens.*

---

## Overview

An end-to-end autonomous drawing system built on a **UR5e 6-DOF industrial robot arm**. The pipeline takes a standard image as input and produces a physical drawing — handling everything from computer vision and motion planning to real-time tracking and hardware execution.

Developed at the **Institute of Robotics and Autonomous Systems, University of Lübeck**.

---

## Key Features

- **Motion Planning** — Integrated [MoveIt2](https://moveit.ros.org/) for collision-aware trajectory planning and smooth execution on the UR5e.
- **Real-Time Pose Tracking** — [OptiTrack](https://optitrack.com/) motion capture tracks the end-effector, whiteboard, and pen holder at runtime.
- **Computer Vision Pipeline** — OpenCV edge detection converts `.jpg` images into ordered waypoints, then smoothed into **Bézier curves** for fluid strokes.
- **Hand-Eye Calibration** — Custom least-squares solver aligns the OptiTrack world frame with the robot base frame for sub-millimeter accuracy.
- **Multi-Color Drawing** — Automated pen-switching logic handles sequential color passes without manual intervention.

---

## System Architecture

```
Image Input
    │
    ▼
[1] Calibration
    Aligns OptiTrack world frame ↔ Robot base frame
    via least-squares hand-eye calibration
    │
    ▼
[2] Image Processing
    Edge detection (OpenCV) → Waypoint extraction → Bézier curve fitting
    │
    ▼
[3] Path Generation
    Trajectory calculation for smooth, collision-free motion
    │
    ▼
[4] Execution
    MoveIt2 executes trajectory on UR5e
    OptiTrack provides real-time feedback
    Automated tool-switching for multi-color output
```

---

## Getting Started

### Prerequisites

- ROS2 Humble
- MoveIt2
- OptiTrack SDK / VRPN client
- OpenCV

### Build

```bash
colcon build
source install/setup.bash
```

### Running the Pipeline

Execute the following steps in order:

**1. Establish Connection**

Start communication between the UR5e and the remote controller:

```bash
ros2 launch launch/setupRobotTrackingConnection.py
```

**2. Calibration**

Run the calibration routine to compute the required transformation matrices:

```bash
ros2 launch launch/calibrate_robot.py
```

**3. Execute Drawing**

Start the drawing pipeline with the path to your target image:

```bash
ros2 launch launch/draw_picture.py picture_path:="/home/user/Pictures/your_image.jpg"
```

---

## Tech Stack

| Area | Tools |
|---|---|
| Robot Middleware | ROS2 Humble |
| Motion Planning | MoveIt2 |
| Computer Vision | OpenCV |
| Pose Tracking | OptiTrack Motion Capture |
| Languages | C++, Python |
| Calibration | Least-Squares Hand-Eye Solver |
| Hardware | Universal Robots UR5e |

---

## Results

The system successfully draws arbitrary images with smooth, multi-color strokes and no manual intervention between color passes. See the full demo including tool-switching on [YouTube](https://your-youtube-link-here).

---

*University project — Institute of Robotics and Autonomous Systems, University of Lübeck*
