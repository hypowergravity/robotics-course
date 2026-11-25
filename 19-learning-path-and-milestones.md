# Stage 19: Suggested Order and Milestone Projects

The files are numbered by topic rather than strictly by study order. This page gives a path through them with a project at each milestone, so you always have something working. Treat the time estimates as rough guesses for someone studying part-time.

## Phase 1: Foundations (about 2 months)

Read file 01 on maths and file 02 up to basic circuits and motor drive, and start Modern Robotics from file 18. Learn git and Linux basics from file 13. Milestone project: build a circuit in the Falstad simulator and then on a breadboard that drives a small DC motor with PWM, and plot its step response.

## Phase 2: Kinematics and control (about 3 months)

Work through file 04 on kinematics, then file 12 on control and dynamics, and the mechanics in file 03. Milestone project: a two-link arm in simulation that follows a path using inverse kinematics and computed-torque control, then a printed version moved by hobby servos or small motors.

## Phase 3: Software and sensing (about 3 months)

Learn ROS 2 and URDF from file 13, sensors and calibration from file 14, and state estimation from file 05. Milestone project: a wheeled or arm robot with an IMU and camera that runs a Kalman filter or SLAM package, with its sensors calibrated and its data logged in bags.

## Phase 4: Real actuators and test bench (about 3 months)

Build your own joint using file 15, with FOC from file 02, and test it with file 11. Apply file 16's safety habits from the first power-up. Milestone project: a quasi-direct-drive joint with measured torque constant, backlash and thermal limit, and a written risk assessment.

## Phase 5: Planning, learning and sim-to-real (about 4 months)

Study files 06, 07, 08 and 17. Collect demonstrations with a low-cost arm from file 09 and train a policy with LeRobot. Milestone project: a teleoperated pick-and-place dataset recorded with LeRobot, an imitation policy trained on it and evaluated on the real arm.

## Phase 6: Advanced frontier (ongoing)

Pick from file 10: VLA models, UMI-style data collection, egocentric data, depth models and edge AI. Milestone project: fine-tune a small VLA on your own dataset and deploy it on edge hardware with measured latency.

## Habits that keep the path working

Finish every phase with a working demo and a short written report of what failed. Keep your hardware and software under git. Do not skip the safety file because the robot is small. When a stage feels too hard, return to the free course spine in file 18 and slow down.

## Final capstone

Build a complete low-cost robot arm with your own actuators, a calibrated camera, a ROS 2 stack, a safety stop, and a learned policy trained from your own demonstrations. Document it in a repository with a bill of materials, wiring diagrams and test results so another learner can reproduce it.
