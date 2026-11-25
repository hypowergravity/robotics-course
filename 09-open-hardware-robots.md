# Bonus: Open Hardware Robots You Can Build

The best way to learn robotics is to build a robot, and these projects publish their designs so you can. Start with a low-cost arm, since it connects directly to Stages 4, 7 and 8. Check each repository's own bill of materials for current prices and parts, because they change.

## Low-cost robot arms for learning and data collection

### [TheRobotStudio/SO-ARM100](https://github.com/TheRobotStudio/SO-ARM100)
A 3D-printable, low-cost arm designed to work with LeRobot. It is the most popular starting point for learning-based manipulation.

### [jess-moss/koch-v1-1](https://github.com/jess-moss/koch-v1-1)
A low-cost follower and leader arm pair that LeRobot supports, useful for teleoperation.

### [AlexanderKoch-Koch/low_cost_robot](https://github.com/AlexanderKoch-Koch/low_cost_robot)
The original low-cost robot arm design that inspired several later projects.

### [tonyzhaozh/aloha](https://github.com/tonyzhaozh/aloha)
A bimanual teleoperation platform that has produced important research datasets.

### [ROBOTIS-GIT/open_manipulator](https://github.com/ROBOTIS-GIT/open_manipulator)
An open arm with ROS support, well documented for education.

### [AngelLM/Thor](https://github.com/AngelLM/Thor)
A 3D-printable six-axis arm with full design files.

### [BCN3D/BCN3D-Moveo](https://github.com/BCN3D/BCN3D-Moveo)
A 3D-printed robotic arm from a university and 3D printing company collaboration.

## Mobile robots and platforms

### [SIGRobotics-UIUC/LeKiwi](https://github.com/SIGRobotics-UIUC/LeKiwi)
A low-cost mobile manipulator designed to be used with LeRobot.

### [ROBOTIS-GIT/turtlebot3](https://github.com/ROBOTIS-GIT/turtlebot3)
The classic small mobile robot for learning ROS, navigation and SLAM.

### [hello-robot/stretch_ros2](https://github.com/hello-robot/stretch_ros2)
Software for the Stretch mobile manipulator, a home-assistant style robot.

## Legged and humanoid robots

### [stanfordroboticsclub/StanfordQuadruped](https://github.com/stanfordroboticsclub/StanfordQuadruped)
Code for Stanford Pupper, a small quadruped robot with a full control stack.

### [mike4192/spotMicro](https://github.com/mike4192/spotMicro)
A ROS-based quadruped inspired by a famous commercial robot, built from printable parts.

### [PetoiCamp/OpenCat](https://github.com/PetoiCamp/OpenCat)
Open firmware for the Petoi robot cat and dog, a compact entry point to legged locomotion.

### [poppy-project/poppy-humanoid](https://github.com/poppy-project/poppy-humanoid)
An open-source humanoid robot platform for education and research.

### [mit-biomimetics/Cheetah-Software](https://github.com/mit-biomimetics/Cheetah-Software)
The control software for the MIT Cheetah robots. Read it to see a research-grade legged control stack.

### [pollen-robotics/reachy_mini](https://github.com/pollen-robotics/reachy_mini)
Open software for Reachy Mini, a small expressive desktop robot built with Hugging Face for AI experiments.

### [unitreerobotics/unitree_sdk2](https://github.com/unitreerobotics/unitree_sdk2)
The SDK for Unitree's quadruped and humanoid robots, useful if you later work with a commercial platform.

### [open-dynamic-robot-initiative/open_robot_actuator_hardware](https://github.com/open-dynamic-robot-initiative/open_robot_actuator_hardware)
Hardware designs for high-performance, low-cost robot actuators used in research quadrupeds.

## Drones

### [ArduPilot/ardupilot](https://github.com/ArduPilot/ardupilot)
Open autopilot software for drones, rovers, boats and planes, with a large community.

