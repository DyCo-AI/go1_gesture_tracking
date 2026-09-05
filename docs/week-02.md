---
layout: page
title: Week 2 - Go1 controller behavior, control, and reinforcement learning
permalink: /week-02/
---

<div class="week-hero">
  <div>
    <p class="eyebrow">WEEK 02 · 2 HOURS · SYSTEMS + CODE</p>
    <h1>Go1 controller behavior, control, and reinforcement learning</h1>
    <p class="week-hero-lede">Move from running the baseline to understanding what the controller receives, what it produces, and how one small change affects behavior.</p>
  </div>
  <div class="week-hero-badge"><strong>Goal</strong><span>Explain and measure the control loop</span></div>
</div>

<div class="prereq-callout">
  <strong>Prerequisite:</strong>
  <span>Complete Week 1, confirm that the <code>go1-mujoco-playground</code> Conda environment runs the Go1 simulation, and work from your assigned team branch.</span>
</div>

## Follow these steps

1. Run the unchanged keyboard controller and fill in the baseline data table.
2. Read `play_go1_keyboard.py` and map the five important functions.
3. Explain the system using basic control-systems and reinforcement-learning terms.
4. Make one instructor-approved sensitivity change and measure it again.
5. Design a safer next input interface and record it in the worksheet.

Use the [Week 2 task sheet](https://github.com/sriram-2502/go1-mujoco-playground/blob/main/course/week-02-go1-controller/README.md) and the [Week 2 worksheet](https://github.com/sriram-2502/go1-mujoco-playground/blob/main/course/week-02-go1-controller/worksheet.md).

## The control idea

The keyboard creates a desired body velocity, represented by `vx`, `vy`, and
`yaw`. The controller combines that reference with robot measurements, sends
them through the frozen ONNX locomotion policy, and applies the resulting 12
joint actions in MuJoCo.

```text
desired velocity + measured robot state
                    ↓
              ONNX policy
                    ↓
             12 joint actions
                    ↓
              MuJoCo Go1
                    ↓
             new measurements
```

In control language, the desired velocity is the reference, the measurements
are feedback, the policy is the controller, and the simulated Go1 is the plant.

## The reinforcement-learning idea

The ONNX controller was trained before the course in simulation. During
training, an agent observes the simulated robot, selects joint actions, and
receives rewards for stable motion, command tracking, and other desired
behavior. The trained policy is then exported as an ONNX file for runtime use.

You are not retraining the policy this week. Your task is to understand its
input/output boundary: the playground provides a 48-value observation and the
policy returns 12 motor actions.

## Two-hour activity

| Time | Activity | Evidence |
|---:|---|---|
| 0:00-0:15 | Run the unchanged baseline | Baseline data table |
| 0:15-0:40 | Read and map the controller code | Five function explanations |
| 0:40-1:00 | Complete control and RL questions | Worksheet sections 3-4 |
| 1:00-1:25 | Make one approved sensitivity change | Git diff |
| 1:25-1:45 | Rerun and compare behavior | Before/after data table |
| 1:45-2:00 | Complete the next-interface design challenge | Five-box diagram |

## Required sensitivity challenge

Increase either the forward command increment from `0.25` to `0.50` or the
turning increment from `0.50` to `1.00`. Use the same input and number of trials
as the baseline. Record the values and observed motion in the worksheet, then
restore the original parameter.

## Optional stability challenge

With instructor approval, gradually increase one command value and find the
smallest value that produces visibly unstable behavior in simulation. Never try
to make the physical robot fall.

## Branch and code rules

Start from your assigned `team-alpha` or `team-bravo` branch, then create a
personal branch such as `week-02/your-name`. Do not push directly to `main` or
to the shared team branch while experimenting. Ask the instructor before
pushing an approved code change.

## Completion evidence

- Baseline and sensitivity data tables completed.
- Controller functions explained.
- Control and RL questions answered.
- One approved sensitivity change measured before and after.
- Original parameter restored.
- Five-box input-interface design completed.
