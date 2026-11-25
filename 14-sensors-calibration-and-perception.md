# Stage 14: Sensors, Calibration and Perception

State estimation (file 05) assumes your sensors work and are calibrated. This stage fills that gap: how the common sensors behave, how to calibrate them, and how a robot turns images and depth into things it can grasp. Links marked "search-confirmed" were found on 25 Nov 2026, and the others are from memory, so verify before use.

## Sensors you should understand

An IMU gives angular rate and acceleration at high rate but drifts, so it needs bias estimation. Encoders give joint position, and you should learn the difference between incremental and absolute types and what quantisation does to a velocity estimate. Cameras give rich data but need intrinsic calibration and accurate timing. Lidar and depth cameras give geometry. Force-torque and tactile sensors give contact information, and motor current can serve as a cheap torque estimate. For each sensor, learn its noise, its rate, its latency and its failure mode, because those four facts decide how you fuse it.

## Camera and multi-sensor calibration

### [ethz-asl/kalibr](https://github.com/ethz-asl/kalibr)
The standard toolbox for multi-camera calibration, camera-IMU spatial and temporal calibration, IMU intrinsics and rolling-shutter cameras, with Docker or ROS workspace installation. A camera-IMU run uses a target such as an AprilGrid and a recorded bag, and temporal calibration is on by default (search-confirmed). It appears in several awesome robotics lists.

### [PJLab-ADG/SensorsCalibration (OpenCalib)](https://github.com/PJLab-ADG/SensorsCalibration)
A toolbox covering camera, lidar, IMU and radar calibration, with target-based methods using chessboard, ArUco, AprilTag and round-hole boards, aimed at autonomous driving but usable for robots (search-confirmed).

### [unmannedlab/imu_lidar_calibration](https://github.com/unmannedlab/imu_lidar_calibration)
Target-free extrinsic calibration between a 3D lidar and an IMU, which is useful when you cannot build a calibration rig. The README says it was tested with IMU rates from 50 to 400 Hz (search-confirmed).

### [Unsigned-Long/iKalibr](https://github.com/Unsigned-Long/iKalibr)
A targetless spatiotemporal calibration method for IMU, radar, lidar and camera systems based on continuous-time batch optimisation (search-confirmed).

### OpenCV calibration
The camera calibration tutorials in [opencv/opencv](https://github.com/opencv/opencv) are where most people first calibrate a lens, and they are a good first exercise before Kalibr (from memory).

## Detection, segmentation and pose

### [facebookresearch/segment-anything](https://github.com/facebookresearch/segment-anything)
Segment Anything is a promptable model that produces masks for arbitrary objects, and robotics pipelines often pair it with a vision-language model that names the object to find. A grasping thesis and a humanoid grasping paper in the search both chain it with other tools (search-confirmed that it is used this way; the link is from memory).

### [ultralytics/ultralytics](https://github.com/ultralytics/ultralytics)
YOLO detection and segmentation models, practical for real-time detection on small hardware. It also appears in file 09.

### FoundationPose
A recent humanoid grasping pipeline chains YOLOv8 training, SAM 3D reconstruction and FoundationPose tracking to perceive objects in real time on a Unitree G1 (search-confirmed). Search for the FoundationPose repository by name from NVIDIA when you reach this step.

## Point clouds and 3D

Learn [Open3D](https://github.com/isl-org/Open3D) for point cloud processing and registration, and [PCL](https://github.com/PointCloudLibrary/pcl) if you work in C++ (both from memory). Depth models in file 10 give you dense depth from a single camera when you have no depth sensor.

## Grasp planning

Grasp detection predicts where and how to close a gripper from a depth image or point cloud. Contact-GraspNet predicts 6-DoF grasps from depth plus an instance mask or from a point cloud, and a robotics harness paper exposes it that way next to M2T2 (search-confirmed). Other well-known grasp tools include GPD and Dex-Net, which one dataset paper describes as pioneering deep 6-DoF grasping and large-scale planar grasp learning respectively (search-confirmed). GraspNet-1Billion is a common benchmark, though a newer paper argues it is too simple and offers a cluttered-scene dataset called GraspClutter6D (search-confirmed). An open-source ecosystem called COMPARE aims to make manipulation software easier to combine and benchmark (search-confirmed).

## Practice projects

Calibrate a webcam with OpenCV and measure reprojection error. Record a bag with an IMU and camera and run Kalibr to find the camera-IMU transform and time offset. Segment an object with Segment Anything, back-project its mask into a depth cloud, and compute a simple top-down grasp pose. Then try Contact-GraspNet on the same cloud and compare the two.
