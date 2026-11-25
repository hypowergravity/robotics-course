# Stage 23: Worked Exercises, Quizzes and Solutions

This file collects existing problem sets, practice exercises, quizzes and solution repositories that match the stages of the course, so a student can test themselves instead of only reading. Every item was found in web searches on 25 Nov 2026, and every GitHub repository named here was confirmed to exist with a read-only git check the same day. Existence is not quality. Student solution repositories in particular are unreviewed, so attempt each problem yourself before looking, and treat a student's answer as a hint rather than the truth.

A gap you should know about: I found no good public quizzes or worked problem sets for gearbox and actuator design, battery management systems, source-measure units, VLA models, UMI-style data collection, robot security or robot safety. For those stages the milestone projects in file 19 and the practice projects at the end of each file are the exercises, and the checkpoint questions at the end of this file give you a self-test.

## Maths (file 01)

### MIT 18.06 Linear Algebra problem sets with solutions
MIT OpenCourseWare publishes the Spring 2010 problem sets with solutions, the exams and the lecture videos, taught from Gilbert Strang's textbook. The 18.06SC Fall 2011 version adds problem-solving videos on every topic and problem sets with solutions to check your answers against. The MIT 18.06 homepage also keeps problem sets and exams from many past semesters, from 2006 to 2022. Start at [ocw.mit.edu/courses/18-06-linear-algebra-spring-2010](https://ocw.mit.edu/courses/18-06-linear-algebra-spring-2010/) and use the Fall 2011 version if you want the video recitations.

## Electronics (file 02)

### All About Circuits worksheets
Tony Kuphaldt's free [worksheets](https://www.allaboutcircuits.com/worksheets/) run from basic electricity to digital circuits. The Ohm's Law practice worksheet has 23 questions with answers, and the Kirchhoff's Laws worksheet has 48 questions with reveal-answer buttons and teacher notes. A separate set of more than 50 worksheets on DC circuits is indexed by the ComPADRE physics library. These are the best free electronics exercises I found, and they suit the early part of file 02. Combine them with the Falstad simulator by building each circuit and checking your answer.

## Mechanics and kinematics (files 03 and 04)

### Modern Robotics practice exercises with solutions
The book's authors publish a [practice exercises PDF](https://hades.mech.northwestern.edu/images/e/ef/MR_practice_exercises.pdf) with chapter-by-chapter exercises and worked solutions, covering configuration space, rigid-body motions, forward and inverse kinematics, velocity kinematics, dynamics and trajectory generation. The Northwestern ME 449 course archive also posts old midterms with solutions, including 2022, 2023 and 2024 midterms and a 2019 quiz. Use the practice PDF as your main problem source for files 04 and 12.

### University homework built on Modern Robotics
Yu Xiang's robotics course posts homework PDFs that pair textbook exercises, such as forward kinematics of an RRPRRR chain and inverse kinematics of an RRP chain, with a ROS coding problem on a Fetch robot in Gazebo using MoveIt. The Fall 2025 homework uses ROS 2 Jazzy. A Sharif University page lists eight robotics projects from coordinate frames and DH parameters through Jacobians, singularities, trajectory planning, dynamics and PD control, with PDF reports on GitHub. The University of Lincoln RBT1001 wiki at [LCAS/RBT1001](https://github.com/LCAS/RBT1001/wiki) lays out a weekly path from URDF and the TF tree to direct and inverse kinematics on paper and then in ROS and MoveIt.

