# Stage 17: Sim-to-Real and Locomotion

This stage connects simulation (file 06) and learning (file 07) to real hardware, and adds legged and humanoid walking control. Items marked "search-confirmed" were found on 25 Nov 2026, and the rest are from memory.

## The sim-to-real gap

A policy trained in simulation fails on hardware when the simulator is wrong about actuators, friction, delays or contacts. Four broad strategies are used. Domain randomisation trains over wide ranges of physical parameters, but it relies on heuristics and can produce conservative policies when poorly tuned. System identification measures the real parameters. Residual and learned models patch the simulator, and online adaptation estimates parameters while running (search-confirmed from a CMU paper and a legged-robot survey). The survey notes that actuator-model identification was a key enabler of zero-shot transfer for legged robots.

## Open code to study

### [LeCAR-Lab/SPI-Active](https://github.com/LeCAR-Lab/SPI-Active)
Sampling-based parameter identification with active exploration for legged robots. The paper reports transfer improvements of 42 to 63 percent over baselines on locomotion tasks (search-confirmed).

### SimGAN
A method that identifies the simulator with adversarial reinforcement learning rather than hand-tuned randomisation. The code is at the [jyf588/SimGAN](https://github.com/jyf588/SimGAN) repository named in the paper (search-confirmed).

### ETH legged-robot sim-to-real pipeline
A 2025 paper from Marco Hutter's group presents an open-source modelling pipeline for systematic sim-to-real transfer across diverse legged robots, with focus on actuator-specific effects (search-confirmed). Their IsaacLab-based tooling connects to file 07.

### Actuator networks
The cycloidal QDD paper in file 15 notes that actuator networks improve actuator models and so help transfer, and it pairs learned torque estimation with its hardware (search-confirmed).

## Model-based legged control

### [qiayuanl/legged_control](https://github.com/qiayuanl/legged_control)
A nonlinear MPC plus whole-body control stack built on OCS2 and ros-control. It lists about 1.5k stars and claims deployment on a Unitree A1 within hours (search-confirmed). Its authors warn that OCS2 is a huge monorepo and you should only compile the legged-robot packages.

### [leggedrobotics/ocs2](https://github.com/leggedrobotics/ocs2)
The optimal control library underneath it, with a legged-robot example and perceptive locomotion MPC (search-confirmed).

### Whole-body MPC with MuJoCo
A 2025 paper shows that plain iLQR using MuJoCo as the forward model gives real-time whole-body control on a quadruped and a full-size humanoid, and releases an interactive GUI for tuning (search-confirmed). It is a good bridge between file 06 and real hardware.

### Other examples
The hunter_bipedal_control repository applies NMPC and WBC to a biped, qm_control applies the same idea to quadruped manipulators, and the dfki-quad repository benchmarks QP formulations and solvers for walking (all search-confirmed). Reading two of these side by side shows what is common across implementations.

## Learning-based locomotion

Files 07 and 17 together cover the standard route: train in IsaacLab, legged_gym, mjlab or Genesis with rsl_rl or similar, randomise and identify, then deploy through unitree_sdk2 or your own driver. The Unitree and humanoid projects in file 09 give you hardware to try this on.

## Practice projects

Identify a motor-plus-gearbox model on your own test bench from file 11, then plug it into a simulated joint and check that the step response matches. Train a policy on a simple simulated quadruped with and without randomisation, and explain the difference. If you have a Unitree-type robot, run legged_control in simulation first and read its estimation code before touching hardware.
