# Autonomous Drawing Robot with UR5e
**Institute of Robotics and Autonomous Systems, University of Lübeck**

![C++](https://img.shields.io/badge/C%2B%2B-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![ROS2](https://img.shields.io/badge/ROS2-Humble-22314E?style=for-the-badge&logo=ros&logoColor=white)
![MoveIt2](https://img.shields.io/badge/MoveIt2-Planning-orange?style=for-the-badge)

---

## 📺 Project Highlight
![UR5e Drawing Process](path/to/your/drawing.gif)
*Note: Replace this with a link to your GIF or a high-res screenshot of the robot in action.*

---

## 📝 Overview
This project implements an autonomous multi-color drawing pipeline using a **UR5e 6-axis industrial robot**. The system transforms standard images into robotic trajectories using edge detection and Bezier curve interpolation, managed via **ROS2** and **MoveIt2**.

## 🚀 Key Features
*   **Motion Planning:** Integrated **MoveIt2** for collision-aware trajectory planning and execution.
*   **Perception & Tracking:** Utilized **Optitrack Motion Capture** to track the end-effector, whiteboard, and penholder in real-time.
*   **Computer Vision:** OpenCV-based edge detection pipeline to convert `.jpg` images into waypoints and smooth **Bezier curves**.
*   **Precision Calibration:** Hand-Eye Calibration routine using a **Least-Squares solver** to align robot and motion-capture coordinate frames.

## 🛠 System Architecture
1.  **Calibration:** Aligning the Optitrack world frame with the Robot base frame.
2.  **Image Processing:** Waypoint extraction and Bezier curve generation.
3.  **Path Generation:** Trajectory calculation for smooth robotic motion.
4.  **Execution:** Automated multi-color drawing and tool-switching logic.

## 💻 Getting Started

### Build & Setup
```bash
# Build the workspace
colcon build

# Source the workspace
source install/setup.bash
