# Photogrammetry and 3D Scanning

This stage answers a practical question: how does a set of ordinary photos from a camera become a 3D model you can measure, print or load into a simulator? It also lists the scanners, both open-source and commercial, that capture 3D shape directly. For a roboticist this matters because scanned parts become CAD for reverse engineering (files 3, 15 and 24), scanned rooms become simulation worlds (file 17), and the same maths drives the camera calibration and depth work in file 14.

The repositories below were confirmed to exist on 25 November 2026 with a read-only `git ls-remote`. That proves existence, not quality or maintenance. The explanations and the hardware notes come from general knowledge rather than fresh verification, so check prices and specifications with the vendor.

## How photos become a 3D model

The classic pipeline has five steps, and understanding them tells you why photogrammetry sometimes fails. First, feature detection finds distinctive points, such as corners and textured patches, in every photo. Second, feature matching finds the same physical point in different photos. Third, structure from motion uses those matches to work out where each camera was and how it was pointed, and produces a sparse cloud of 3D points. This step is where the camera calibration and the geometry from file 4 appear, because it solves for rotations, translations and lens parameters together, usually with bundle adjustment. Fourth, multi-view stereo uses the known camera positions to estimate depth for almost every pixel, which gives a dense point cloud. Fifth, meshing turns the points into a surface of triangles, and texturing paints the photo colours onto it.

Three practical consequences follow. The object needs texture, so shiny, transparent or plain white surfaces fail unless you spray them with matte powder or add markers. The photos need about sixty to eighty percent overlap and should be sharp and evenly lit. And the result has no real-world scale until you place a ruler or scale bars in the scene, or use markers with known distances.

Newer methods skip parts of this pipeline. Neural radiance fields and Gaussian splatting learn a view-synthesis model from the photos and give beautiful renders, though they are not always accurate geometry. Feed-forward models such as DUSt3R and VGGT predict camera poses and depth directly from a few images. For measurement and CAD, classic photogrammetry is still the safer choice, while for simulation scenery and visualisation the newer methods are very attractive.

## Open-source photogrammetry software

### [alicevision/Meshroom](https://github.com/alicevision/Meshroom) and [alicevision/AliceVision](https://github.com/alicevision/AliceVision)
Meshroom is a graphical program with a node graph of the whole pipeline, built on the AliceVision framework. It is the easiest free start, though the full pipeline expects an NVIDIA GPU for the dense stage.

### [colmap/colmap](https://github.com/colmap/colmap)
COLMAP is the research standard for structure from motion and multi-view stereo, with both a graphical and a command-line interface. Many other tools, including the neural methods below, use COLMAP to get camera poses.

### [openMVG/openMVG](https://github.com/openMVG/openMVG) and [cdcseacave/openMVS](https://github.com/cdcseacave/openMVS)
Two libraries that are often used together: OpenMVG for structure from motion and OpenMVS for dense reconstruction, meshing and texturing. They are good for learning each step separately.

### [OpenDroneMap/ODM](https://github.com/OpenDroneMap/ODM)
Turns drone photos into maps, elevation models and 3D models. Useful if you work with aerial or outdoor robots.

### Neural and feed-forward methods
[graphdeco-inria/gaussian-splatting](https://github.com/graphdeco-inria/gaussian-splatting) is the original 3D Gaussian splatting code, [nerfstudio-project/nerfstudio](https://github.com/nerfstudio-project/nerfstudio) is a friendly framework for neural radiance fields, [NVlabs/instant-ngp](https://github.com/NVlabs/instant-ngp) trains them in seconds on a GPU, and [naver/dust3r](https://github.com/naver/dust3r) and [facebookresearch/vggt](https://github.com/facebookresearch/vggt) predict geometry directly from images. Check each licence, since several research codes limit commercial use.

## Processing and cleaning the result

[CloudCompare/CloudCompare](https://github.com/CloudCompare/CloudCompare) and [cnr-isti-vclab/meshlab](https://github.com/cnr-isti-vclab/meshlab) are the free tools for inspecting, cleaning, aligning, measuring and decimating scans. For scripting, [isl-org/Open3D](https://github.com/isl-org/Open3D) and [mikedh/trimesh](https://github.com/mikedh/trimesh) let you load, filter, register and repair meshes in Python, which is also how an agent from file 24 would automate it. Blender is useful for retopology and texture work. To use a scan as a CAD part, a scan is a mesh, so you usually trace it in FreeCAD or Fusion, or fit simple shapes such as planes and cylinders to it, and then make a clean parametric model.

## Commercial photogrammetry

RealityCapture from Epic Games, Agisoft Metashape and Pix4D are the professional tools. They are faster and more robust than the free ones and are common in surveying and games. Several have free or reduced-price tiers for students or small users, but terms change, so check them. Phone apps such as Polycam, Scaniverse and Luma use photos or the phone's depth sensor and are handy for quick captures.

## Scanners that measure shape directly

Photogrammetry infers shape from images, while scanners measure it. Structured-light scanners project patterns onto an object and photograph them, which gives high accuracy for small parts; examples are the Revopoint, Creality CR-Scan and Shining3D families, and the older open-source Ciclop design. Laser-line and handheld laser scanners, such as those from Creaform and Artec, are used in industry for accuracy and speed. Time-of-flight and stereo depth cameras, such as Intel RealSense ([IntelRealSense/librealsense](https://github.com/IntelRealSense/librealsense)), Azure Kinect successors and the Orbbec cameras, give live depth for robot perception rather than precise parts. Lidar scanners such as 2D units from Slamtec ([Slamtec/rplidar_sdk](https://github.com/Slamtec/rplidar_sdk)) and 3D units from Ouster, Livox and Velodyne map rooms and outdoor spaces, and [introlab/rtabmap](https://github.com/introlab/rtabmap) is a well-known open-source mapping tool that works with RGB-D cameras and lidar. Phones with lidar, such as recent iPhone Pro models, are a cheap way to scan rooms. For a build-it-yourself option, [OpenScan-org/OpenScan3](https://github.com/OpenScan-org/OpenScan3) is an open-source turntable-and-camera photogrammetry scanner you can make with a Raspberry Pi camera.

As a rule of thumb, use photogrammetry for large or textured objects and scenes when you have a camera and time, use structured light for small precise parts, use RGB-D cameras and lidar when a robot needs the geometry live, and use a coordinate measuring tool or calipers whenever you need to check what a scan claims.

## Exercises

First, photograph a textured object on a turntable with at least fifty sharp photos, place a ruler in the scene, process it in Meshroom or COLMAP, and compare a scanned dimension against calipers. Second, repeat with a shiny object and write down what failed and why. Third, open the result in CloudCompare, align it to a CAD model of the same part, and measure the deviation. Fourth, ask an agent to write an Open3D script that scales, cleans and decimates the scan, then check its output by hand. Finally, train a Gaussian splat of a room and import a cleaned mesh into MuJoCo or Gazebo as a scene.

## Checkpoint

You are ready to move on when you can name the five pipeline steps in order, explain why a plain white object fails, say how you would give the result real-world scale, and choose between photogrammetry, structured light and lidar for a given job.
