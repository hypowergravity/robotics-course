# Advanced Stage: VLAs, Egocentric Data, UMI Devices, Teleoperation, Depth and Edge AI

This file covers the modern data-and-deployment side of robot learning. Read it after Stages 7 and 8. The sections go in the order of a real project: choose a model, collect data (egocentric video, UMI-style handhelds, teleoperation), add depth perception, and finally deploy on small hardware such as an FPGA.

A note on accuracy: I confirmed the project pages and repositories for UMI, HumanEgo, Open Teach, Open-TeleVision, GELLO, EgoMimic, hls4ml, FINN, Depth Anything V2 and VisionProTeleop by web search. Repository addresses for the other entries are from memory, so check that each link opens before relying on it.

## 1. Open-source VLA models (vision-language-action)

A VLA takes camera images and a language instruction and outputs robot actions. Start with the smallest model you can fine-tune on your own data, then move up.

### [huggingface/lerobot](https://github.com/huggingface/lerobot)
Includes SmolVLA, a compact 450M-parameter VLA that pairs a small vision-language model with a flow-matching action expert. It is the most realistic first VLA to train on a single consumer GPU with data from a low-cost arm.

### [openvla/openvla](https://github.com/openvla/openvla)
The first fully open 7B-parameter VLA, built on a Llama 2 language model and a fused vision encoder. Read its code to understand how actions become tokens.

### [moojink/openvla-oft](https://github.com/moojink/openvla-oft)
The optimised fine-tuning recipe for OpenVLA, which makes adapting the model to a new robot faster and more successful. Look here when plain OpenVLA is too slow.

### [Physical-Intelligence/openpi](https://github.com/Physical-Intelligence/openpi)
Open models and code from Physical Intelligence, including the pi0 family of flow-based policies.

### [NVIDIA/Isaac-GR00T](https://github.com/NVIDIA/Isaac-GR00T)
A foundation model for humanoid skills that pairs a vision-language backbone with a diffusion transformer action head.

### [octo-models/octo](https://github.com/octo-models/octo)
A small 93M-parameter generalist policy with a diffusion action head, trained on the Open X-Embodiment data. Its small size makes it good for learning how such policies are built.

### [Psi-Robot/Awesome-VLA-Papers](https://github.com/Psi-Robot/Awesome-VLA-Papers)
A curated reading list of VLA papers organised by how they represent actions. Use it to keep up, because this field changes quickly.

## 2. Egocentric (first-person) human data

The idea is that people wearing a camera can collect manipulation data anywhere, without a robot, and a robot policy can then learn from it.

### [Project Aria](https://www.projectaria.com/) and [projectaria_tools](https://github.com/facebookresearch/projectaria_tools)
Meta's research glasses that record egocentric video with hand tracking and device SLAM. Access is by application, so check the site for current availability. The tools repository lets you read and process the recordings.

### [EgoMimic](https://egomimic.github.io/)
A full-stack framework that co-trains policies from egocentric human video and teleoperated robot data, with a low-cost bimanual robot designed to reduce the gap between human and robot viewpoints. The project page links the code and bill of materials.

### [TX-Leo/HumanEgo](https://github.com/TX-Leo/HumanEgo)
An open framework for learning robot policies from minutes of human egocentric video, with code, a dataset and documentation. You can train on its released dataset without any hardware, which makes it a good place to begin.

### [facebookresearch/Ego4d](https://github.com/facebookresearch/Ego4d)
Tools for the very large Ego4D egocentric video dataset of daily activities, useful for pretraining and for understanding first-person video.

### [apple/ml-egodex](https://github.com/apple/ml-egodex)
Code for EgoDex, a large egocentric dataset aimed at dexterous manipulation.

## 3. UMI and UMI-like handheld devices

A UMI is a handheld gripper with a camera, so a person can demonstrate a task while the system records what a robot would need to learn it.

