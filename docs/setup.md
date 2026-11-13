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


## Current Go2 course setup

| Stage | Use this repository / interface |
| --- | --- |
| Weeks 1–6: simulation and reports | [go1-mujoco-playground](https://github.com/sriram-2502/go1-mujoco-playground); individual reports on the assigned team branch |
| Week 7: stationary Basic checkout | [Clemson DyCo-AI/go2-webRTC](https://github.com/DyCo-AI/go2-webRTC); Basic UI on port 5173, no MediaPipe |
| Weeks 8–9 onward: gesture hardware | [Personal go2-gesture-nav](https://github.com/sriram-2502/go2-gesture-nav); Clemson UI on port 5174 plus the Python gesture service |

Follow the [course hardware guide](https://github.com/sriram-2502/go1-mujoco-playground/blob/main/course/GO2_HARDWARE.md#which-setup-to-use)
for the transition. The Week 7 starter uses root-level setup/start scripts;
the personal Clemson setup uses `webrtc\setup-ui.ps1 -Edition clemson` and
`webrtc\start-ui.ps1 -Edition clemson`, plus a separate Python terminal.
Keep the two checkouts separate, and disconnect/stop Basic before opening
Clemson. Neither course path needs ROS on the Windows operator laptop.

For the personal UI, follow its [quick start](https://github.com/sriram-2502/go2-gesture-nav#quick-start-on-windows-11)
or [update/restart instructions](https://github.com/sriram-2502/go2-gesture-nav#update-and-restart).
After restarting, hard-refresh the browser and match **Navigation | UI build ID**
to the launcher. That confirms the loaded code, not physical qualification.
Click **Enable gesture control** directly; no palm/fist startup pose is needed.
New tracking frames, fresh video/state, and the consistency hold still gate motion.

The personal Clemson UI already supplies **Jump once** (one forward-jump
request) and **Bound gait** (a persistent gait selection followed by explicit
gesture enabling). They are buttons, not default hand gestures. Both pause
navigation on selection and use the existing robot connection. See
[behavior selection and recovery](https://github.com/sriram-2502/go2-gesture-nav/blob/main/webrtc/clemson/CONTROL_EXTENSIONS.md).
The maintainer has reported a successful forward jump and landing; that is not
full interruption/recovery qualification. Bound requires its own supervised
hardware checks. These are optional instructor-approved experiments; the required
baseline remains ordinary walking in a flat maze. A sent/acknowledged request
does not establish completed motion.

Record the approved hardware-repo commit and UI build ID in your report. Obtain
the assigned robot's credentials privately and use its Go2 hotspot, not campus
Wi-Fi. The Basic starter does not include Clemson's gesture panel or Jump/Bound
workflow. Do not substitute its unrestricted upstream action grid for the
supervised course interface.

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
