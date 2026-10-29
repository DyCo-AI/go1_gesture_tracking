---
layout: page
title: Safety Principles
permalink: /safety/
---

> **Current course implementation:** the course keeps its Go1 name. Students use
> Go1 simulation first, then **Go2 on Windows 11 over Wi-Fi/WebRTC**. Physical Go1
> integration is under development; Go1/ROS/Jetson/ZED descriptions are legacy
> architecture references, not the hardware instructions for this course version.
> Use the [student code and weekly labs](https://github.com/sriram-2502/go1-mujoco-playground)
> and [current Go2 onboarding](https://github.com/sriram-2502/go1-mujoco-playground/blob/main/course/GO2_HARDWARE.md).


Safety is a system requirement and a prerequisite for hardware access.

## Command Rules

- No gesture directly produces an unbounded or persistent hardware command.
- All motion commands use instructor-approved speed and yaw-rate limits.
- Commands expire unless refreshed by valid, current input.
- Low-confidence or inconsistent classifications are treated as no command.
- Stop always overrides every other gesture or motion primitive.
- Student-defined actions must remain time-limited and interruptible.

## Fail-Safe Conditions

The robot must command zero velocity when gesture perception, the operator's
video feed, robot communication, or the controller heartbeat is lost or stale.
Obstacle proximity may also suppress or modify a requested command through the
safety supervisor.

## Hardware Operation

- Robot operation requires instructor or authorized laboratory supervision.
- Teams progress from mock mode to simulation before physical motion tests.
- The test area must be controlled and cleared before arming.
- One team member must be ready to trigger the independent emergency stop.
- Batteries, cables, mounts, and communications are checked before every run.