### [real-stanford/universal_manipulation_interface](https://github.com/real-stanford/universal_manipulation_interface)
The original Universal Manipulation Interface: a 3D-printed handheld parallel gripper with a GoPro as the only sensor, plus the training and deployment code. The repository links the hardware guide, data collection instructions and SLAM pipeline, and it includes a sample dataset you can train on.

### [Fast-UMI](https://fastumi.com/)
A more scalable and hardware-independent variant. It uses a handheld device for collection and a separate robot-mounted device for inference, designed to work with a wide range of grippers. See the project site for the code link.

### Newer variants
Research groups keep extending the idea with tactile sensing, force feedback and combined teleoperation and handheld use (for example the RUMI paper). Search for "UMI" with "tactile" or "dexterous hand" to find current projects.

## 4. Teleoperation

Teleoperation is how most good robot data is collected today. The choice is between leader-follower arms, VR headsets and phones.

### [wuphilipp/gello_software](https://github.com/wuphilipp/gello_software)
GELLO is a low-cost leader arm built from 3D-printed parts and off-the-shelf motors that copies the kinematics of the target arm. Designs exist for Franka, UR5 and xArm, and the design idea transfers to other arms.

### [aadhithya14/Open-Teach](https://github.com/aadhithya14/Open-Teach)
A VR teleoperation system built on the Meta Quest 3, supporting several arms and hands including Franka, xArm, Jaco, Allegro and Hello Stretch.

### [OpenTeleVision/TeleVision](https://github.com/OpenTeleVision/TeleVision)
Immersive teleoperation with stereo video streamed from the robot to the operator's VR headset, so the operator sees through the robot's eyes. Useful when you want egocentric data from a humanoid.

### [Improbable-AI/VisionProTeleop](https://github.com/Improbable-AI/VisionProTeleop)
Uses Apple Vision Pro hand tracking to control robots and collect training data.

### [dexsuite/dex-retargeting](https://github.com/dexsuite/dex-retargeting)
Maps human hand motion onto robot hand kinematics. Essential if you want a multi-fingered hand to follow your fingers.

### [TeleDex](https://orayyan.com/teledex)
An open system that uses an ordinary phone and a 3D-printable wrist mount for teleoperating arms and dexterous hands.

### [tonyzhaozh/aloha](https://github.com/tonyzhaozh/aloha)
The leader-follower bimanual system from the hardware file, still the reference design for collecting bimanual demonstrations.

## 5. Depth perception

Depth can come from a sensor (stereo, time of flight, structured light) or from a neural network that estimates it from ordinary images. A robot project usually mixes both.

### [DepthAnything/Depth-Anything-V2](https://github.com/DepthAnything/Depth-Anything-V2)
A strong monocular depth model with several sizes and metric-depth variants. It runs on a single RGB camera, so it works with a wrist camera or a GoPro.

### [Depth Anything 3](https://depth-anything-3.github.io/)
The next generation, which estimates depth and camera pose from any number of images. See the project page for the code.

### [facebookresearch/vggt](https://github.com/facebookresearch/vggt)
A feed-forward transformer that predicts camera poses, depth and 3D points from a set of images in a single pass.

### [naver/dust3r](https://github.com/naver/dust3r)
The model that started the recent wave of learning-based multi-view geometry, predicting pointmaps from image pairs without calibration.

### [NVlabs/FoundationStereo](https://github.com/NVlabs/FoundationStereo)
A stereo-matching foundation model for accurate depth from two cameras.

### [apple/ml-depth-pro](https://github.com/apple/ml-depth-pro)
A model that produces sharp metric depth from a single image.

### [isl-org/Open3D](https://github.com/isl-org/Open3D)
A library for point clouds, meshes and RGB-D processing, useful for turning depth images into something a robot can plan with.

### [colmap/colmap](https://github.com/colmap/colmap)
The standard structure-from-motion tool for recovering camera poses and 3D structure from photos.

