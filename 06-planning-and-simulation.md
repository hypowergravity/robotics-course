# Stage 6: Planning and Simulation

**Start here:** [MuJoCo in the browser, by Zalo](https://zalo.github.io/mujoco_wasm/)

Planning decides what a robot should do, and simulation lets you test it without breaking anything. This stage links your kinematics and estimation work into complete behaviours. Begin by playing with the browser demo, then install a simulator on your computer and run a planner inside it.

## Learn the algorithms

### [AtsushiSakai/PythonRobotics](https://github.com/AtsushiSakai/PythonRobotics)
Readable implementations of path planning (A*, RRT, potential fields), path tracking and control, each with an animation. Run these first to see how planners think.

### [ompl/ompl](https://github.com/ompl/ompl)
The Open Motion Planning Library, a collection of sampling-based planners such as RRT and PRM used by many real systems.

### [ros-navigation/navigation2](https://github.com/ros-navigation/navigation2)
The standard navigation stack for mobile robots in ROS 2, covering costmaps, planners, controllers and behaviour trees.

### [moveit/moveit2](https://github.com/moveit/moveit2)
Motion planning for robot arms, with collision checking and trajectory generation.

## Optimisation and control tools

### [casadi/casadi](https://github.com/casadi/casadi)
A tool for nonlinear optimisation and optimal control with automatic differentiation. Many model-predictive controllers are built with it.

### [osqp/osqp](https://github.com/osqp/osqp)
A fast solver for quadratic programs, which sit inside many robot controllers.

### [loco-3d/crocoddyl](https://github.com/loco-3d/crocoddyl)
An optimal control library for robot trajectories, used for legged and manipulator robots.

### [RobotLocomotion/drake](https://github.com/RobotLocomotion/drake)
Modelling, simulation and trajectory optimisation in one toolbox, with excellent lecture notes alongside it.

## Simulators

### [google-deepmind/mujoco](https://github.com/google-deepmind/mujoco)
A fast and accurate physics simulator for contact-rich robots. The browser demo you started with is built on it.

### [zalo/mujoco_wasm](https://github.com/zalo/mujoco_wasm)
The source of the browser demo. Reading it shows how a physics engine can run on a web page.

### [google-deepmind/mujoco_menagerie](https://github.com/google-deepmind/mujoco_menagerie)
A collection of high-quality MuJoCo models of real robots, including arms, quadrupeds and humanoids. Use it to try a planner on a real robot model.

### [google-deepmind/mujoco_mpc](https://github.com/google-deepmind/mujoco_mpc)
Model-predictive control built on MuJoCo with an interactive interface, good for seeing planning happen in real time.

### [google-deepmind/mujoco_playground](https://github.com/google-deepmind/mujoco_playground)
A suite of GPU-accelerated robot learning environments built on MuJoCo. It connects directly to Stage 7.

### [bulletphysics/bullet3](https://github.com/bulletphysics/bullet3)
The Bullet physics engine and its PyBullet interface, a long-standing and beginner-friendly choice.

### [gazebosim/gz-sim](https://github.com/gazebosim/gz-sim)
The modern Gazebo simulator that pairs naturally with ROS 2.

### [isaac-sim/IsaacSim](https://github.com/isaac-sim/IsaacSim)
NVIDIA's photorealistic robot simulator. It needs a capable NVIDIA graphics card.

### [Genesis-Embodied-AI/Genesis](https://github.com/Genesis-Embodied-AI/Genesis)
A newer, very fast physics platform aimed at robotics and embodied AI research.

### [haosulab/ManiSkill](https://github.com/haosulab/ManiSkill)
A GPU-parallel simulator and benchmark for robot manipulation.

## Robot software framework

### [ros2/ros2](https://github.com/ros2/ros2)
The meta-repository for ROS 2, the common middleware that connects sensors, planners and controllers. Most robotics jobs expect you to know it.

### [ros-controls/ros2_control](https://github.com/ros-controls/ros2_control)
The framework that connects controllers to real or simulated hardware.

## What to be able to do before moving on

You should be able to run an RRT planner in a 2D map, load a robot model into a simulator, and drive it to a goal with a controller. A good project is a simulated arm that reaches a target using your own inverse kinematics.

## Trending and most-starred additions (checked 25 Nov 2026)

Star counts below are approximate figures reported by public aggregator pages on 25 Nov 2026, so treat them as a rough guide to popularity, not exact numbers. Entries without a count had no figure in the pages I could reach. Links not marked as checked are from memory, so confirm they open.

### Most popular simulators
[Genesis-Embodied-AI/Genesis](https://github.com/Genesis-Embodied-AI/Genesis) has by far the most stars in an embodied-AI ranking, at about 28.6k. [newton-physics/newton](https://github.com/newton-physics/newton) is a GPU-accelerated physics engine built on NVIDIA Warp and aimed at roboticists, listed at about 5.2k stars. [cyberbotics/webots](https://github.com/cyberbotics/webots) is listed at about 4.5k stars and is a long-established, beginner-friendly simulator. [haosulab/ManiSkill](https://github.com/haosulab/ManiSkill) is at about 2.9k, and [google-deepmind/mujoco_playground](https://github.com/google-deepmind/mujoco_playground) at about 2.3k.

### The current trend: MuJoCo on the GPU
[google-deepmind/mujoco_warp](https://github.com/google-deepmind/mujoco_warp) is the GPU-accelerated version of MuJoCo. [mujocolab/mjlab](https://github.com/mujocolab/mjlab) combines Isaac Lab's manager-based API with MuJoCo Warp, and robot makers such as PAL Robotics have started publishing their robots for it. If you want fast parallel simulation without Isaac Sim's hardware needs, this is the direction to watch.

### Finding simulators
[knmcguire/best-of-robot-simulators](https://github.com/knmcguire/best-of-robot-simulators) is a ranked, regularly updated list of robot simulators with star counts. [RoboVerseOrg/RoboVerse](https://github.com/RoboVerseOrg/RoboVerse) aims to unify several simulators behind one interface.

### Choosing between them
One comparison describes Isaac Sim and Isaac Lab as having the most comprehensive ROS integration and the largest community, while Genesis is a 2024 framework built around differentiable physics. A practical rule: use MuJoCo to learn, Gazebo when you want ROS 2 integration, and a GPU-parallel simulator when you start training policies in Stage 7.
