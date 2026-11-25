# Stage 21: Robot Security, Hardware and Software

A robot is a computer that can move, so a security flaw can become a safety incident. This stage covers embedded hardware security (firmware, debug ports, fault injection) and software and network security (ROS 2, DDS, update channels). Everything here is for securing and testing your own devices and robots, and you should only probe hardware you own or have written permission to test. Items marked "search-confirmed" were found on 25 Nov 2026, and the rest are from memory.

## Embedded hardware security

### The main weaknesses
A survey on safety in embodied AI says that without secure boot and authenticated firmware updates anchored in a hardware root of trust, an attacker with access to firmware storage or the update interface can install malicious firmware that persists (search-confirmed). The same survey describes debug interface abuse: JTAG, UART and SWD are common on boards, and an attacker with physical access can halt the processor and read permitted memory through an unsecured debug port. A bug bounty article lists five attack classes that are accessible to newcomers: side-channel attacks, hardcoded encryption keys, unprotected debug interfaces, missing cryptographic authentication and fault injection (search-confirmed).

### What protections can and cannot do
An NCC Group whitepaper on microcontroller readback protection says all microcontroller data protection can be defeated by invasive methods involving decapsulation, and many can also be broken through non-invasive fault injection such as power or clock glitching (search-confirmed). ST's application note AN5156 explains that debug access gives control of CPU registers, flash, RAM and peripherals, that firmware should limit what the protocol can reach, and that general-purpose microcontrollers usually lack efficient hardware countermeasures against fault injection, with secure elements such as STSAFE as the stronger choice (search-confirmed). A patent on randomised execution during boot lists the usual software defences, redundant checks and comparisons against magic values, and hardware defences such as voltage and frequency monitors (search-confirmed).

### Practical hardening checklist for your own motor controllers
Lock debug access in production units, use a bootloader that verifies signed firmware, keep keys out of source code, authenticate commands on CAN and wireless links, and add a hardware watchdog and an independent emergency stop from file 16 so a compromised controller cannot disable safety. Assume an attacker with physical access can eventually read an ordinary microcontroller, and keep valuable secrets in a secure element.

## Software and network security for ROS 2

ROS 2 uses the DDS-Security standard, and SROS2 is the toolset that makes managing that security infrastructure easier. The standard defines plugins for authentication, access control, cryptography, logging and data tagging, and SROS2 organises credentials into security enclaves (search-confirmed). Authentication uses public key cryptography with digital signatures. The SROS2 paper describes a six-step methodology for securing a ROS 2 graph iteratively, and it argues that without usability, security in robotics will be greatly impaired (search-confirmed).

Security is not automatic. A 2022 ACM CCS paper found three design vulnerabilities in SROS2 that allow unauthorised access to be retained even when security is on, and the official ROS 2 threat model lists exposed debug ports, unsecured DDS domains and firmware update channels as entry points (search-confirmed). A survey of teleoperated quadruped robots covers these threats in one place.

### [aliasrobotics/RVD](https://github.com/aliasrobotics/RVD)
The Robot Vulnerability Database is a community list of robot vulnerabilities and weaknesses, licensed GPL-3.0 and showing 168 stars on one index page, with issues covering DDS chain-of-trust problems in several DDS implementations (search-confirmed). At its 2021 launch the maintainers recorded 236 weaknesses in ROS 2 alone. Reading entries here teaches you what real robot bugs look like.

## Habits for a secure robot

Never expose a robot's DDS domain or web interface to the open internet, and put robots on an isolated network or VPN. Turn on SROS2 for anything beyond a bench demo and keep a written list of which nodes may publish to which topics. Sign and verify firmware updates. Keep Linux packages updated and remove unused services. Log security events and review them. For teleoperation links, authenticate the operator and encrypt the channel, since a hijacked teleoperation session is a direct physical hazard.

## Practice projects

Enable SROS2 on a two-node demo, generate keys and a policy, and confirm that an unauthorised node cannot subscribe. Read ten RVD entries and write down the root cause category of each. Using a development board you own, check whether its debug port is locked, then lock it and confirm that a debugger can no longer read flash. Finally write a one-page threat model for your own robot arm listing entry points, impact and mitigations.
