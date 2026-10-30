# Go1 Gesture Tracking

Gesture-guided teleoperation for the DyCo-AI laboratory's Unitree Go1.

The operator's laptop recognizes hand gestures from its webcam, validates the
result, and sends bounded high-level commands to the Go1 through ROS Noetic. The
robot-mounted ZED 2i is a separate camera: its Jetson AGX Xavier camera node
publishes the live robot view used by the operator.

Project website: [https://dyco-ai.github.io/go1_gesture_tracking/](https://dyco-ai.github.io/go1_gesture_tracking/)

## Course website and current hardware path

The course keeps its Go1 name. It supports learning across Go1 and Go2: this
version uses Go1 simulation and Go2 Wi-Fi/WebRTC hardware on Windows 11.
Physical Go1 integration is under development. The ROS/Jetson/ZED scaffolds below
remain legacy references rather than the current student hardware application.

- [Course website](https://dyco-ai.github.io/go1_gesture_tracking/): schedule, concepts, assignment expectations, and submission policy.
- [Student code repository](https://github.com/sriram-2502/go1-mujoco-playground): runnable weekly labs and reports.
- [Current Go2 onboarding](https://github.com/sriram-2502/go1-mujoco-playground/blob/main/course/GO2_HARDWARE.md): clone the [Go2 setup repository](https://github.com/sriram-2502/unitree-go2-setup) and record the instructor-approved Git commit.

Weekly submissions are individual README reports on assigned team branches;
full run data stays local. See [student work and data](docs/student-work.md).

## Legacy Go1 Runtime Architecture

The system is distributed across two computers:

- **Operator laptop:** ROS master, laptop-webcam gesture recognition, gesture
  validation, command mapping, operator video display, and Unitree high-level
  bridge.
- **Go1 Jetson AGX Xavier:** ZED 2i camera node publishing `/video`,
  `/camera_pose`, and `/detections` to the laptop's ROS master.

The validated Jetson/ZED configuration is maintained separately in
[`go1_density_social_nav`](https://github.com/sriram-2502/go1_density_social_nav).
This repository does not duplicate that hardware stack.

## Repository Layout

```text
gesture_recognition/   ROS Noetic Python package for laptop-webcam gestures
gesture_control/       ROS Noetic C++ package for validation and Go1 commands
docs/                  Jekyll project website and system documentation
.github/workflows/     Website deployment and future code checks
```

## Development Workspace

Clone this multi-package repository directly into a catkin workspace:

```bash
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws/src
git clone git@github.com:DyCo-AI/go1_gesture_tracking.git

cd ~/catkin_ws
rosdep install --from-paths src --ignore-src -r -y
catkin build
source devel/setup.bash
```

The packages are intentionally scaffolds at this stage. Runtime nodes and launch
files will be added as the gesture and command interfaces are implemented and
validated against the laboratory hardware.

## Existing Runtime Dependencies

- ROS Noetic and Python 3
- MediaPipe, OpenCV, and TensorFlow Lite for laptop gesture recognition
- `unitree_legged_msgs` and the laboratory's `unitree_ros_to_real` workspace
- Existing Jetson AGX Xavier/ZED 2i camera stack

See [DEPENDENCIES.md](DEPENDENCIES.md) before attempting hardware operation.