### [PX4/PX4-Autopilot](https://github.com/PX4/PX4-Autopilot)
Another widely used open autopilot, common in research and industry.

## Connecting and sensing

### [micro-ROS/micro_ros_setup](https://github.com/micro-ROS/micro_ros_setup)
Brings ROS 2 to microcontrollers so small boards can talk to the rest of your robot.

### [opencv/opencv](https://github.com/opencv/opencv)
The standard computer vision library.

### [ultralytics/ultralytics](https://github.com/ultralytics/ultralytics)
Easy-to-use object detection and segmentation models, handy for giving a robot a camera-based task.

### [luxonis/depthai-core](https://github.com/luxonis/depthai-core)
Software for OAK cameras that run neural networks on the camera itself.

### [IntelRealSense/librealsense](https://github.com/IntelRealSense/librealsense)
The SDK for RealSense depth cameras.

## Motor drivers for your own joints

For brushless joints, see [ODrive](https://github.com/odriverobotics/ODrive), [moteus](https://github.com/mjbots/moteus), [VESC](https://github.com/vedderb/bldc) and [SimpleFOC](https://github.com/simplefoc/Arduino-FOC), which are described in [Stage 2](02-electronics.md).

## A sensible build order

Begin with an SO-ARM100 or similar low-cost arm. Run its inverse kinematics from Stage 4, record demonstrations with LeRobot from Stage 8, and train a policy from Stage 7. Move to a mobile robot such as the TurtleBot 3 once you want to practise Stage 5 localisation and Stage 6 navigation on real hardware.

## Trending and most-starred additions (checked 25 Nov 2026)

Star counts below are approximate figures reported by public aggregator pages on 25 Nov 2026, so treat them as a rough guide to popularity, not exact numbers. Entries without a count had no figure in the pages I could reach. Links not marked as checked are from memory, so confirm they open.

### Humanoids
[Roboparty/roboto_origin](https://github.com/Roboparty/roboto_origin) is a fully open DIY humanoid with hardware, electronics and training code, at about 2.8k stars. [Roboparty/RP1](https://github.com/Roboparty/RP1) is a related full-stack platform for agentic humanoids at about 1.2k. [menloresearch/asimov-v0](https://github.com/menloresearch/asimov-v0) is an open-source humanoid, with a version 1 listed at about 1.6k. [TheRobotStudio/HOPEJr](https://github.com/TheRobotStudio/HOPEJr) is a DIY humanoid with dexterous hands at around 800 stars. [poppy-project/poppy-humanoid](https://github.com/poppy-project/poppy-humanoid) (listed above) has about 895. One 2026 ranking of open humanoids by how open they really are calls Pollen's Reachy 2 the most open, since both its hardware and software are published under Apache 2.0, and also covers Roboto Origin, Asimov v1, AgiBot X1, Bruce, Sourccey and RP1. Remember that open source does not mean free, because motors, batteries and computers still cost most of the money.

### Arms
[enactic/openarm](https://github.com/enactic/openarm) is a fully open humanoid-style arm for contact-rich physical AI research, at about 1.8k stars. A May 2026 Hugging Face community post introduced the LeRobot Humanoid, an open, low-cost, 3D-printed humanoid designed for robot learning. GitHub's SO-101 topic lists dozens of community projects around the SO-ARM101 arm, including simulation-first learning pipelines.

### Directories
[Growbotics-AI/awesome-open-source-robotics](https://github.com/Growbotics-AI/awesome-open-source-robotics) lists open projects including Mobile ALOHA (a whole-body teleoperation system for bimanual mobile manipulation) and TienKung 3.0 (a full-size humanoid platform). [stephane-caron/awesome-open-source-robots](https://github.com/stephane-caron/awesome-open-source-robots) is a curated list of fully open robots with about 214 stars. [SmilingRobo/open-source-robotics](https://github.com/SmilingRobo/open-source-robotics) collects projects including HumanPlus and InMoov.
