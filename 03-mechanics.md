# Stage 3: Mechanics

**Start here:** [Gears, by Bartosz Ciechanowski](https://ciechanow.ski/gears/)

Motors are fast and weak, while robot joints need to be slow and strong. Gears, linkages and good structural design close that gap. The best way to learn mechanics is to design a part, print it and see where it breaks, so the repositories below are mostly the design and fabrication tools.

## CAD and design tools

### [FreeCAD/FreeCAD](https://github.com/FreeCAD/FreeCAD)
A full parametric 3D modeller. Parametric means you change a dimension and the whole part updates, which is exactly what you want while iterating on a robot arm link.

### [openscad/openscad](https://github.com/openscad/openscad)
A modeller where you describe parts with code. It suits gears and brackets, because a gear is just a few parameters.

### [openscad/MCAD](https://github.com/openscad/MCAD)
A library of mechanical parts for OpenSCAD, including gears, bearings and motor mounts. A quick way to produce your first working gear train.

### [CadQuery/cadquery](https://github.com/CadQuery/cadquery)
A Python library for building precise 3D models in code. It is useful when you want to generate whole families of parts from a script.

### [gumyr/build123d](https://github.com/gumyr/build123d)
A modern Python CAD library in the same spirit as CadQuery, with a clean and readable style.

### [solvespace/solvespace](https://github.com/solvespace/solvespace)
A small parametric CAD tool with a strong constraint solver. Its sketch-and-constrain workflow helps you think about linkages.

## Fabrication

### [prusa3d/PrusaSlicer](https://github.com/prusa3d/PrusaSlicer)
Slicer software that turns a 3D model into printer instructions. Learn how wall count, infill and orientation change the strength of a part.

### [Klipper3d/klipper](https://github.com/Klipper3d/klipper)
3D printer firmware that is also a clear example of a real-time motion planner, with acceleration limits and kinematics for different machine types.

## What to learn alongside the code

Study gear ratio and its trade of speed for torque, backlash and why it hurts accuracy, torque at a joint as force times arm length, and the difference between direct drive, geared and cable-driven joints. A useful exercise is to compute the gear ratio needed for a small motor to hold a 1 kg weight on a 10 cm arm, then design the gears, print them and test your numbers.

## What to be able to do before moving on

You should be able to design a two-link arm in CAD, choose a motor and gear ratio from a torque calculation, and print and assemble it. See [the hardware file](09-open-hardware-robots.md) for complete open robot designs to study and copy.

## Trending and most-starred additions (checked 25 Nov 2026)

Star counts below are approximate figures reported by public aggregator pages on 25 Nov 2026, so treat them as a rough guide to popularity, not exact numbers. Entries without a count had no figure in the pages I could reach. Links not marked as checked are from memory, so confirm they open.

### Most popular tools
[FreeCAD/FreeCAD](https://github.com/FreeCAD/FreeCAD) is by far the most-starred open CAD project, at about 35k stars. [gumyr/build123d](https://github.com/gumyr/build123d) has grown to about 3.6k stars and is the leading code-first CAD library after CadQuery.

### Libraries and parts
[CadQuery/cadquery-contrib](https://github.com/CadQuery/cadquery-contrib) collects shared CadQuery scripts and projects, and [CadQuery/awesome-cadquery](https://github.com/CadQuery/awesome-cadquery) lists viewers, CAM add-ons and other tools. [gumyr/cq_warehouse](https://github.com/gumyr/cq_warehouse) is a parametric part collection for CadQuery. [earthtojake/step.parts](https://github.com/earthtojake/step.parts) offers more than 12,000 open STEP parts you can drop into a design, and [chrisspen/gears](https://github.com/chrisspen/gears) is an OpenSCAD gear generator, which suits this stage's gear lesson directly. [DavidMStraub/cad-as-code-book](https://github.com/DavidMStraub/cad-as-code-book) is an open textbook on code-first CAD, and [mlightcad/awesome-cad](https://github.com/mlightcad/awesome-cad) lists open CAD software by category.

### The current trend: text-to-CAD
Several new tools generate parametric models from a written description, for example a build123d-based text-to-CAD app called cad-studio, an MCP server for build123d, and an AI assistant workbench for FreeCAD. These are young projects with small star counts, so treat them as experiments rather than dependable tools, and check any generated part against your own torque and size calculations.

## Added: Photogrammetry and reverse engineering

Star counts are approximate figures from public aggregator pages on 25 Nov 2026.

Photogrammetry recovers 3D shape from ordinary photographs. For a robot builder it is useful in three ways: scanning an existing part so you can redesign it in CAD, capturing a workspace or object for simulation, and recovering camera poses for learning pipelines such as the UMI and egocentric data in the advanced file.

### [alicevision/Meshroom](https://github.com/alicevision/Meshroom)
An open-source 3D reconstruction application built on the AliceVision framework, with a node-based interface. It is the most-starred open photogrammetry application I found, at about 11.8k stars, and the easiest place to start.

### [alicevision/AliceVision](https://github.com/alicevision/AliceVision)
The photogrammetric computer vision framework underneath Meshroom, covering structure from motion, multi-view stereo and surface reconstruction, at about 2.8k stars.

### [colmap/colmap](https://github.com/colmap/colmap)
The standard structure-from-motion and multi-view stereo tool under a permissive BSD licence, at about 8.6k stars in an earlier snapshot. It is the usual way to get accurate camera poses for research code.

### MicMac, OpenSfM and WebODM
MicMac is a mature photogrammetry package from the French mapping agency IGN, and a 2026 paper introduces MicMacRoom, which joins MicMac's workflow to Meshroom's node interface. OpenSfM ([mapillary/OpenSfM](https://github.com/mapillary/OpenSfM)) is a Python structure-from-motion library, and [OpenDroneMap/WebODM](https://github.com/OpenDroneMap/WebODM) processes aerial imagery from drones.

### [nerfstudio-project/nerfstudio](https://github.com/nerfstudio-project/nerfstudio)
A friendly framework for NeRFs and Gaussian splatting. These produce views and, increasingly, usable geometry from photos, though a mesh from classic photogrammetry is still easier to import into CAD.

### From scan to CAD
Scan the part with a phone or camera from many angles, reconstruct it in Meshroom, clean and scale the mesh, then use it as a reference in FreeCAD, or measure it and rebuild it as a parametric model with CadQuery or build123d. Use a scale object or known dimension in your photos, because photogrammetry alone does not know real-world size. For robot parts that must fit exactly, always verify the final dimensions with calipers.
