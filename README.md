#  Drawing Robot
## Context
This research project was conducted at the Institute of Robotics and Autonomous Systems of the University of Lübeck.
Our goal was to use the 6-axis robot, UR5e, alongside the ROS2 and Motion Planning Framework Moveit2 to draw provided images with multiple colors. Additionally, 
the Optitrack motion capture system was utilized to track the robot's end-effector, whiteboard, and penholder.
## Hand-Eye-Calibration
The primary step of the project was to properly calibrate the robot. This was accomplished by providing 10 poses which are linearly independent and utilizing a 
least-square approach to solve the linear equation.
## Drawing
The drawing process is enabled through an edge detection algorithm used to draw Bezier curves from the extracted waypoints. After that, the robot is tasked with 
following the user-defined number of steps, frequently switching out the colors located in the penholder.
## Tutorial
Before you are able to use these ROS2 commands you have to use the following command to build you're workspace.

```
colcon build
```

After that you have to use the following command to source you're workspace.

```
source install/setup.bash
```


There are three ROS2 launch files to start the different parts of the project.

This command is used to establish a connection between the UR5e and the remote controller.

  1. Robot Connection: 
```
ros2 launch launch/setupRobotTrackingConnection.py
```
  
This command is used to start the calibration and calculate the needed calibration matrices.  

  2. Calibration: 
```
ros2 launch launch/calibrate_robot.py
```

This command is used to draw the picture. What kind of picture you want to draw can be specified by the picture path.

  3. Draw Picture: 
```
ros2 launch launch/draw_picture.py picture_path:="/home/prakt3/Pictures/chopper.jpg"
```
## Results
Here is a link to our Youtube Video highlighting our project and showing our results. [YouTube](https://www.youtube.com/watch?v=YwW8a0XS5Mk&t=311s)


