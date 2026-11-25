# Stage 12: Control Theory and Rigid-Body Dynamics

Control is what turns a motor and a model into a robot that does what you ask. This stage belongs between kinematics (file 04) and state estimation (file 05) in your study order, although you can return to it after the electronics file if you want to tune a real motor early. A note on sourcing: the repositories below marked "search-confirmed" were found in web searches on 25 Nov 2026, and the rest are well-known projects listed from memory, so check each link before relying on it.

## A note on the word PID

In this file PID means proportional-integral-derivative, the three-term feedback controller. In Linux, PID means process identifier, the number the kernel gives each running process. A PID controller usually runs inside a process that has a process ID, and how that process is scheduled decides whether the controller meets its deadlines, which is the subject of file 20.

## How to think about this stage

A controller compares what you want with what you measure and decides what to command. PID does this with three simple terms, LQR does it optimally for a linear model, and model predictive control (MPC) repeatedly solves a small optimisation over the near future. Dynamics tells you the torques needed to produce a motion, which is the model every advanced controller leans on. If you can write the manipulator equation M(q)q'' + C(q,q')q' + g(q) = tau and explain each term, you have the core idea.

## Start here: the textbook that doubles as software

### [Underactuated Robotics, Russ Tedrake](https://underactuated.mit.edu/)
This free online book from MIT covers nonlinear dynamics and control with a focus on mechanical systems, with interactive Jupyter notebooks written against Drake. Its appendix on multi-body dynamics derives the manipulator equations and is a gentle way into dynamics. Lecture videos are on YouTube, and the notes point to Craig's textbook as a practical guide to kinematics and dynamics (search-confirmed).

### [Modern Robotics, Lynch and Park](https://hades.mech.northwestern.edu/index.php/Modern_Robotics)
The book has a free preprint, free video lectures and a code library in Python, MATLAB and Mathematica. Its Coursera specialisation includes a dedicated course on robot dynamics and another on motion planning and control (search-confirmed). If you already used it for kinematics in file 04, continue into its dynamics and control chapters here.

## Classical and optimal control in Python

### [python-control/python-control](https://github.com/python-control/python-control)
The Python Control Systems Library implements analysis and design of feedback systems, including stability margins, eigenvalue placement, LQR, H2 and Hinf design, a Kalman filter-style estimator and MPC (search-confirmed). Its examples are drawn from standard textbooks, which makes it a good companion while you read.

### [minhyeong10/optimal_control_tutorial](https://github.com/minhyeong10/optimal_control_tutorial)
A small teaching repository with clean Python implementations of LQR, iLQR and differential dynamic programming, and linear MPC, including demos on a double integrator, a manipulator and an inverted pendulum (search-confirmed). Reading and running these short scripts is a fast way to see the algorithms without a heavy framework.

### [zgrobot/PyAdvancedControl](https://github.com/zgrobot/PyAdvancedControl)
Python samples of LQR regulation and tracking, finite-horizon optimal control and several MPC variants written with cvxpy and cvxopt, including one that calls a solver directly without a modelling layer (search-confirmed). It is older, so expect to adjust dependency versions.

## Solvers and frameworks for real MPC (from memory)

### [casadi/casadi](https://github.com/casadi/casadi)
A symbolic framework with automatic differentiation that most nonlinear MPC projects build on. It also appears in file 06.

### [acados/acados](https://github.com/acados/acados)
A fast embedded solver library for nonlinear MPC, popular when the controller must run on real hardware at high rates.

### [do-mpc/do-mpc](https://github.com/do-mpc/do-mpc)
A Python toolbox for nonlinear and robust MPC. The acados-related literature cites it as a standard open framework (search-confirmed that it is cited; the link is from memory).

### [osqp/osqp](https://github.com/osqp/osqp) and [stack-of-tasks/pinocchio](https://github.com/stack-of-tasks/pinocchio)
OSQP is the quadratic-program solver behind many linear MPC and whole-body controllers, and Pinocchio computes rigid-body dynamics quantities such as mass matrices and inverse dynamics quickly. Both also appear in files 04 and 06.

### [RobotLocomotion/drake](https://github.com/RobotLocomotion/drake)
Drake combines multibody dynamics, optimisation and control design, and is the toolbox behind Tedrake's book.

## Rigid-body dynamics, step by step

Learn it in this order. First derive the equations of motion for a pendulum with Lagrangian mechanics. Next do a two-link arm by hand and see the M, C and g terms appear. Then use Pinocchio or Drake to compute the same quantities numerically and compare. Finally implement computed-torque control, which cancels the dynamics with a model and leaves a simple linear error system, and see how it breaks when your model is wrong. Featherstone's recursive algorithms are what libraries use under the hood, and Tedrake's appendix points to them.

## Practice projects

Tune a PID loop on a simulated DC motor and plot step responses while you vary each gain. Design an LQR for an inverted pendulum on a cart and compare it with your PID. Write a linear MPC for a double integrator with input limits and watch it respect the constraints that LQR ignores. Finally implement computed-torque control for a two-link arm in MuJoCo using Pinocchio for the dynamics, then add model error and see what happens.

## What to be able to explain before moving on

Why a PID loop can go unstable when you raise the gain, what gain and phase margin tell you, what the LQR cost weights mean physically, why MPC handles constraints that LQR cannot, and why computed-torque control needs an accurate model.
