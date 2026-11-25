# Stage 13: Robot Software Engineering and Communication Buses

Most real robot problems are software and wiring problems rather than algorithm problems. This stage covers the habits and plumbing that sit under everything else: Linux, git, ROS 2, robot description files, and the buses that connect computers to motor drivers and sensors. A sourcing note: items marked "search-confirmed" were found on 25 Nov 2026, and unmarked repositories are listed from memory, so verify links first.

## Foundations to have before ROS 2

Be comfortable in a Linux terminal, with git branches and pull requests, with Python virtual environments, and with enough C++ to read a header and a CMake file. The Construct's free academy lists short courses on git and GitHub, modern C++ for robotics, URDF and path planning, which suits this need (search-confirmed that these courses exist on their academy page).

## ROS 2

### [ROS 2 official tutorials](https://docs.ros.org/)
Start with the official documentation. Work through nodes, topics, services, actions, parameters and launch files in order, because everything else assumes them. A community write-up notes that there is no single standard ROS 2 textbook, so learning by running demos and building small projects is the realistic route (search-confirmed).

### [fkromer/awesome-ros2](https://github.com/fkromer/awesome-ros2)
A curated list of ROS 2 resources, linked from the RosHowTwo learning-resource repository (search-confirmed).

### Free video courses
Open Robotics Discourse announced more than 120 free recorded ROS 1 and ROS 2 training sessions on YouTube, split into beginner, intermediate and advanced levels, with slides and a public GitHub repository (search-confirmed). A structured syllabus found in the same search recommends this chapter order: URDF and Xacro, Gazebo simulation, ros2_control, sensors in simulation, bag files, then a pick-and-place capstone.

### Paid but well-reviewed options
Edouard Renard's Udemy courses on ROS 2 basics and the Nav2 stack are well reviewed in the ROS forum thread and course pages found in the search. Treat these as optional since the free route above is enough.

## Robot description: URDF and Xacro

A URDF file describes links, joints and the visual and collision geometry of a robot, and Xacro adds macros and parameters to keep large files readable. Build a two-link arm URDF by hand, view it in RViz, then spawn it in simulation. The awesome-robot-descriptions list in file 04 gives hundreds of real examples to read.

## ros2_control

[ros2_control](https://github.com/ros-controls/ros2_control) is the hardware abstraction layer that connects controllers to real or simulated hardware. Learn it after the basics, because it is where your motor driver code from file 02 meets the rest of the stack.

## Communication buses

Pick the bus that fits the job. I2C and SPI connect nearby sensors on a board, UART and RS-485 are simple serial links, CAN is the usual choice for multiple motor drivers on a robot, and EtherCAT is used when many axes need tight synchronisation.

### CAN and CANopen
CAN suits low-level links between motion controllers, actuators and other components, and CANopen is a higher-level protocol widely used in robotics, with open-source libraries available (search-confirmed). The detail that a master can send process data objects and then one sync message to make all slaves act together is a good idea to learn early. On Linux, SocketCAN plus the [python-can](https://github.com/hardbyte/python-can) library is the practical way to start (from memory). Many open actuator projects in file 02, such as moteus and ODrive, speak CAN.

### EtherCAT
The IgH EtherCAT Master is an open-source Linux master written in C that runs as a kernel module, and SOEM is a lightweight open-source alternative (search-confirmed). One article describes EtherCAT as the most advanced choice when you need extremely high real-time performance and synchronised multi-axis control, and a vendor page shows an EtherCAT joint driven at up to 2000 Hz. Real-time behaviour usually needs a PREEMPT_RT kernel. Expect this to be a later, advanced step.

### Advice on keeping it simple
A robotics best-practice guide recommends avoiding multiple bus systems in one robot, so choose one bus per project where you can (search-confirmed).

## Logging, replay and debugging

Record everything with ROS 2 bag files so you can replay a failure at your desk, and use [Foxglove](https://foxglove.dev/) or [rerun](https://github.com/rerun-io/rerun) to visualise it. Add timestamps to every sensor message from the start, because later sensor fusion depends on them. File 08 covers rerun and mcap further.

## Practice projects

Write a ROS 2 node that publishes a fake sensor and another that filters it, then record and replay a bag. Build a URDF for a two-link arm and move it with ros2_control in simulation. Connect a microcontroller motor driver over CAN to a Linux machine and plot its feedback in real time, then measure the latency of your control loop and explain where the delay comes from.
