Autonomous Drawing Robot with UR5e
Institute of Robotics and Autonomous Systems · University of Lübeck
Bild anzeigen
Bild anzeigen
Bild anzeigen
Bild anzeigen

Demo

📺 Watch the full drawing pipeline on YouTube

Bild anzeigen
The UR5e executing a multi-color drawing — including automated tool-switching between pens.

Overview
An end-to-end autonomous drawing system built on a UR5e 6-DOF industrial robot arm. The pipeline takes a standard image as input and produces a physical drawing — handling everything from computer vision and motion planning to real-time tracking and hardware execution.
Developed at the Institute of Robotics and Autonomous Systems, University of Lübeck.

Key Features

Motion Planning — Integrated MoveIt2 for collision-aware trajectory planning and smooth execution on the UR5e.
Real-Time Pose Tracking — OptiTrack motion capture tracks the end-effector, whiteboard, and pen holder at runtime.
Computer Vision Pipeline — OpenCV edge detection converts .jpg images into ordered waypoints, then smoothed into Bézier curves for fluid strokes.
Hand-Eye Calibration — Custom least-squares solver aligns the OptiTrack world frame with the robot base frame for sub-millimeter accuracy.
Multi-Color Drawing — Automated pen-switching logic handles sequential color passes without manual intervention.


System Architecture
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

Getting Started
Prerequisites

ROS2 Humble
MoveIt2
OptiTrack SDK / VRPN client
OpenCV

Build
bashcolcon build
source install/setup.bash
Running the Pipeline
Execute the following steps in order:
1. Establish Connection
Start communication between the UR5e and the remote controller:
bashros2 launch launch/setupRobotTrackingConnection.py
2. Calibration
Run the calibration routine to compute the required transformation matrices:
bashros2 launch launch/calibrate_robot.py
3. Execute Drawing
Start the drawing pipeline with the path to your target image:
bashros2 launch launch/draw_picture.py picture_path:="/home/user/Pictures/your_image.jpg"

Tech Stack
AreaToolsRobot MiddlewareROS2 HumbleMotion PlanningMoveIt2Computer VisionOpenCVPose TrackingOptiTrack Motion CaptureLanguagesC++, PythonCalibrationLeast-Squares Hand-Eye SolverHardwareUniversal Robots UR5e

Results
The system successfully draws arbitrary images with smooth, multi-color strokes and no manual intervention between color passes. See the full demo including tool-switching on YouTube.

University project — Institute of Robotics and Autonomous Systems, University of Lübeck
