# Stage 2: Electronics

**Start here:** [Falstad Circuit Simulator](https://falstad.com/circuit/)

Every sensor, motor and computer in a robot is a circuit. Simulate first so you understand voltage, current and signals, then move to real boards and real motor drivers. The repositories below are grouped in that order: simulation and design, then microcontroller platforms, then motor control.

## Simulation and circuit design

### [pfalstad/circuitjs1](https://github.com/pfalstad/circuitjs1)
The source of the simulator linked above. Reading how it steps a circuit through time is a good introduction to how any simulator works.

### [KiCad/kicad-source-mirror](https://github.com/KiCad/kicad-source-mirror)
A GitHub mirror of KiCad, the main open-source tool for drawing schematics and designing circuit boards. Once your breadboard prototype works, KiCad is how you turn it into a proper board.

## Microcontroller platforms

### [arduino/Arduino](https://github.com/arduino/Arduino)
The classic Arduino IDE and ecosystem. It is the easiest first step into reading sensors and driving motors from code.

### [espressif/esp-idf](https://github.com/espressif/esp-idf)
The official framework for ESP32 chips, which add Wi-Fi and Bluetooth at a low price. Many hobby robots use ESP32 boards as their brains.

### [raspberrypi/pico-sdk](https://github.com/raspberrypi/pico-sdk)
The C and C++ SDK for the Raspberry Pi Pico family. Its programmable I/O hardware is useful for precise motor and encoder signals.

### [micropython/micropython](https://github.com/micropython/micropython)
Python that runs directly on a microcontroller. It is the quickest way to experiment if you already know Python.

### [adafruit/circuitpython](https://github.com/adafruit/circuitpython)
Adafruit's beginner-friendly fork of MicroPython, with a very large library of sensor drivers.

### [platformio/platformio-core](https://github.com/platformio/platformio-core)
A build system and project manager that works across many boards, so one workflow covers Arduino, ESP32 and Pico projects.

## Motor control

### [simplefoc/Arduino-FOC](https://github.com/simplefoc/Arduino-FOC)
A friendly library for field-oriented control of brushless motors. It is the best place to learn how modern robot joints are driven smoothly.

### [odriverobotics/ODrive](https://github.com/odriverobotics/ODrive)
Firmware and documentation for a popular open brushless motor controller used in many robot arms and legged robots.

### [vedderb/bldc](https://github.com/vedderb/bldc)
The firmware behind VESC motor controllers. It is a mature, real-world example of high-quality motor control code.

### [mjbots/moteus](https://github.com/mjbots/moteus)
An open servo controller design aimed at robot actuators, with firmware, hardware files and clear documentation.

## Hardware to buy for this stage

A multimeter, a breadboard, an Arduino Uno or ESP32 board, a few hobby servos, a small brushed DC motor with an H-bridge driver, and a current-limited bench supply or a battery pack with a fuse. Start with low voltages so mistakes are cheap and safe.

## What to be able to do before moving on

You should be able to compute a voltage divider, explain why a motor needs a driver and a flyback diode, read a sensor over I2C or analog, and drive a motor from code with speed control. A good test is a small line follower or a servo that tracks a potentiometer.

## Trending and most-starred additions (checked 25 Nov 2026)

Star counts below are approximate figures reported by public aggregator pages on 25 Nov 2026, so treat them as a rough guide to popularity, not exact numbers. Entries without a count had no figure in the pages I could reach. Links not marked as checked are from memory, so confirm they open.

The most-starred open actuator designs in this area are the ones already listed. The mjbots moteus controller shows about 1.3k stars on the organisation page, and the Open Dynamic Robot Initiative's [open_robot_actuator_hardware](https://github.com/open-dynamic-robot-initiative/open_robot_actuator_hardware) is listed at roughly 1.3k in a community electronics list, though its last visible commit there was around 2022.

### [open-dynamic-robot-initiative/open-motor-driver-initiative](https://github.com/open-dynamic-robot-initiative/open-motor-driver-initiative)
An open-source driver for brushless motors that follows the same initiative's design philosophy. It has about 115 stars, so it is smaller but fits the same actuator designs.

### [cajt/list_of_robot_electronics](https://github.com/cajt/list_of_robot_electronics)
A community-maintained list of open motor controllers, including VESC, STMBL, OpenBLDC and many others. It is the quickest way to survey what exists before choosing one.

### Newer, smaller projects worth watching
A robot arm actuator built around the ESP32 (listed as robot-actuator-esp32-v8) has about 233 stars and ships PCB, firmware and CAD files. The EPFL Xplore team's Amulet is a high-power moteus alternative with up to 100 A peak phase current, aimed at legged robots. The Spectral Micro is a small brushless controller sold with open-source software. All three show the trend toward cheap, compact, CAN-connected joint controllers.

## Added: Battery management systems (BMS)

Star counts below are approximate figures from public aggregator pages on 25 Nov 2026. Links not described as found in search are from memory, so confirm they open.

A BMS keeps a lithium pack safe and tells the robot how much energy is left. Its building blocks are cut-off MOSFETs, a fuel gauge, a cell voltage monitor, cell balancing, temperature monitoring, a real-time clock and a state machine. Learn the blocks first, then read a real open design.

### Where to learn how the circuit works
The Renesas [Battery Management System Tutorial](https://renesas.com/en/document/whp/battery-management-system-tutorial) white paper walks through each building block, including how comparators watch for short circuits and drive the FET drivers directly to reduce latency. The All About Circuits [Introduction to Battery Management Systems](https://www.allaboutcircuits.com/technical-articles/introduction-to-battery-management-systems/) covers the cell monitor, balancing (including simple balancers that work without a microcontroller) and short-circuit protection. Monolithic Power's [How to Design a BMS](https://www.monolithicpower.com/how-to-design-a-battery-management-system-bms) explains the common three-chip structure of an analog front end, a microcontroller and a fuel gauge. For a hands-on view, CircuitDigest [reverse-engineered a cheap 4S 40A BMS module](https://circuitdigest.com/comment/35780) and found one IC (DW01-A) handling overvoltage, overcurrent and short-circuit protection while another handled balancing. Remember the two balancing styles: passive balancing burns excess charge in bypass resistors, while active balancing moves charge between cells.

### Open BMS designs to study and build
[LibreSolar/bms-c1](https://github.com/LibreSolar/bms-c1) is a 16-cell, 100 A BMS built around the TI bq76952, with schematic, bill of materials and user manual, at about 217 stars and a CERN open hardware licence. Its firmware is in [LibreSolar/BMS_Software](https://github.com/LibreSolar/BMS_Software), built on the Zephyr RTOS. [LibreSolar/BMS-5s](https://github.com/LibreSolar/BMS-5s) is a smaller 3 to 5 cell design based on the bq76920 and is a gentler first read. [stuartpittaway/diyBMSv4](https://github.com/stuartpittaway/diyBMSv4) is the popular DIY powerwall BMS, and [messimu/OpenBMS](https://github.com/messimu/OpenBMS) is a scalable open BMS for up to 96 cells without a second master board. [DieBieEngineering/DieBieMS](https://github.com/DieBieEngineering/DieBieMS) is an electric-skateboard BMS with Altium hardware files, which is closer to a robot's high-current needs. [libreUPS/bms](https://github.com/libreUPS/bms) is a work-in-progress 15-cell design using a bq769x0-family chip, an STM32 and CAN. [syssi/esphome-jk-bms](https://github.com/syssi/esphome-jk-bms) (about 1k stars) monitors and controls a commercial JK BMS over UART or Bluetooth, and [mnh-jansson/open-battery-information](https://github.com/mnh-jansson/open-battery-information) (about 1.8k) reads data from battery packs.

### What to be able to do
Explain what each BMS block does, size the cut-off MOSFETs and shunt for your robot's peak current, and decide between passive and active balancing. Always test a BMS on a bench supply and a fused, current-limited setup before connecting real cells.

## Added: PWM, motor drive circuits and control

### Where to learn
The All About Circuits article on [H-bridge DC motor control with complementary PWM, shoot-through and dead time](https://www.allaboutcircuits.com/technical-articles/h-bridge-dc-motor-control-complementary-pulse-width-modulation-pwm-shoot-through-dead-time-pwm/) is the clearest starting point. It explains that duty cycle sets average power and that turning on both MOSFETs of one side together causes a shoot-through short circuit, which dead time prevents. A patent text on half-bridge drivers adds a useful tradeoff: too little dead time risks shoot-through, while too much wastes power in the body diodes. Digi-Key has two breadboard guides, [an Arduino H-bridge with bootstrapped high-side drivers](https://forum.digikey.com/t/breadboard-an-arduino-based-h-bridge-motor-controller/45230) and [an Arduino-controlled BLDC driver](https://forum.digikey.com/t/breadboard-an-arduino-controlled-bldc-motor-driver/45637), which uses a three-phase H-bridge and trapezoidal commutation from Hall sensors. The MIT [motors learning map](https://motors.mit.edu/motors) covers PWM and the H-bridge, current (torque) control of a brushed motor, drive control bandwidth, and designing your own controller including FET selection, current sensing, protection and regenerative braking. The Obuda University [H-bridge and motor control notes](https://www.aut.uni-obuda.hu/es/Embedded%20Systems/Reference/05-motors/motor-basics) explain that torque follows current while speed depends on voltage and load.

### The control layers to learn in order
First, open-loop PWM speed control. Second, a current loop, because current is torque and a fast current controller protects the motor and driver. Third, a velocity loop around it, then a position loop around that, which is the cascaded structure used in almost every robot joint. For brushless motors, the next step is field-oriented control, and the SimpleFOC, ODrive, VESC and moteus projects listed earlier are the best open examples to read.

### What to be able to do
Build a MOSFET H-bridge with proper dead time on a breadboard at low voltage, measure the switching waveforms on an oscilloscope, and close a current loop with a shunt resistor or current sensor. This is where the test bench instruments in [the test bench file](11-test-bench-and-instruments.md) become essential.
