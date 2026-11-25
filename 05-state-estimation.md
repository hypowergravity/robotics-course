# Stage 5: Knowing Where You Are (State Estimation)

**Start here:** [How a Kalman Filter Works, in Pictures](https://www.bzarg.com/p/how-a-kalman-filter-works-in-pictures/)

Sensors are noisy and models are imperfect, so a robot never knows its position exactly. State estimation combines a prediction with a measurement and keeps track of how uncertain it is. Begin with the Kalman filter, then move on to localisation and SLAM, which is the problem of building a map while working out where you are inside it.

## Filtering fundamentals

### [rlabbe/Kalman-and-Bayesian-Filters-in-Python](https://github.com/rlabbe/Kalman-and-Bayesian-Filters-in-Python)
A free book written as Jupyter notebooks. It builds up from simple ideas to Kalman filters with interactive examples, and is the best next step after the pictures article.

### [rlabbe/filterpy](https://github.com/rlabbe/filterpy)
The Python library that goes with the book. It provides Kalman, extended Kalman and particle filters you can drop into your own projects.

### [cra-ros-pkg/robot_localization](https://github.com/cra-ros-pkg/robot_localization)
A ROS package that fuses wheel odometry, IMU and GPS using extended and unscented Kalman filters. It shows how filtering is used on real robots.

## Optimisation-based estimation

### [borglab/gtsam](https://github.com/borglab/gtsam)
A library for factor graphs, the modern way to solve estimation and SLAM problems. It is the foundation for many current systems.

### [ceres-solver/ceres-solver](https://github.com/ceres-solver/ceres-solver)
A general library for nonlinear least squares, the numerical engine behind much of SLAM and calibration.

### [RainerKuemmerle/g2o](https://github.com/RainerKuemmerle/g2o)
A framework for graph-based optimisation that many SLAM systems use internally.

## Learning resources and tutorials

### [AtsushiSakai/PythonRobotics](https://github.com/AtsushiSakai/PythonRobotics)
Short, readable Python implementations of localisation, mapping, SLAM and path tracking, with animations. Ideal for understanding an algorithm before you meet a large C++ version.

### [gaoxiang12/slambook2](https://github.com/gaoxiang12/slambook2)
Code for the book *14 Lectures on Visual SLAM*. It teaches the full visual SLAM pipeline step by step.

## Real SLAM and odometry systems

### [cartographer-project/cartographer](https://github.com/cartographer-project/cartographer)
Google's real-time 2D and 3D laser SLAM system.

### [UZ-SLAMLab/ORB_SLAM3](https://github.com/UZ-SLAMLab/ORB_SLAM3)
A well-known visual and visual-inertial SLAM system supporting monocular, stereo and RGB-D cameras.

### [HKUST-Aerial-Robotics/VINS-Mono](https://github.com/HKUST-Aerial-Robotics/VINS-Mono)
A visual-inertial estimator that is popular for drones.

### [rpng/open_vins](https://github.com/rpng/open_vins)
A research platform for visual-inertial estimation with clean documentation and evaluation tools.

### [TixiaoShan/LIO-SAM](https://github.com/TixiaoShan/LIO-SAM)
Lidar-inertial odometry that fuses a spinning lidar with an IMU.

### [hku-mars/FAST_LIO](https://github.com/hku-mars/FAST_LIO)
A fast and robust lidar-inertial odometry system.

### [PRBonn/kiss-icp](https://github.com/PRBonn/kiss-icp)
A simple, easy-to-run lidar odometry pipeline that works with little tuning, so it is a good first lidar experiment.

### [MRPT/mrpt](https://github.com/MRPT/mrpt)
The Mobile Robot Programming Toolkit, with a large collection of SLAM, mapping and estimation tools.

## Evaluating your results

### [MichaelGrupp/evo](https://github.com/MichaelGrupp/evo)
A tool for comparing estimated trajectories with ground truth. Learning to measure error properly is half of state estimation.

## What to be able to do before moving on

You should be able to explain the predict and update steps of a Kalman filter in your own words, write a one-dimensional filter from scratch, and explain why a filter that trusts its model too much ignores the sensor. A good project is a simulated robot with a noisy position sensor and a filter that smooths it.

## Trending and most-starred additions (checked 25 Nov 2026)

Star counts below are approximate figures reported by public aggregator pages on 25 Nov 2026, so treat them as a rough guide to popularity, not exact numbers. Entries without a count had no figure in the pages I could reach. Links not marked as checked are from memory, so confirm they open.

### Most popular systems
[UZ-SLAMLab/ORB_SLAM3](https://github.com/UZ-SLAMLab/ORB_SLAM3) is the most-starred SLAM system I found, at about 8.4k stars. [rpng/open_vins](https://github.com/rpng/open_vins) is listed at about 2.8k stars as an open platform for visual-inertial navigation research.

### Curated lists to browse
[kanster/awesome-slam](https://github.com/kanster/awesome-slam) has about 1.7k stars and lists SLAM tutorials, projects and communities. [SilenceOverflow/Awesome-SLAM](https://github.com/SilenceOverflow/Awesome-SLAM) has about 1.1k stars and groups resources by sensor type, including lidar systems such as A-LOAM, Cartographer and FAST-LIO. [OpenSLAM/awesome-SLAM-list](https://github.com/OpenSLAM/awesome-SLAM-list) is another long-standing list. [youngguncho/awesome-slam-datasets](https://github.com/youngguncho/awesome-slam-datasets) lists datasets, which you need to test any estimator.

### For beginners
SLAM-Resources-for-Beginner is a recommended collection of lectures, papers and books with about 260 stars, and it pairs well with the *Visual SLAM* book code already listed.

### The current trend: NeRF and Gaussian splatting SLAM
[3D-Vision-World/awesome-NeRF-and-3DGS-SLAM](https://github.com/3D-Vision-World/awesome-NeRF-and-3DGS-SLAM) tracks the shift toward dense neural maps, including a 2026 survey on 3D Gaussian splatting SLAM. These are active research directions rather than production tools, so learn factor graphs with GTSAM first.
