---
layout: page
title: Control Pipeline — How the Go1 Walks
permalink: /control-pipeline/
---

<div class="week-hero pipeline-hero">
  <div>
    <p class="eyebrow">WEEK 01 · SYSTEMS READING</p>
    <h1>How a high-level command becomes quadruped motion</h1>
    <p class="week-hero-lede">The course begins above the motor level. Your job is to shape safe motion intent; the provided locomotion system turns that intent into coordinated leg movement.</p>
  </div>
  <div class="week-hero-badge"><strong>Big idea</strong><span>Command → policy → joints → motion</span></div>
</div>

## The complete loop

<div class="pipeline-diagram" role="img" aria-label="High-level quadruped locomotion control pipeline">
  <div class="pipeline-node input-node"><strong>Human input</strong><span>Keyboard, joystick, or gesture</span></div>
  <div class="pipeline-arrow">→</div>
  <div class="pipeline-node"><strong>Motion intent</strong><span>vx, vy, yaw rate</span></div>
  <div class="pipeline-arrow">→</div>
  <div class="pipeline-node"><strong>Validation</strong><span>Bounds, timing, stop</span></div>
  <div class="pipeline-arrow">→</div>
  <div class="pipeline-node policy-node"><strong>Locomotion policy</strong><span>Observation → 12 actions</span></div>
  <div class="pipeline-arrow">→</div>
  <div class="pipeline-node"><strong>Robot motion</strong><span>Leg coordination and body movement</span></div>
</div>

The loop continues because sensors report what the robot is doing. The policy
uses the current observation, including robot motion, orientation, joint state,
previous actions, and the requested command, to choose the next joint actions.

## What students control

A high-level command describes desired body motion:

| Quantity | Meaning | Example |
|---|---|---:|
| vx | forward/backward velocity in the robot body frame | 0.3 m/s |
| vy | lateral velocity in the robot body frame | 0.0 m/s |
| yaw rate | turning speed around the vertical axis | 0.5 rad/s |

The command is not a motor command. It is a request such as “walk forward
slowly” or “turn left.” The provided controller and locomotion policy handle the
many joint-level decisions needed to produce that behavior.

## What the provided Go1 system does

1. **Reads the command.** The keyboard controller stores a three-value velocity
   command.
2. **Collects an observation.** The simulation supplies sensors, gravity
   direction, joint angles, joint velocities, previous actions, and the command.
3. **Runs the policy.** The bundled ONNX policy maps the observation to one
   action for each of the Go1's 12 actuated joints.
4. **Applies the action.** MuJoCo advances the simulated robot using the model's
   joints, actuators, contacts, and physics.
5. **Repeats the loop.** The next observation reflects the robot's new state.

The physical robot later uses the same high-level command concept, but a different
final interface. This separation lets you test command logic in simulation
before hardware is enabled.

## The current keyboard behavior

In the Week 1 baseline, an arrow-key callback changes the stored command. The
command persists after the key is released because the program receives a key
press event, not a continuous “key is currently held” signal. Enter explicitly
sets all command values to zero.

This is useful for learning the pipeline, but it creates an important design
question: what should happen when an input source stops updating?

## Open-ended Week 1 question

**How would you redesign the input layer so that motion stops automatically when
the operator is no longer providing input?**

A strong first proposal might:

- replace the keyboard with a joystick or gamepad;
- read an input value continuously;
- record the timestamp of the latest valid input;
- send a zero command when the input is unchanged, released, disconnected, or
  older than a timeout; and
- keep an explicit stop command with priority over every motion request.

Do not connect a physical joystick or robot for this exercise. Sketch the
interface, choose a reasonable timeout, and explain the tradeoff between
responsiveness and accidental stopping.

## Takeaway

Students are working on the command and safety layers around a pretrained
locomotion controller. The central engineering problem is not “how do I move
12 motors independently?” It is “how do I turn uncertain human intent into a
bounded, timely, interruptible request for coordinated robot motion?”

[Return to Week 1 activities →]({{ '/week-01/' | prepend: site.baseurl }})

