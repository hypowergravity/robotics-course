# Tools and Software Catalogue

No single program is the right answer for every student, so this file lists several options in each category, with a short note on cost and on what each one is best for. The choice usually comes down to three questions: is it free, does it run in a browser or on your machine, and can an agent drive it from a script. Tools with a scripting interface or a text file format are much easier to use with the agents from file 24, so those are marked.

Everything here comes from general knowledge and from the course map rather than from fresh verification, except where marked "(search-confirmed)". Prices, licences and free tiers change often, so check the vendor page before you commit. Open-source and free tools are listed first within each category because they let every student start without a licence.

## Circuit simulators

For learning, start in a browser. Falstad Circuit Simulator shows current moving through a circuit and is the best first tool for building intuition, and it is free. Tinkercad Circuits from Autodesk is free, runs in the browser and simulates an Arduino alongside simple parts, so it suits absolute beginners. Wokwi is a browser simulator for ESP32, Arduino, Raspberry Pi Pico and others, and it is excellent for firmware without any hardware; it has a free tier and paid plans. CircuitSim is a free browser tool focused on digital logic. EveryCircuit and CircuitLab are browser tools that are friendly but limit what you can do without paying. Cirkit Designer combines schematic, breadboard and code in one browser tool, with free and paid levels.

For serious analog work, move to a SPICE engine. LTspice from Analog Devices is free for Windows and Mac and is widely used for power supplies and amplifiers. ngspice is open source, runs from a command line, and is the one that agents can drive easily because it reads plain text netlists. Qucs-S is an open-source graphical front end that can use ngspice and other engines, and [ra3xdh/qucs_s](https://github.com/ra3xdh/qucs_s) exists on GitHub. TINA-TI from Texas Instruments is free and ships with their component models. PSpice from Cadence has a free version bundled with some tools. Proteus from Labcenter and NI Multisim are commercial, popular in universities, and good at simulating a microcontroller together with its circuit. SimulIDE is a free simulator aimed at microcontroller projects.

A practical rule: learn the idea in Falstad, test firmware in Wokwi, and do real analysis in ngspice or LTspice. For battery packs and motor drives, make sure the simulator can handle switching converters, which LTspice and ngspice do well.

## PCB and electronics design (EDA)

KiCad is the open-source standard and is free, with a text-based file format and a Python scripting interface, so it works well with the KiCad MCP servers in file 24. Other free options are LibrePCB, which is simpler and very beginner-friendly, and Horizon EDA. EasyEDA together with the JLCPCB and LCSC ecosystem is free, browser-based and convenient for cheap fabrication and part sourcing. Autodesk Fusion Electronics, formerly Eagle, is free for personal use with limits. Altium Designer and OrCAD/Allegro are professional commercial tools that you will meet in industry. Flux.ai is a browser tool with built-in AI assistance. Beginners should pick KiCad and stay with it.

## Mechanical CAD

FreeCAD is free and open source, fully scriptable in Python, and the base for several of the MCP servers in file 24. CadQuery is a Python library for parametric CAD and the best target for text-to-CAD because a model can write it. OpenSCAD is another code-first tool with its own small language, and it is excellent for simple parametric parts. Onshape is a full professional CAD that runs in the browser and has a free plan for non-commercial work, though your designs are public on that plan. Autodesk Fusion has a free personal-use licence with restrictions. SolidWorks, Inventor, Siemens NX and Creo are commercial industry tools. Blender is for meshes, rendering and visuals rather than precise mechanical design. For beginners wanting to print parts, Fusion or Onshape is quickest, while those wanting automation should learn CadQuery.

## Slicing, simulation of parts and photogrammetry

For 3D printing, PrusaSlicer, OrcaSlicer and Ultimaker Cura are free slicers. For stress analysis, FreeCAD's FEM workbench with CalculiX is free, and Fusion and Onshape include simulation in some plans. For photogrammetry, Meshroom (AliceVision) and COLMAP are free and open source, while RealityCapture and Metashape are commercial. CloudCompare and MeshLab are free tools for inspecting and cleaning point clouds and meshes.

## Control, modelling and maths software

Python with NumPy, SciPy and Matplotlib is the default for this course, together with python-control for control design. GNU Octave is a free MATLAB-compatible environment, and Scilab with Xcos is a free block-diagram alternative to Simulink. OpenModelica is a free environment for physical system modelling, and [OpenModelica/OpenModelica](https://github.com/OpenModelica/OpenModelica) is its repository. MATLAB and Simulink are the commercial standard in industry and in many universities, and students often get a campus licence. Julia is worth knowing for fast numerical work. Wolfram Alpha and SymPy help check algebra and calculus.

## Robot simulators and learning frameworks

MuJoCo is free and open source and is the fastest way to start with contact physics. Gazebo is the standard simulator for ROS 2. NVIDIA Isaac Sim and Isaac Lab are powerful GPU-based simulators and need an NVIDIA GPU. PyBullet is older but easy to start with, Webots is free and beginner-friendly, and Genesis and ManiSkill are newer GPU-accelerated options. Drake is excellent for control and planning research. Choose MuJoCo for learning physics, Gazebo for ROS work, and Isaac Lab for large-scale reinforcement learning.

## Firmware, IDEs and embedded tools

PlatformIO is a free multi-board build system that works inside VS Code and is easy for agents to drive. The Arduino IDE is the friendliest start. STM32CubeIDE, ESP-IDF, the Raspberry Pi Pico SDK and Zephyr's west tool are the vendor and RTOS toolchains. For debugging, OpenOCD with a hardware probe such as ST-Link, J-Link or a CMSIS-DAP device is the open route, covered in file 22. For logic and protocol analysis, PulseView and sigrok are free, and Saleae Logic is a polished commercial option.

## Robotics middleware, data and ML tools

ROS 2 with RViz and rosbag is the standard middleware, and Foxglove, Rerun and PlotJuggler are visualisation tools for logs and live data. For machine learning, PyTorch is the main framework, with LeRobot and the Hugging Face tools for robot datasets and policies. Weights & Biases and TensorBoard track experiments. Docker and devcontainers keep tool versions repeatable, which matters when many different tools must work together.

## AI assistants and coding agents

Alongside the frameworks in file 24, students will use coding assistants such as Claude Code, GitHub Copilot, Cursor and Aider to write scripts, firmware and ROS nodes. They differ in price and in how much of your machine they can touch, so read what each is allowed to run, and use version control so you can undo what an agent changed.

## How to choose

Pick tools by what the stage needs and what your budget is. A student with no budget can complete the whole course with free tools: Falstad, Wokwi, ngspice or LTspice, KiCad, FreeCAD or CadQuery, Python, MuJoCo, ROS 2 and PlatformIO. Add commercial tools only when a specific stage or employer requires them. Prefer tools with text file formats and scripting, because they are the ones that agents and version control work with most easily.

## Checkpoint

You are ready to move on when you can name at least two tools for each category above, say which of them are free and which are scriptable, and explain why you chose the one you use for your current project.
