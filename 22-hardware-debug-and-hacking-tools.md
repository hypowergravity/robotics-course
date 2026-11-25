# Stage 22: Hardware Debug and Hacking Tools for Robotics

This file compares three tools you asked about, the ChipWhisperer-Husky, the Bus Pirate 6 and the Tigard, and says how useful each is for robotics work. In short, the Bus Pirate and Tigard are everyday bench tools for anyone building robot electronics, while the ChipWhisperer is a specialist security instrument. Use all of them only on hardware you own or have permission to test. Items marked "search-confirmed" were found on 25 Nov 2026, and prices change, so check current listings.

## Tigard

Tigard is an open-source board built around the FT2232H chip, with a primary port dedicated to UART including flow control and a secondary port shared among headers for SWD, JTAG, SPI and I2C. It has directional level shifters for 1.8 to 5.5 V and switchable target voltage, a mode switch between SPI/JTAG and I2C/SWD, a logic analyser port and indicator lights (search-confirmed). Its crowdfunding page lists $49 for the board with wiring harnesses, and its use cases include dumping a SPI flash chip and using GDB over JTAG (search-confirmed). The design files are in KiCad and software support includes LibMPSSE and PyFtdi.

For robotics it is the most useful of the three for firmware work. It gives you a serial console on a Linux single-board computer, a SWD or JTAG link to flash and debug a motor-driver microcontroller, and a way to read or write an SPI flash chip. Start with Tigard if you can only buy one.

## Bus Pirate 6

The Bus Pirate talks I2C, SPI, UART and 1-Wire from simple commands, without writing code, and reads and writes flash memory and EEPROMs. It also helps discover JTAG and SWD debug ports and sniff I2C (search-confirmed). The version 6 uses an RP2350B microcontroller and adds a follow-along logic analyser on eight pins that shows protocol activity in real time in Sigrok and PulseView, 8 buffered IO pins from 1.2 to 5 V, and an adjustable power supply with current measurement and limiting on the 5XL and 6 (search-confirmed). A 2024 listing showed the Bus Pirate 6 at $82.50 and the 5XL at $63.50.

For robotics it is excellent for bringing up a new sensor. You can poke an IMU, encoder chip or flash over I2C or SPI interactively, see the waveform at the same time, and confirm addresses and registers before writing driver code. The documentation I found does not list CAN, so use a dedicated CAN adapter for that bus. A Bus Pirate is slower and less capable for debugging a running microcontroller than a proper SWD probe such as the Tigard.

## ChipWhisperer-Husky

The Husky is a compact tool for side-channel power analysis and fault injection. It has a high-speed logic analyser, voltage glitching with high-power and low-power crowbar options, clock glitching, a 12-bit ADC sampling at 200 MS/s versus the Lite's 10 bits at 105 MS/s, and an integrated Arm trace sniffer called TraceWhisperer (search-confirmed). The FPGA logic, microcontroller firmware and computer code are open source, and the manufacturer's page lists it at US$630, with a higher-end HuskyPlus offered at about €1,195 by one reseller (search-confirmed). Learning material includes the ChipWhisperer Jupyter notebook labs and the book The Hardware Hacking Handbook.

For robotics it is not an everyday tool. It matters if you design robots that others will use and want to test whether your motor controller or secure bootloader resists glitching and power analysis, or if you need to recover access to a locked controller you own. It also doubles as a precise power-trace instrument, which can be educational for understanding what code does to current draw. Skip it until you have worked through file 21.

## Which to buy first

Buy a Tigard first for debugging and flashing, add a Bus Pirate 6 when you start working with many I2C and SPI sensors, and buy a Husky only if security testing becomes part of your work. A cheap logic analyser compatible with sigrok from file 11 complements all three. For CAN, add a USB-CAN adapter supported by SocketCAN, and for robot buses beyond that see file 13.

## Practice projects

Use a Tigard to open a serial console on a Raspberry Pi and flash a microcontroller over SWD. Read the ID register of an IMU with a Bus Pirate while watching the waveform in PulseView. If you buy a Husky, work through the first ChipWhisperer lab on simple power analysis against its included target board, and then write down which of the weaknesses in file 21 your own controller would share.
