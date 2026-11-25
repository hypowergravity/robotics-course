# Robotics Course Map

This course takes from the mathematics of motion to robots that learn from real data. Each stage has its own file with an interactive starting point, a set of well-known GitHub repositories to study, and a short test of what you should be able to do before moving on.

The first three give you the foundations (maths, electronics and mechanical structure). Stages 4 and 5 give you the core robot loop of acting and sensing. Stages 6 to 8 move from simulation to learning to real-world data, and the bonus file shows open robots you can build to practise on.

| Stage | File | Interactive starting point |
|---|---|---|
| 1. Maths | [01-maths.md](01-maths.md) | [Immersive Linear Algebra](https://immersivemath.com/ila/index.html) |
| 2. Electronics | [02-electronics.md](02-electronics.md) | [Falstad Circuit Simulator](https://falstad.com/circuit/) |
| 3. Mechanics | [03-mechanics.md](03-mechanics.md) | [Gears](https://ciechanow.ski/gears/) |
| 4. Kinematics | [04-kinematics.md](04-kinematics.md) | [Inverse Kinematics](https://zalo.github.io/blog/inverse-kinematics/) |
| 5. State estimation | [05-state-estimation.md](05-state-estimation.md) | [Kalman Filter in Pictures](https://www.bzarg.com/p/how-a-kalman-filter-works-in-pictures/) |
| 6. Planning and simulation | [06-planning-and-simulation.md](06-planning-and-simulation.md) | [MuJoCo in the browser](https://zalo.github.io/mujoco_wasm/) |
| 7. Robot learning | [07-robot-learning.md](07-robot-learning.md) | [RL demo](https://cs.stanford.edu/people/karpathy/convnetjs/demo/rldemo.html) |
| 8. Real-world robot data | [08-real-world-robot-data.md](08-real-world-robot-data.md) | [LeRobot Dataset Visualizer](https://huggingface.co/spaces/lerobot/visualize_dataset) |
| Bonus. Open hardware | [09-open-hardware-robots.md](09-open-hardware-robots.md) | Build a low-cost arm |
| Test bench | [11-test-bench-and-instruments.md](11-test-bench-and-instruments.md) | [MC-Dyno](https://impressivetaste.github.io/Dyno-MCHP-Repository-WIP/docs/_build/html/index.html) |
| Advanced. VLAs, egocentric data, UMI, teleoperation, depth, FPGA edge AI | [10-advanced-vla-egocentric-umi-edge.md](10-advanced-vla-egocentric-umi-edge.md) | [UMI](https://umi-gripper.github.io) |
| Control theory and dynamics | [12-control-theory-and-dynamics.md](12-control-theory-and-dynamics.md) | [Underactuated Robotics](https://underactuated.mit.edu/) |
| Robot software and buses | [13-robot-software-and-buses.md](13-robot-software-and-buses.md) | [ROS 2 docs](https://docs.ros.org/) |
| Sensors, calibration, perception | [14-sensors-calibration-and-perception.md](14-sensors-calibration-and-perception.md) | [Kalibr](https://github.com/ethz-asl/kalibr) |
| Actuator and gearbox design | [15-actuator-and-gearbox-design.md](15-actuator-and-gearbox-design.md) | [OpenTorque](https://github.com/G-Levine/OpenTorque-Actuator) |
| Safety | [16-safety.md](16-safety.md) | Build an emergency stop |
| Sim-to-real and locomotion | [17-sim-to-real-and-locomotion.md](17-sim-to-real-and-locomotion.md) | [legged_control](https://github.com/qiayuanl/legged_control) |
| Free courses and books | [18-free-courses-and-books.md](18-free-courses-and-books.md) | [Modern Robotics](https://hades.mech.northwestern.edu/index.php/Modern_Robotics) |
| Kernel, RTOS and real-time | [20-kernel-rtos-and-real-time.md](20-kernel-rtos-and-real-time.md) | [Bootlin training](https://bootlin.com/training/) |
| Robot security (hardware and cyber) | [21-robot-security-embedded-and-cyber.md](21-robot-security-embedded-and-cyber.md) | [Robot Vulnerability Database](https://github.com/aliasrobotics/RVD) |
| Hardware debug tools | [22-hardware-debug-and-hacking-tools.md](22-hardware-debug-and-hacking-tools.md) | Tigard, Bus Pirate 6, ChipWhisperer-Husky |
| Exercises, quizzes and solutions | [23-exercises-quizzes-and-solutions.md](23-exercises-quizzes-and-solutions.md) | [Modern Robotics practice exercises](https://hades.mech.northwestern.edu/images/e/ef/MR_practice_exercises.pdf) |
| Suggested order and milestones | [19-learning-path-and-milestones.md](19-learning-path-and-milestones.md) | Start with Phase 1 |

## A finishing project

Build a low-cost arm, solve its inverse kinematics yourself, smooth its sensor readings with a filter, test its motions in simulation, and finally record demonstrations and train a policy to repeat a pick-and-place task.


