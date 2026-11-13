---
layout: page
title: System Setup
permalink: /setup/
---

> **Current course implementation:** the course keeps its Go1 name. Students use
> Go1 simulation first, then **Go2 on Windows 11 over Wi-Fi/WebRTC**. Physical Go1
> integration is under development; Go1/ROS/Jetson/ZED descriptions are legacy
> architecture references, not the hardware instructions for this course version.
> Use the [student code and weekly labs](https://github.com/sriram-2502/go1-mujoco-playground)
> and [current Go2 onboarding](https://github.com/sriram-2502/go1-mujoco-playground/blob/main/course/GO2_HARDWARE.md).


## One Go2 setup for the hardware phase

Use **[sriram-2502/go2-gesture-nav](https://github.com/sriram-2502/go2-gesture-nav)**
for Weeks 7 onward. It is a standalone Windows gesture project with **no ROS
workspace and no `webrtc/` wrapper folder**. WebRTC is the built-in robot
connection method, not another installation students need to manage.

Follow the [project quick start](https://github.com/sriram-2502/go2-gesture-nav#1-install-once)
for installation and the [course hardware checklist](https://github.com/sriram-2502/go1-mujoco-playground/blob/main/course/GO2_HARDWARE.md)
for lab expectations. No separate Basic UI repository is needed.

| Step | Where / command from the personal repo root |
| --- | --- |
| Install Python dependencies/model | Anaconda Prompt: `pip install -r requirements.txt`, then `python -m gesture_preview.download_model` in `go2wifi` |
| Install dashboard once | PowerShell: `powershell.exe -NoProfile -ExecutionPolicy Bypass -File .\\setup-ui.ps1` |
| Start hand tracking | Anaconda Prompt: `python -m gesture_preview.server` |
| Start dashboard | PowerShell: `powershell.exe -NoProfile -ExecutionPolicy Bypass -File .\\start-ui.ps1` |

Open **http://127.0.0.1:5174/**. The Python service uses **8766** through the
dashboard proxy. Install while internet is available, then join the Go2 hotspot.
Obtain the private credentials from the instructor. Use only one robot client.

**Week 7:** preview and stationary connection/camera/state checks, with movement
disabled. **Weeks 8–9 onward:** use the same setup for reviewed stop checks,
supervised walking, recording/replay, and the maze. The Go1 simulator remains
a separate teaching checkout, not a hardware runtime.

After updating, restart both services, hard-refresh, and match **Navigation | UI
build ID** to the launcher. Enable gesture control is a direct click; fresh
tracking/video/state and the gesture hold still gate motion.

The UI already supplies **Jump once** and **Bound gait** as buttons, not default
hand gestures. They share the robot connection and pause navigation on selection.
Bound needs successful mode feedback and explicit gesture enabling afterward.
These are optional, separately approved experiments; ordinary walking remains
the required baseline. A reported successful jump is not full recovery
qualification, and Bound needs its own supervised checks. Read
[behavior and recovery](https://github.com/sriram-2502/go2-gesture-nav/blob/main/dashboard/CONTROL_EXTENSIONS.md).
Stationary Look Around remains disabled.

The personal repo's old `webrtc/` launch commands are obsolete after the layout
refactor. Follow its migration note; the existing `go2wifi` environment and saved
recordings can be reused. The research ROS starter is separate from this course.

## Earlier Go1 / ROS reference


The earlier Go1 project uses ROS Noetic across two computers: the operator laptop and the
Jetson AGX Xavier mounted on the Unitree Go1. Gesture perception, robot-view
perception, command validation, and actuation remain separate so each subsystem
can be tested safely.

## Robot Platform

- Unitree Go1 quadruped
- ZED 2i stereo camera
- Jetson AGX Xavier running ROS Noetic
- External battery pack for Jetson power
- Custom camera and compute mounting hardware

For more details, refer to the
[Go1 Density Social Navigation website](https://sriram-2502.github.io/go1_density_social_nav/).

<div class="hardware-gallery hardware-gallery-primary">
  <figure>
    <img src="{{ '/_images/hardware_go1_front.png' | prepend: site.baseurl }}" alt="Front view of the laboratory Go1 with labeled ZED 2i, Wi-Fi antennas, battery pack, and printed housing">
  </figure>
  <figure>
    <img src="{{ '/_images/hardware_go1_back.png' | prepend: site.baseurl }}" alt="Rear view of the laboratory Go1 with labeled Jetson AGX Xavier and battery pack">
  </figure>
</div>

## Runtime Architecture

```text
OPERATOR LAPTOP                         GO1 / JETSON AGX XAVIER

Laptop webcam                           ZED 2i
      |                                    |
      v                                    v
Gesture recognition                  ZED camera node
      |                                    |
      v                                    +-- /video
/gesture_intent                           +-- /camera_pose
      |                                    +-- /detections
      v                                    |
Confidence and temporal                   |
validation                                |
      |                                    |
      v                                    v
Gesture-control node <----------- Operator video display
      |
      v
Timeouts, limits, stop priority
      |
      v
/high_cmd
      |
      v
Unitree high-level bridge
      |
      v
Unitree Go1
```

### Operator Laptop

The laptop runs the ROS master, reads the operator-facing webcam, classifies hand
gestures, validates intent over time, displays the robot's `/video` stream, and
publishes bounded Unitree commands through the existing high-level bridge.

### Jetson Camera Node

The ZED 2i connects to the Jetson AGX Xavier mounted on the Go1. The existing
camera stack publishes the live robot view, ZED pose, and tracked detections to
the laptop's ROS master over the Go1 Wi-Fi network.

| Topic | ROS message | Purpose |
|:--|:--|:--|
| `/video` | `sensor_msgs/Image` | Live robot-view image |
| `/camera_pose` | `geometry_msgs/PoseStamped` | ZED camera pose |
| `/detections` | `autoware_msgs/DetectedObjectArray` | Tracked objects |

Robot motion is sent separately through the Unitree high-level bridge on
`/high_cmd`.

## Safety Boundary

Gesture recognition publishes abstract intent only. It cannot publish
`unitree_legged_msgs/HighCmd` directly. The gesture-control package owns command
limits, timeouts, stop precedence, and hardware arming. Loss of valid gesture
input or ROS communication results in a stop command.

## Operating Modes

1. **Mock mode:** gesture intent is visualized without publishing robot commands.
2. **Bridge test mode:** command mapping is inspected with hardware output disabled.
3. **Hardware mode:** approved limits are enabled under laboratory supervision.

## Mounting Hardware

The camera, compute, and power hardware use custom 3D-printed mounts carried on
the Go1. See the
[Go1 Density Social Navigation website](https://sriram-2502.github.io/go1_density_social_nav/)
for the source hardware documentation.

<div class="hardware-gallery hardware-gallery-mounts">
  <figure>
    <img src="{{ '/_images/hardware_camera_mount.png' | prepend: site.baseurl }}" alt="Slicer preview of the custom Go1 camera and compute mount">
    <figcaption>Camera and compute mounting structure.</figcaption>
  </figure>
  <figure>
    <img src="{{ '/_images/hardware_battery_holder.png' | prepend: site.baseurl }}" alt="Slicer preview of the external battery holders">
    <figcaption>External battery-holder components.</figcaption>
  </figure>
</div>
