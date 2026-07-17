---
layout: page
title: System Setup
permalink: /setup/
---

The project uses ROS Noetic across two computers: the operator laptop and the
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
