# Stage 8: Real-World Robot Data

**Start here:** [LeRobot Dataset Visualizer](https://huggingface.co/spaces/lerobot/visualize_dataset)

Simulation is clean, but real robots produce messy camera feeds, joint readings and human demonstrations. Modern robot learning depends on collecting, storing and replaying this data well. Browse a few datasets in the visualizer first, then use the tools below to record and train on your own.

## The main toolkit

### [huggingface/lerobot](https://github.com/huggingface/lerobot)
An open library for real-world robotics in PyTorch. It provides datasets, pretrained policies, training code and support for low-cost arms, so you can go from teleoperation to a trained policy on cheap hardware. This is the most important repository in this stage.

## Datasets and collection

### [google-deepmind/open_x_embodiment](https://github.com/google-deepmind/open_x_embodiment)
Tools for the Open X-Embodiment collaboration, which pooled robot data from many labs and many robot types into a shared format.

### [droid-dataset/droid](https://github.com/droid-dataset/droid)
A large real-world manipulation dataset collected in many environments, with the hardware and software setup used to record it.

### [ARISE-Initiative/robomimic](https://github.com/ARISE-Initiative/robomimic)
A framework for learning from demonstrations, with datasets and standard algorithms to compare.

### [ARISE-Initiative/robosuite](https://github.com/ARISE-Initiative/robosuite)
A simulation framework for manipulation research that works with robomimic.

### [Lifelong-Robot-Learning/LIBERO](https://github.com/Lifelong-Robot-Learning/LIBERO)
A benchmark for lifelong robot learning with many manipulation tasks.

### [tonyzhaozh/aloha](https://github.com/tonyzhaozh/aloha)
Hardware and software for the ALOHA bimanual teleoperation system, which produced many of the best-known demonstration datasets.

## Visualising and storing robot data

### [rerun-io/rerun](https://github.com/rerun-io/rerun)
A tool for logging and visualising multimodal data such as images, point clouds, transforms and time series. It makes debugging a real robot much faster.

### [foxglove/mcap](https://github.com/foxglove/mcap)
An open container format for robotics logs, widely used for recording sensor and message data.

## Habits worth building

Record everything with timestamps, keep camera and joint data synchronised, and inspect your data before you train on it. Many failed learning projects turn out to be problems in the data rather than in the algorithm. A good project is to record twenty demonstrations of a simple pick-and-place with a low-cost arm, look through them in the visualizer, and train a small policy.

## Where to go next

Continue with [the open hardware file](09-open-hardware-robots.md) to choose a robot you can build and collect data with.

## Trending and most-starred additions (checked 25 Nov 2026)

Star counts below are approximate figures reported by public aggregator pages on 25 Nov 2026, so treat them as a rough guide to popularity, not exact numbers. Entries without a count had no figure in the pages I could reach. Links not marked as checked are from memory, so confirm they open.

### LeRobot's recent additions
LeRobot is the most-starred project in this area, at about 28.7k. Its version 4.0 introduced Datasets v3.0, new VLA models such as PI0.5 and GR00T N1.5, a plugin system for hardware, and a command-line tool for editing datasets (merging, deleting episodes and more). NVIDIA and Hugging Face have also brought Isaac Teleop, an open framework for capturing human demonstrations in standard formats, and the GR00T 1.7 model to LeRobot workflows.

### Related projects
[ubi-coro/lerobot-hil-serl](https://github.com/ubi-coro/lerobot-hil-serl) adds human-in-the-loop reinforcement learning on top of LeRobot. [ROBOTIS-GIT/vuer](https://github.com/ROBOTIS-GIT/vuer) is a 3D visualisation tool for robotics and VR, and ROBOTIS also publishes a ROS 2 integration for LeRobot built on zenoh.

### New large datasets to know about
EgoVerse is a large egocentric human dataset collected around the world for robot learning (arXiv 2604.07607). EgoLive is another large egocentric dataset from real-world human tasks. [MrKeee/FastUMI-100K](https://github.com/MrKeee/FastUMI-100K) is a large UMI-style dataset of complex dual-arm tasks. TWIST2 released a humanoid teleoperation dataset at twist-data.github.io. See the advanced file for how these connect to data collection hardware.
