# Stage 20: Kernel Engineering, RTOS and Real-Time Control

Your control loop is only as good as the operating system that schedules it. This stage covers the Linux kernel side, microcontroller real-time operating systems, and how to measure whether your timing is good enough. Items marked "search-confirmed" were found on 25 Nov 2026, and the rest are from memory, so check links before relying on them.

## Two things called PID

In file 12, PID means proportional-integral-derivative, the three-term feedback controller. In Linux, PID means process identifier, the number the kernel gives every running process. They meet in practice because a PID controller usually runs inside a process with a process ID, and the scheduling of that process decides whether your controller meets its deadlines. When a ROS node hangs you find its process ID with ps or htop and stop it with kill, and when you want a control loop to be reliable you pin that process to a CPU core and give it a real-time priority with tools such as taskset and chrt (from memory).

## Why timing matters

A robot is a multi-rate system. One engineering note lists a current loop at 10 to 40 kHz, joint servo control at about 1 kHz, Cartesian control at 200 to 500 Hz, motion planning in the millisecond range and perception around tens of milliseconds, and says the fast tiers need real-time guarantees while planning and perception can run on standard Linux (search-confirmed). The ROS 2 documentation gives the classic example of an inverted pendulum that falls over if the controller blocks for an unexpectedly long time (search-confirmed).

## Real-time Linux

### PREEMPT_RT
PREEMPT_RT does not make Linux faster, it makes it more deterministic by turning non-preemptible sections into preemptible ones, and a university tutorial states it has been merged into mainline Linux as of version 6.12 (search-confirmed). The same material puts worst-case latency around 20 to 80 microseconds, enough for motor control at 1 kHz, and suggests that when you need more you let a microcontroller or FPGA handle the hard real-time part while Linux supervises. A RISC-V automotive paper measured worst-case latency of 13.4 ms without the patch and 159 microseconds with it using cyclictest (search-confirmed).

### Measuring latency
Install rt-tests and run cyclictest, which reports scheduling latency, and always look at the worst case rather than the average, since one missed deadline is what breaks a control loop (search-confirmed from the Obuda tutorial). The ROS 2 real-time programming demo uses a pendulum controller and prints minimum, maximum and mean latency, and tells you to set an rtprio limit in the security limits file and lock memory (search-confirmed).

### Dual-kernel alternatives
Xenomai and RTAI take a dual-kernel approach, while PREEMPT_RT patches the one kernel, and a ROS 2 performance paper discusses both (search-confirmed). For learning, start with PREEMPT_RT because it is now in the mainline kernel.

## Kernel engineering for roboticists

You rarely need to write kernel code, but you should understand device trees, drivers, interrupts, the scheduler, memory locking and how SPI, I2C and CAN drivers present devices to user space. Bootlin publishes free training slides on embedded Linux, Linux kernel and driver development, Yocto, Buildroot and real-time topics, which is the best free route in (search-confirmed). Read the kernel documentation for SocketCAN, then write a small character driver or an IIO sensor driver as an exercise (from memory).

## Microcontroller RTOS

FreeRTOS is known for simplicity and is MIT-licensed, Zephyr is a professional-grade open-source RTOS with a driver model and the MCUboot secure bootloader, and NuttX is a third option. micro-ROS supports FreeRTOS, Zephyr and NuttX, so you can run ROS 2 entities on a microcontroller (search-confirmed). Free resources include Richard Barry's FreeRTOS book, the Zephyr documentation and the Linux Foundation's Zephyr Essentials material (search-confirmed). A Linux Foundation talk builds a line-following robot on Zephyr using its device driver model (search-confirmed).

## A sensible architecture

Run the current loop in a microcontroller or driver chip, run joint servo control either on the microcontroller or on a PREEMPT_RT Linux process with a pinned core and locked memory, and run planning and perception on ordinary Linux. Tie them together with CAN or EtherCAT from file 13. Log timestamps at every boundary so you can find where latency enters.

## Practice projects

Run cyclictest on a Raspberry Pi with and without PREEMPT_RT and compare the worst case under CPU stress. Write a 1 kHz control loop in C++ with SCHED_FIFO, pinned to a core, and plot its jitter. Port a small motor-control task from bare metal to Zephyr or FreeRTOS and compare timing. Finally build a micro-ROS node on a microcontroller that publishes encoder data to a Linux ROS 2 graph.
