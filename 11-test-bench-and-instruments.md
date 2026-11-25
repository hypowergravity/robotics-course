# Test Bench and Instruments

Building a robot without measuring it means guessing. This file covers the instruments you need to characterise motors, drivers, batteries and sensors, and the open projects that let you build or script your own. Read it alongside Stage 2 (electronics) and Stage 3 (mechanics).

Star counts are approximate figures from public aggregator pages on 25 Nov 2026. Links I did not see in search results are marked as from memory, so confirm they open.

## The core instruments and what each tells you

A digital multimeter confirms voltages and continuity and is the first thing you reach for. A programmable bench power supply with current limiting protects your circuit while you debug, and lets you log the current a motor draws. A source measure unit (SMU) goes further: it works like a power supply that can source current into a load and also sink current like an electronic load, measuring as it goes. An oscilloscope shows switching waveforms, which is how you check PWM dead time and ringing. A logic analyzer decodes buses such as CAN, SPI and I2C. For torque you need a torque sensor, load cell or dynamometer, together with a speed sensor such as an encoder or a tachometer. A thermal camera or thermocouple tells you whether a motor or MOSFET is running too hot.

## Measuring torque: motor dynamometers and load cells

### MC-Dyno
[MC-Dyno](https://impressivetaste.github.io/Dyno-MCHP-Repository-WIP/docs/_build/html/index.html) is an open hardware and software project for building a motor dynamometer to test and tune motor-control algorithms. It supports high-voltage and low-voltage setups and can test almost any electric motor. One design uses a differential coupling for cheap torque measurement, and its documentation notes that a dedicated torque sensor is not required for basic characterisation. You can observe torque, speed, power, efficiency and thermal behaviour while applying a controllable mechanical load.

### MIT motor testing data
The MIT Center for Bits and Atoms [motor-testing-data repository](https://gitlab.cba.mit.edu/davepreiss/motor-testing-data) documents a stall-condition test rig where the motor's torque passes through a frame and is constrained by a load cell, reported as sensitive down to grams times millimetres. It compares hobby servos, steppers and brushless motors, with and without reduction, which is the exact decision you face when choosing a joint motor.

### Low-cost dynamometer articles
Electronic Design's two-part [Simple, Low-Cost Dynamometer Setup for Motor Testing](https://www.electronicdesign.com/power-management/whitepaper/21130416/simple-lowcost-dynamometer-setup-for-motor-testing-part-2) describes a student-built dynamometer with open-source files that produces torque profiles such as ramps and square waves. The Cornell ECE 4760 [motor dynamometer project](https://people.ece.cornell.edu/land/courses/ece4760/FinalProjects/f2017/apg67_kss223_ejy25/kss223_apg67_ejy25/kss223_apg67_ejy25/index.html) is a friction-brake design using a Hall-effect current sensor, strain gauges for torque and an infrared speed sensor, tested on a brushed 540 motor. Circuit Cellar's [Build a Motor Dynamometer](https://circuitcellar.com/research-design-hub/projects/build-a-motor-dynamometer/) teaches Wheatstone bridge circuitry for strain gauges. A Hackaday project shows a homemade dynamic torque transducer with an absorber motor that dissipates the test motor's energy.

### The basic dyno idea
Mount the motor under test and a second motor (the absorber) on opposite sides of a torque sensor, joined by couplers. The absorber loads the test motor while you sweep current and speed and record torque, current and RPM. From those you compute the torque constant, efficiency and the continuous and peak torque limits your robot joint can rely on.

## Source measure units and programmable supplies

### EEZ Bench Box 3 and EEZ Studio
[eez-open/modular-psu](https://github.com/eez-open/modular-psu) is the EEZ Bench Box 3, a modular open-source test and measurement chassis, listed at about 333 stars. [eez-open/studio](https://github.com/eez-open/studio) is a cross-platform low-code tool and SCPI controller for instruments, at about 986 stars. [eez-open/psu-hw](https://github.com/eez-open/psu-hw) is the earlier fully open EEZ H24005 programmable power supply, at about 454 stars, whose crowdfunding campaign was 280 percent funded.

### Open source measure units
[jaromir-sukuba/J-SMU](https://github.com/jaromir-sukuba/J-SMU) is an open implementation of an SMU inspired by the Keithley 236, listed at about 173 stars, with KiCad files and PDF schematics. [knarfS/smuview](https://github.com/knarfS/smuview) is a Qt-based source-measurement GUI for sigrok that supports power supplies, multimeters, oscilloscopes and logic analyzers. The Analog Devices ADALM1000 learning kit combines an SMU, an oscilloscope and a function generator with open-source hardware and software, at roughly seventy dollars when one reviewer wrote about it, so check the current price.

### Scripting any instrument
PyVISA and PyVISA-py ([pyvisa/pyvisa](https://github.com/pyvisa/pyvisa) and [pyvisa/pyvisa-py](https://github.com/pyvisa/pyvisa-py)) let Python control instruments over SCPI. One engineering-education paper used them to control a Keysight power supply and multimeter for I-V characterisation. [sigrok](https://sigrok.org/) is an open suite for logic analyzers, oscilloscopes and multimeters, and its PulseView front end is a good place to start. A tiny example pattern is a Python class that wraps a power supply and exposes set_voltage, set_current, measure_voltage and measure_current, then logs the results to a file while a test script sweeps the motor.

## A sensible starter bench

For under a few hundred dollars you can assemble a useful bench: a multimeter, a current-limited bench power supply, a basic oscilloscope or USB scope, a cheap logic analyzer that works with sigrok, a strain-gauge load cell with an amplifier board, and an encoder or optical tachometer. Add a differential coupling or a second absorber motor when you are ready to build a dynamometer. Add a thermal camera later.

## Safety on the bench

Fuse every battery, current-limit your supply, use a resistive load before a real motor, and never connect a scope ground clip to a switching node without checking what it is referenced to. Test BMS and battery circuits with a bench supply first, and keep cells in fire-safe storage while charging.

## What to be able to do

You should be able to measure a motor's no-load and stall current, plot torque versus current to get the torque constant, view PWM switching and dead time on a scope, and script a sweep that records voltage, current, speed and torque into a file.
