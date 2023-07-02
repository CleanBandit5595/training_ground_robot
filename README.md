# Ground Robot Exercise 

## Prerequisites

1. Basic knowledge or ros2 concepts - understanding of ros2 docs tutorials and concepts. 

2. Basic knowledge and understanding of ardupilot and integrating with it. 

## Purpose 

This exercise is meant to be build on top of ros2 basic concepts and is meant to get you to the entry level into ground robotics and its fundementals. 

It should include the following elements - 

1. Gazebo experience and creating models using sdf, urdf and xacro 

2. ROS2 - Ardupilot - Gazebo integration  

3. Basics of navigation and control 

## General guidance and recommendations 

1. use gazebo classic 11 (it will be the easiest and will serve the matter of the exercise).

## Phase 1 - sdf, urdf, xacro 

1. Create a workspace for the project. This workspace will guide you through this whole exersice. Setup also Dockerfile, you might want to use [allison template](https://github.com/athackst/vscode_ros2_workspace)

2. Create a urdf which  describes a differential robot (a robot which controls the celocity of each side independently), and load it in gazebo. These links might help you get started - 

https://automaticaddison.com/urdf-vs-sdf-link-pose-joint-pose-visual-collision/

https://nu-msr.github.io/ros_notes/ros2/modeling.html


You may use a model from the internet as long as you understand the making of it. Make sure it confirms to what you would expect in real life, for example: 

- Apply a torque on the wheel and check that it spins and spins the robot accordingly. 

- Apply a force on the chasis of the robot and see it move in the force direction. 

- Drop it from some height and see how it reacts on impact.

**CAUTION: creating a full realistic model can be tedious and takes time, get to a certain level at which you feel comfortable with the basic physics of the robot.**

**You'll have a chance to revise it later on.!** 

3. See the model in RVIZ . You might need to use joint_state_publisher package. 

4. If you haven't used xacro in your model - it's about damn time. Parametrize your model and seperate it to files as per the different parts of it - chassis, wheels, etx. Make sure xacro-->urdf-->sdf transition goes smoothly and that the RVIZ and gazebo checks pass. 


## Phase 2 - ROS2 and your robot

1. Create a launch file to launch the gazebo simulation, and RVIZ.

2. Connect ROS to the gazebo model using ROS2-GAZEBO plugins. The following resources might help you: 

https://articulatedrobotics.xyz/mobile-robot-2-concept-urdf/

https://automaticaddison.com/the-ultimate-guide-to-the-ros-2-navigation-stack/

https://classic.gazebosim.org/tutorials?tut=ros2_overview&cat=connect_ros

3. Let's teleoperate that robot - use your keyboard and a teleop_twist_keyboard to manipulate the robot. The above links should help you here also. 

4. Now you should have a good control on your robot. Add an object to your gazebo simulation and maneuver your robot to collide it. If you're not satisfied with your model, now's a good time to sharpen it a little.


## Phase 4 - Autonomy 101 

By now you should have a somewhat functional but stupid robot. Let's make it inetresting: 

1. Add a lidar to the model. Make sure it is seen in the gazebo and in the rviz. Read it's output and make sure it makes sense. USE XACRO! 

2. Get in the head of the operator - drive only using rviz and collide your robot with an object. 

3. Use the lidar to create a simple control loop, that when a command is given (pressed a given or even sending command using ROS CLI), it autonomously collides with the closest object it sees.


## Phase 5 - Add in Ardupilot

Now most of our systems use ardupilot to drive the vehicles, as a matter of principle. 

1. Add ardupilot to the model. This isn't straightforward as it sounds, and the best way to attack this is to look at a working example and learn how to modify it to your custom robot from there. A working example can be (hopefully) found here - 

https://github.com/SwiftGust/ardupilot_gazebo

This may take some trial and error, so don't give up !  

2. Make sure you can control it with sitl through mavlink - to ease things up use a GCS or mavproxy to send commands for the relevant rc_channels commands. If you have a joystick, it might be nice to connect it and use it to teleoperate.  

3. Now incorporate ROS2 with your ardupilot model. A good flow of information might look like this - 

ros2_teleop_node --> twist command --> mavros --> mavlink rc_channels command --> gazebo 

If you're up to it, you may (and it is welcome) to use mavros. It certaintly might be half baked so writing yourself a little code with pymavlink and connect it to ROS2 is also alright.

## Important general resources for this exercise: 

1. https://nu-msr.github.io/ros_notes/

2. https://automaticaddison.com/the-ultimate-guide-to-the-ros-2-navigation-stack/


## Exercise Salt: 
If you've finished and you're bored, you may add this salt at the end of the exercise: 

1. After phase 4 - write a pid control algorithm to the vehicle cmd_vel to reach the object.  

2. Sensor fusing and tf2 - 