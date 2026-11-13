---
layout: page
title: Project Overview
permalink: /project/
---

> **Current course implementation:** the course keeps its Go1 name. Students use
> Go1 simulation first, then **Go2 on Windows 11 over Wi-Fi/WebRTC**. Physical Go1
> integration is under development; Go1/ROS/Jetson/ZED descriptions are legacy
> architecture references, not the hardware instructions for this course version.
> Use the [student code and weekly labs](https://github.com/sriram-2502/go1-mujoco-playground)
> and [current Go2 onboarding](https://github.com/sriram-2502/go1-mujoco-playground/blob/main/course/GO2_HARDWARE.md).


## Mission

Develop and evaluate an intuitive, safety-aware interface for remote quadruped
navigation. The human provides motion intent with hand gestures; the robot-side
system converts that intent into approved high-level actions while enforcing
command limits and stop conditions.

## Learning Outcomes

Upon successful completion of the course, students will be able to:

1. Describe the basic architecture of a robotic system, including sensing, computation, communication, control, and actuation.
2. Explain fundamental concepts in human–robot teaming, including how a human operator and a robot share information, decisions, and control responsibilities.
3. Apply basic robot-motion and control concepts, including body-frame velocity, turning rate, gait selection, and high-level command generation.
4. Use and evaluate camera-based AI models for hand detection and gesture recognition.
5. Apply introductory motion-planning and control-design concepts to translate recognized operator intent into bounded, safe robot velocity commands.
6. Integrate sensing, human commands, control logic, and robot hardware into a functional mechatronic system.
7. Incorporate safety constraints and fail-safe behavior into robot operation under uncertain perception, communication delays, and nearby obstacles.
8. Design and conduct repeatable engineering tests, analyze recorded data, and use evidence to evaluate performance and justify design decisions.
9. Contribute effectively to a collaborative robotics project using appropriate documentation, version control, and project-management practices.
10. Communicate the motivation, design, results, limitations, and future directions of a robotics project to technical and nontechnical audiences.
11. Prepare and present project results through a research poster and live robot demonstration for audiences beyond the classroom.

## Final Demonstration

The operator works from a mission-control station without direct visual contact
with the robot or maze. Using only the live onboard video and hand gestures, the
team guides the Go2 through a student-built modular maze. A successful system must finish the
course while respecting safety boundaries and remaining immediately stoppable.

## Open-Ended Extensions

The [instructor dashboard demonstration]({{ '/#see-the-instructor-baseline-in-action' | prepend: site.baseurl }})
shows the baseline students will extend. Teams own both the interface extensions
and the design of their modular maze, using it as a repeatable model of features
found in unstructured environments.

1. **Establish the baseline.** Navigate a flat cardboard maze using gesture-to-velocity commands and the onboard camera. Record completion time, wall contacts, and stop responses.
2. **Design your extension.** Add new gesture commands, compare the supplied Jump once / Bound gait behaviors, or design a deliberate selection interface where the assigned robot supports it. These buttons already exist in the personal Clemson reference; implementing them again is not required. Explain behavior selection, bounds, interruption/recovery, and usefulness. Validate application logic with offline tests before separately approved hardware trials; the existing Go1 simulator does not qualify Go2 jumping.
3. **Build the experiment.** Rearrange passages and obstacles to compare baseline and extended navigation. Optional terrain or jump modules need separate instructor review before construction and hardware trials.
4. **Evaluate the result.** Repeat runs on the same layout, compare performance, and explain recognition errors, delays, and behavior-selection decisions using recordings.

Use the [course setup progression]({{ '/setup/' | prepend: site.baseurl }}) and
[reference behavior/recovery guide](https://github.com/sriram-2502/go2-gesture-nav/blob/main/webrtc/clemson/CONTROL_EXTENSIONS.md)
for what is implemented and what still needs qualification. The older dashboard
clip does not demonstrate the new buttons.

The required demonstration remains a flat maze. Gait changes, jumping, and terrain
modules are optional, instructor-approved extensions developed through simulation
and supervised hardware testing. Preserve the supplied command supervision and
robot checks; each added behavior needs a validated interruption or recovery
procedure appropriate to that behavior. Extensions are evaluated for usefulness,
repeatability, and safety.