Depth hardware, including [RealSense](https://github.com/IntelRealSense/librealsense) and [OAK cameras](https://github.com/luxonis/depthai-core), is in the hardware file.

## 6. Edge AI and FPGAs

Running a large model on a robot is a deployment problem. The choice is between a GPU module such as a Jetson, a neural accelerator, or an FPGA, which gives you deterministic low latency and custom data paths at the cost of a harder toolchain.

### [fastmachinelearning/hls4ml](https://github.com/fastmachinelearning/hls4ml)
Translates trained neural networks into FPGA or ASIC firmware through high-level synthesis, aimed at very low-latency, low-power inference. A good first project is a small convolutional network for a camera task.

### [Xilinx/finn](https://github.com/Xilinx/finn)
AMD's open framework for dataflow neural network accelerators on FPGAs, which excels at very low bit-width quantised networks. It is often used together with Brevitas for quantisation-aware training.

### [Xilinx/PYNQ](https://github.com/Xilinx/PYNQ)
A Python framework for programming Zynq FPGAs, so you can control hardware from a notebook. It is the easiest way to begin on FPGA boards.

### [Xilinx/Vitis-AI](https://github.com/Xilinx/Vitis-AI)
AMD's toolchain for deploying models on its FPGA deep-learning processor units, as found on Kria boards.

### [dusty-nv/jetson-inference](https://github.com/dusty-nv/jetson-inference)
Tutorials and code for deploying vision models on NVIDIA Jetson. Compare it with the FPGA route, because the Jetson path is usually simpler to set up.

### [tensorflow/tflite-micro](https://github.com/tensorflow/tflite-micro)
Runs small neural networks on microcontrollers with no operating system.

### [microsoft/onnxruntime](https://github.com/microsoft/onnxruntime)
A cross-platform inference engine, useful for exporting a PyTorch policy once and running it on many targets.

### [openvinotoolkit/openvino](https://github.com/openvinotoolkit/openvino)
Intel's toolkit for optimising and running models on CPUs, integrated GPUs and NPUs.

### Hardware description tools
To go beyond model compilers and design your own FPGA logic, study [YosysHQ/yosys](https://github.com/YosysHQ/yosys) (open synthesis), [SpinalHDL/SpinalHDL](https://github.com/SpinalHDL/SpinalHDL) and [chipsalliance/chisel](https://github.com/chipsalliance/chisel) (hardware description in Scala), and [enjoy-digital/litex](https://github.com/enjoy-digital/litex) (building systems on a chip).

Starter boards include the AMD Kria KV260 and the PYNQ-Z2. A Turku University thesis comparing the KV260 with a Jetson Nano on mobile-robot tasks found the Jetson faster on one test model and easier to deploy, so treat FPGAs as the choice when you need fixed latency or custom logic, not as an automatic upgrade.

## Suggested data-collection kit

A GoPro and a 3D-printed UMI gripper for portable demonstrations, a leader-follower pair such as GELLO or a low-cost arm from the hardware file for teleoperated data, a Meta Quest 3 if you want VR teleoperation, and a depth camera for wrist or head mounting. Keep every camera and joint stream timestamped so you can replay it in the Stage 8 tools.

## A project that ties it together

Collect fifty demonstrations of one task with a UMI-style gripper and fifty with teleoperation, convert both into LeRobot format, fine-tune SmolVLA or Octo on them, add a depth estimate as an extra input, and compare success rates. Then quantise a small perception network and run it on an FPGA or Jetson to measure latency on the robot.

## Trending and most-starred additions (checked 25 Nov 2026)

Star counts below are approximate figures reported by public aggregator pages on 25 Nov 2026, so treat them as a rough guide to popularity. Entries without a count had no figure in the pages I could reach. Links not marked as checked are from memory, so confirm they open.

### VLA frameworks and toolboxes
[starVLA/starVLA](https://github.com/starVLA/starVLA) is a Lego-like codebase for developing VLA models, at about 3.9k stars. Dexbotic is an open-source VLA toolbox at about 3.2k stars. [keivalya/mini-vla](https://github.com/keivalya/mini-vla) is a minimal, beginner-friendly VLA that shows how a policy fuses images, text and robot state to produce actions, so it is the best place to understand the idea before reading larger codebases. [allenai/vla-evaluation-harness](https://github.com/allenai/vla-evaluation-harness) helps you evaluate models fairly. There are also reinforcement-learning fine-tuning projects such as verl-vla and RL2-VLA, which reflect the trend of improving a pretrained VLA with RL after supervised training. The NVIDIA GR00T family keeps updating, with N1.6 shown at CES 2026 and GR00T 1.7 now available through LeRobot. Gemini Robotics 2 is a prominent VLA that is not open.

### Curated VLA lists
[jonyzhang2023/awesome-embodied-vla-va-vln](https://github.com/jonyzhang2023/awesome-embodied-vla-va-vln) is the largest I found, at about 3.2k stars with around 700 resources, and it also tracks World Action Models. [DravenALG/awesome-vla-wam](https://github.com/DravenALG/awesome-vla-wam) has about 1.1k. [Jiaaqiliu/Awesome-VLA-Robotics](https://github.com/Jiaaqiliu/Awesome-VLA-Robotics) has about 500, and [yueen-ma/Awesome-VLA](https://github.com/yueen-ma/Awesome-VLA) accompanies a survey. [KwanWaiPang/Awesome-VLA](https://github.com/KwanWaiPang/Awesome-VLA) lists models such as X-VLA and pi0.5 with their code links. [TianxingChen/Embodied-AI-Guide](https://github.com/TianxingChen/Embodied-AI-Guide) is a wider embodied AI guide at about 13.4k stars. [OpenDriveLab/WholebodyVLA](https://github.com/OpenDriveLab/WholebodyVLA) targets whole-body humanoid loco-manipulation (about 335 stars).

### Egocentric data and UMI-style devices: new in 2026
NVIDIA's GEAR lab released GEAR DexUMI (a hand exoskeleton), GEAR UMI (a handheld gripper) and GEAR Neck (an active three-axis head for teleoperation) on 9 Nov 2026, with software on GitHub and hardware files on its site (research.nvidia.com/labs/gear/hardware-prototypes). Other recent research systems include EgoMI, which captures synchronised hand and active-head motion for semi-humanoid robots, Mobile UMI for mobile manipulation, EgoGuide, which adds head-mounted sensing and augmented-reality feedback to UMI-style collection, and RUMI, which combines a handheld device with haptic teleoperation. Large datasets to train on include FastUMI-100K ([MrKeee/FastUMI-100K](https://github.com/MrKeee/FastUMI-100K)), EgoVerse and EgoLive.

### Teleoperation: humanoids
TWIST2 is a portable, motion-capture-free humanoid teleoperation system that streams the robot's egocentric view and supports whole-body control from one operator, with an open dataset at twist-data.github.io. NVIDIA's Isaac Teleop is an open framework for collecting demonstrations from external devices in standard formats and now integrates with LeRobot.

### Depth: newest models
Depth Anything 3 reports better pose and geometry accuracy than VGGT and also improves on Depth Anything 2 for single images. [robbyant/lingbot-depth](https://github.com/robbyant/lingbot-depth) is a 2026 model for depth completion and monocular depth that is designed for robotics tasks such as dexterous grasping.

### FPGA and ROS 2 hardware acceleration
The Kria Robotics Stack (KRS) is a ROS 2 superset built around AMD's Kria modules, now maintained by the ROS 2 Hardware Acceleration Working Group. Its GitHub organisation, [ros-acceleration](https://github.com/ros-acceleration), holds the acceleration examples and the KV260 and KR260 firmware packages, and a 2026 community write-up called KRS Unleashed describes an easier prototyping flow. The Kria KV260 Vision AI Starter Kit lists at a $249 MSRP, and the KR260 Robotics Starter Kit is the robotics-focused board. [BrunoLevy/learn-fpga](https://github.com/BrunoLevy/learn-fpga) is a free course on FPGAs, Yosys, nextpnr and RISC-V that suits anyone who wants to design logic rather than only compile models.
