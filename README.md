Autonomous Drawing Robot with UR5e
Institute of Robotics and Autonomous Systems, University of Lübeck

Overview
This project implements an autonomous multi-color drawing pipeline using a UR5e 6-axis industrial robot. The system transforms standard images into robotic trajectories using edge detection and Bezier curve interpolation, managed via ROS2 and MoveIt2.

Key Features & Tech Stack
Motion Planning: Integrated MoveIt2 for collision-aware trajectory planning and execution.

Perception & Tracking: Utilized Optitrack Motion Capture for real-time tracking of the end-effector, whiteboard, and penholder.

Computer Vision: Developed an edge-detection pipeline to convert .jpg images into waypoints and smooth Bezier curves.

Calibration: Implemented a Hand-Eye Calibration routine using 10 linearly independent poses and a Least-Squares solver for high-precision coordinate transformation.

Software: ROS2 (Humble/Foxy), C++, Python, OpenCV.

System Architecture
Calibration: Aligning the Optitrack world frame with the Robot base frame.

Image Processing: Extracting waypoints from user-provided images.

Path Generation: Calculating Bezier curves for smooth robot motion.

Execution: Automated tool switching for multi-color drawings.

Getting Started
Bash
# Build the workspace
colcon build
source install/setup.bash

# 1. Establish UR5e & Tracking Connection
ros2 launch launch/setupRobotTrackingConnection.py

# 2. Run Hand-Eye Calibration
ros2 launch launch/calibrate_robot.py

# 3. Start Drawing Pipeline
ros2 launch launch/draw_picture.py picture_path:="path/to/image.jpg"
Results
Full Project Demonstration on YouTube
