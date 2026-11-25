# Stage 15: Actuator and Gearbox Design

File 02 taught you to drive a motor and file 03 taught you to design parts. This stage joins them: choosing a motor and a gearbox, and building a joint that is strong, backdrivable and controllable. Items marked "search-confirmed" were found on 25 Nov 2026, and the rest come from memory.

## The core idea: quasi-direct drive

A quasi-direct-drive (QDD) actuator pairs a large, torque-dense brushless motor with a low reduction, typically somewhere between 3:1 and 10:1. The goal is an actuator that is robust, highly backdrivable and able to sense force through its own motor current, which makes impedance control possible (search-confirmed from the OpenTorque and cycloidal QDD pages). This is the philosophy behind the MIT Mini Cheetah actuator and most modern legged robots.

## Gearbox types and their trade-offs

Planetary gearboxes are compact and common. Cycloidal drives give high torque density, low backlash and resistance to shock loads, which is why a recent legged-robot paper favours them over planetary designs for dynamic tasks (search-confirmed). Harmonic drives give very high ratios and almost no backlash but are less backdrivable, and a thesis comparison chart in the search places them far above 30:1, while capstan and spur arrangements suit lower ratios. Learn the trade between ratio, backlash, efficiency, backdrivability and cost before choosing.

## Open-source actuators you can build

### [G-Levine/OpenTorque-Actuator](https://github.com/G-Levine/OpenTorque-Actuator)
An open implementation of the MIT-style QDD scheme with 3D-printable parts. The project page says the latest version weighs 1150 g and gives 80 N·m peak torque (search-confirmed).

### [bbokser/sprydrive](https://github.com/bbokser/sprydrive)
An affordable QDD actuator made from a brushless outrunner motor, a low-cost metal gearbox and a 3D-printed housing, with a build guide (search-confirmed). A Hackaday log reports about 0.13 degrees of output backlash.

### OpenQDD and OpenCycloid
OpenCycloid is a 3D-printed cycloidal actuator, and its author says it grew out of building Aaed Musa's OpenQDD design and using his parametric two-disk cycloidal generator for Fusion 360 (search-confirmed on Instructables).

### Open-source 3D-printed QDD research designs
A 2022 paper presents two open QDD actuators built from off-the-shelf and 3D-printed parts for under 200 USD each, sized for 8 to 15 kg robots (search-confirmed). A Hackster article describes a 3D-printable QDD actuator that costs as little as 40 USD and reaches nearly 30 N·m of holding torque, using a planetary gearbox generated with the open-source pygeartrain tool (search-confirmed).

### KRC-Actuator
A maker built twelve actuators for a robot dog, each with a 9:1 3D-printed cycloidal gearbox and a custom FOC driver board, and released CAD, PCB, firmware and host tools under the MIT licence (search-confirmed). It is a complete reference of mechanics, electronics and firmware together.

### Berkeley Humanoid Lite
An open-source, 3D-printed humanoid whose core is a modular 3D-printed gearbox (search-confirmed). See also file 09 for humanoid projects.

## Tools for designing your own

Use the CAD-as-code tools from file 03 to parameterise gear designs, [pygeartrain](https://github.com/EelcoHoogendoorn/pygeartrain) for planetary layouts (owner confirmed by a repository check on 25 Nov 2026), and motor-sizing calculators from your motor vendor. Pair the mechanical work with the dynamometer approach in file 11 to measure what you built.

## Selection and thermal limits

Choose a motor by its torque constant, winding resistance and thermal limits, then size the gear ratio so the peak load sits near the motor's efficient region. Continuous torque is limited by heat, not by the peak figure, so measure winding temperature during tests. Quantisation, cogging and friction set your torque resolution at low speed.

## Practice projects

Size a QDD joint for a 0.3 m link carrying 1 kg at its end, listing motor, ratio, peak and continuous torque. Print and assemble SpryDrive or OpenCycloid, then measure backlash with a dial indicator. Run the joint on your FOC driver, estimate torque from current, and compare it with a load cell reading from your test bench.
