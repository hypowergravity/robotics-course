# Stage 4: Moving an Arm (Kinematics)

**Start here:** [Inverse Kinematics, by Zalo](https://zalo.github.io/blog/inverse-kinematics/)

Forward kinematics answers "given my joint angles, where is my hand?" Inverse kinematics answers the harder question "given where I want my hand, what should my joint angles be?" This stage uses the maths from Stage 1 to move the mechanics from Stage 3. Work through a textbook first, then use the libraries to check your own code.

## Textbook companion

### [NxRLab/ModernRobotics](https://github.com/NxRLab/ModernRobotics)
Code for the *Modern Robotics* book and course from Northwestern University. It implements screw theory, forward and inverse kinematics and dynamics in clear, readable Python. If you only pick one repository in this stage, pick this one.

## Python libraries for learning

### [petercorke/robotics-toolbox-python](https://github.com/petercorke/robotics-toolbox-python)
A toolbox for arm models, forward and inverse kinematics, Jacobians and visualisation. It comes with many ready-made robot models.

### [petercorke/spatialmath-python](https://github.com/petercorke/spatialmath-python)
Classes for rotations and poses in 2D and 3D. It helps you see transforms as objects instead of loose matrices.

### [Phylliade/ikpy](https://github.com/Phylliade/ikpy)
A small inverse kinematics library that loads a robot from a URDF file and solves for joint angles. A very approachable first solver.

## Production-grade libraries

### [stack-of-tasks/pinocchio](https://github.com/stack-of-tasks/pinocchio)
A fast rigid-body dynamics library used in research and industry. It computes kinematics, Jacobians and dynamics efficiently.

### [orocos/orocos_kinematics_dynamics](https://github.com/orocos/orocos_kinematics_dynamics)
The KDL library, a long-standing C++ kinematics library used throughout the ROS ecosystem.

### [moveit/moveit2](https://github.com/moveit/moveit2)
The standard manipulation framework for ROS 2. It combines kinematics, collision checking and motion planning for real arms.

### [RobotLocomotion/drake](https://github.com/RobotLocomotion/drake)
A toolbox for modelling, simulating and optimising robots, with strong kinematics and trajectory optimisation support.

## Rotations done properly

### [strasdat/Sophus](https://github.com/strasdat/Sophus)
A C++ library for Lie groups, the mathematics of rotations and poses that avoids gimbal lock and handles small changes cleanly.

### [artivis/manif](https://github.com/artivis/manif)
A Lie theory library for state estimation and optimisation, accompanied by a well-known tutorial paper. You will use these ideas again in Stage 5.

## Planning helper

### [caelan/pybullet-planning](https://github.com/caelan/pybullet-planning)
Utilities for kinematics, collision checking and motion planning built on PyBullet, handy for quick experiments.

## What to be able to do before moving on

You should be able to write forward kinematics for a two-link arm on paper, derive the inverse solution, compute a Jacobian, and explain what happens near a singularity. Then reproduce the interactive demo in your own script and compare the answers with ikpy or the Robotics Toolbox.

## Trending and most-starred additions (checked 25 Nov 2026)

Star counts below are approximate figures reported by public aggregator pages on 25 Nov 2026, so treat them as a rough guide to popularity, not exact numbers. Entries without a count had no figure in the pages I could reach. Links not marked as checked are from memory, so confirm they open.

### [kevinzakka/mink](https://github.com/kevinzakka/mink)
Python inverse kinematics built on MuJoCo, with about 1.5k stars and a 2026 release. It is a port of Pink, which uses Pinocchio. If you plan to follow Stage 6 with MuJoCo, this is the most natural IK library to learn.

### [stephane-caron/pink](https://github.com/stephane-caron/pink)
Differential inverse kinematics using Pinocchio and quadratic-programming solvers. It outputs velocities that steer the robot toward all your tasks at once, which is how modern whole-body controllers are built.

### [Phylliade/ikpy](https://github.com/Phylliade/ikpy)
Already listed above. Aggregators report about 900 stars, which makes it one of the most popular pure-Python IK libraries.

### [traclabs/trac_ik](https://github.com/traclabs/trac_ik)
An improved IK solver that is widely used in ROS. It was last updated in June 2026 on the ROS index.

### [Simple-Robotics/LoIK](https://github.com/Simple-Robotics/LoIK)
Low-Complexity Inverse Kinematics in C++, with about 128 stars. A smaller, research-oriented project.

### [openrr/k](https://github.com/openrr/k)
A kinematics library for Rust with forward and inverse kinematics and a URDF loader, at about 219 stars. Useful if you prefer Rust.

### [robot-descriptions/awesome-robot-descriptions](https://github.com/robot-descriptions/awesome-robot-descriptions)
A curated list of robot models in URDF and MJCF formats, at roughly 1.5k to 1.7k stars. You need a robot description before any kinematics library can work, and this is the best place to find one.

### Differentiable kinematics
PyTorch-based kinematics libraries (for example pytorch_kinematics) let you compute kinematics inside a learning pipeline on the GPU. They are a good fit once you reach Stage 7.