### Student solution repositories for kinematics and dynamics
[mattephi/for.hw](https://github.com/mattephi/for.hw) contains fundamentals-of-robotics homework including a spherical-wrist manipulator, Jacobians and nullspace, and a linearised PD trajectory controller. [tiansy35/Kinematics-and-Dynamics](https://github.com/tiansy35/Kinematics-and-Dynamics) has solutions for forward and inverse kinematics of a five-degree-of-freedom manipulator. [Arya-Ebrahimi/robotics-spring2023](https://github.com/Arya-Ebrahimi/robotics-spring2023) holds one student's ROS 2 homework solutions, written against the course lab repository [arashsm79/robotics-lab](https://github.com/arashsm79/robotics-lab). Use them only after you have tried the problem.

## Control (file 12)

### Underactuated Robotics assignments
MIT's [Underactuated Robotics](https://underactuated.csail.mit.edu/) problem sets are taken directly from the textbook's chapter exercises, and many are coding problems in Jupyter notebooks, such as cart-pole balancing, minimum-time control and pendulum dynamic programming. The Spring 2024 assignments are posted at pages such as underactuated.csail.mit.edu/Spring2024/set_1.html. A student's homework solutions for the 2019 course are in [jam643/underactuatedrobotics-6p832-jessem](https://github.com/jam643/underactuatedrobotics-6p832-jessem), which is older and uses an earlier Drake setup.

### Control Tutorials and PID quizzes
The University of Michigan Control Tutorials for MATLAB and Simulink walk through PID, root locus, frequency domain and state-space design, and MathWorks offers a browser-based version you can run without installing MATLAB. MATLAB Academy has a self-paced PID course with automated feedback on motor speed and quadcopter altitude. For Python, the [minhyeong10/optimal_control_tutorial](https://github.com/minhyeong10/optimal_control_tutorial) repository gives clean LQR, iLQR and MPC examples to modify. For quiz-style checks, one open textbook site has a chapter quiz on PID control and tuning, and Sanfoundry has more than a thousand multiple-choice control-systems questions, though that site's answers are unreviewed. Toronto Metropolitan University also publishes a free open textbook, Introduction to Control Systems, with a chapter on PID tuning and stability.

## State estimation (file 05)

### Kalman and Bayesian Filters in Python
[rlabbe's book](https://github.com/rlabbe/Kalman-and-Bayesian-Filters-in-Python) is written as Jupyter notebooks, and its README says every exercise has a solution, which the author deliberately did so independent readers are not stuck. This is the single best exercise-plus-solution resource for the state-estimation stage.

## Learning (files 07 and 08)

### Spinning Up exercises
OpenAI's [spinningup](https://github.com/openai/spinningup) includes a page of exercises with starter files and solution files for PyTorch, such as the Gaussian log-likelihood and an MLP diagonal Gaussian policy for PPO. You run the file to check your work automatically. The project is in maintenance mode, so expect version friction.

### Hugging Face Deep RL course
The free course has a quiz at the end of each unit and Colab hands-on notebooks, and learners can check their progress and earn a certificate. A maintenance notice says the content remains accessible.

### Karpathy's Neural Networks: Zero to Hero
The [official repository](https://github.com/karpathy/nn-zero-to-hero) lists exercises in each lecture's description. Community solution repositories include [spolivin/nnzerotohero_solutions](https://github.com/spolivin/nnzerotohero_solutions), [0ssamaak0/Karpathy-Neural-Networks-Zero-to-Hero](https://github.com/0ssamaak0/Karpathy-Neural-Networks-Zero-to-Hero) and [chizkidd/Karpathy-Neural-Networks-Zero-to-Hero](https://github.com/chizkidd/Karpathy-Neural-Networks-Zero-to-Hero), the last with exercise notebooks for micrograd, bigrams, MLP and batch norm. They fit the micrograd step in file 07.

### Hugging Face Robotics Course with LeRobot
Hugging Face's free [Robotics Course](https://huggingface.co/learn/robotics-course) is based on the Robot Learning Tutorial, covers classical robotics and learning-based approaches with LeRobot, and says each major unit ends with an interactive quiz alongside hands-on code. NVIDIA also publishes a sim-to-real course for the SO-101 arm that builds on LeRobot. Use these alongside file 08.

## Checkpoint questions for the stages without public quizzes

These are questions I wrote myself, so check your answers against the files and textbooks rather than treating them as authoritative.

For gearboxes and actuators (file 15), explain why a low gear ratio makes an actuator more backdrivable, and say what limits continuous torque. For batteries (file 02), explain what a battery management system must do when one cell is lower than the others, and why passive balancing wastes energy. For test instruments (file 11), describe how you would measure a motor's torque constant with a load cell and a current probe. For safety (file 16), explain the difference between an emergency stop that cuts power and one that brakes under control, and when each is appropriate. For security (file 21), list three ways an attacker with physical access could take over a motor controller and one defence for each. For real-time (file 20), explain why worst-case latency matters more than average latency for a 1 kHz control loop.
