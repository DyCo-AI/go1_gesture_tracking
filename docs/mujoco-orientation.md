---
layout: page
title: MuJoCo Orientation — The Go1 Simulation
permalink: /mujoco-orientation/
---

<div class="week-hero pipeline-hero">
  <div>
    <p class="eyebrow">WEEK 01 · MUJOCO ORIENTATION</p>
    <h1>What is inside the Go1 simulation?</h1>
    <p class="week-hero-lede">Before changing code, learn how the robot model, simulated world, pretrained policy, and command interface fit together.</p>
  </div>
  <div class="week-hero-badge"><strong>Think in layers</strong><span>World · robot · policy · commands</span></div>
</div>

## The simulation stack

<div class="pipeline-diagram" role="img" aria-label="MuJoCo Go1 simulation stack">
  <div class="pipeline-node"><strong>World model</strong><span>Ground, gravity, contacts</span></div>
  <div class="pipeline-arrow">→</div>
  <div class="pipeline-node"><strong>Go1 model</strong><span>Links, joints, actuators, sensors</span></div>
  <div class="pipeline-arrow">→</div>
  <div class="pipeline-node policy-node"><strong>ONNX policy</strong><span>48 observations → 12 actions</span></div>
  <div class="pipeline-arrow">→</div>
  <div class="pipeline-node"><strong>MuJoCo physics</strong><span>State evolves over time</span></div>
</div>

MuJoCo is a physics simulator. It does not merely draw a robot; it computes
motion, contacts, gravity, joint behavior, actuator forces, and sensor values
as simulated time advances.

## World description: URDF and MJCF

A **URDF** is commonly used to describe a robot's links, joints, visual geometry,
and collision geometry, especially in ROS workflows. It answers questions such
as: “How are the legs connected?” and “Where is this joint?”

MuJoCo commonly uses **MJCF**, an XML-based model format. MJCF can describe both
the robot and its environment:

- world bodies and ground;
- robot bodies, joints, and inertial properties;
- actuators and control parameters;
- cameras, lights, and sensors; and
- contacts and simulation options.

In this course, students are given a prepared Go1 MJCF/world configuration and
its required mesh assets. The keyboard runner loads that XML into MuJoCo, which
parses it into an internal model and simulation state. Week 1 is about
understanding and running this prepared world; students do not need to build a
world from scratch yet.

Later, students can inspect the XML and experiment with a flat world, terrain,
or maze. A useful mental model is:

```text
XML/MJCF + mesh assets
          ↓
       MjModel       fixed model: bodies, joints, actuators, sensors
          +
        MjData       changing state: positions, velocities, contacts
          ↓
       mj_step       advance the physics simulation
```

## The Go1 controller

The robot is running a **pretrained locomotion policy**, not a controller that
students train during Week 1.

The provided program:

1. loads the Go1 world and robot model;
2. loads the bundled ONNX policy;
3. builds an observation from simulated sensors and robot state;
4. appends the requested velocity command;
5. runs policy inference; and
6. applies 12 joint actions while MuJoCo advances the physics.

The policy is a learned mapping:

```text
observation (48 values) → ONNX policy → action (12 joint values)
```

The 12 outputs correspond to the Go1's 12 actuated joints. The policy handles
the coordination required to turn a high-level walking request into leg motion.

## Commands students can send

The command interface has three high-level values:

| Command | Meaning |
|---|---|
| vx | forward/backward velocity in the robot body frame |
| vy | lateral velocity in the robot body frame |
| yaw rate | turning speed about the vertical axis |

The current keyboard runner exposes:

| Key | Effect |
|---|---|
| Up arrow | Increase forward command |
| Down arrow | Decrease forward command |
| Left arrow | Increase turning command |
| Right arrow | Decrease turning command |
| Enter | Set all command values to zero |
| Backspace | Stop and reset the simulation |

The keyboard runner does not currently use a lateral-motion key. The underlying
command representation still includes lateral velocity so later input sources
can use the same interface.

## What students will replace

The locomotion policy remains the provided motion layer. The course work will
replace or extend the **input and command layers**:

```text
keyboard input
      ↓
gesture intent       voice intent       joystick input
      \                 |                 /
       └──── validated high-level command ────┘
                         ↓
                 same Go1 locomotion policy
```

Possible open-ended extensions include gesture commands, voice commands,
joystick control, command smoothing, automatic speed scaling, and stale-input
timeouts. Every extension must preserve bounded commands and a reliable stop
behavior.

[Read the control pipeline overview →]({{ '/control-pipeline/' | prepend: site.baseurl }})

[Return to Week 1 activities →]({{ '/week-01/' | prepend: site.baseurl }})

