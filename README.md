# Ground Robot Exercise 

## Prerequisites

1. Basic knowledge or ros2 concepts - understaing of ros2 docs tutorials and concepts. 

2. Basic knowledge and understading of ardupilot and integrating with it. 

## Purpose 

This exercise is meant to be build on top of ros2 basic concepts and is meant to get you to the entry level into ground robotics and its fundementals. 

It should include the following elements - 

1. Gazebo experience and creating models using sdf, urdf and xacro 

2. ROS2 - Ardupilot - Gazebo integration  

3. Basics of navigation and control 

## Phase 1 - sdf, urdf, xacro 

1. Create a workspace for the project. This workspace will guide you through this whole exersice. Setup also Dockerfile, you might want to use [allison template](https://github.com/athackst/vscode_ros2_workspace)

2. Create a urdf which  describes a differential robot (a robot which controls the celocity of each side independently), and load it in gazebo. These links might help you get started - 

https://automaticaddison.com/urdf-vs-sdf-link-pose-joint-pose-visual-collision/

https://nu-msr.github.io/ros_notes/ros2/modeling.html


You may use a model from the internet as long as you understand the making of it. Make sure it confirms to what you would expect in real life, for example: 

- Apply a torque on the wheel and check that it spins and spins the robot accordingly. 

- Apply a force on the chasis of the robot and see it move in the force direction. 

- Drop it from some height and see how it reacts on impact.

**CAUTION: creating a full realistic model can be tediours and takes time, get to a certain level at which you feel comfortable with basic physics of the robot.**

**You'll have a chance to revise it later on.!** 

3. See the model in RVIZ . YOu might need to use joint_state_publisher. 

4. If you haven't used xacro in your model - it's about damn time. Parametrize your model and seperate it to files as per the different parts of it - chassis, wheels, etx. Make sure xacro-->urdf--> sdf transition goes smoothly and that the RVIZ  and gazebo checks pass. 


## Phase 2 - 

## help resources for this exercise: 

1. https://nu-msr.github.io/ros_notes/

2. 