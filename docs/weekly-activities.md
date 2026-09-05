---
layout: page
title: Weekly Activities
permalink: /weekly-activities/
---

# Weekly Activities

This is the student-facing course path. Each week has one clear goal, a small
set of activities, and evidence to save in the team's code repository.

<div class="activity-callout">
  <strong>Start here:</strong>
  <span>Read the week, open the linked task sheet, then record your work in the
  team's weekly summary.</span>
</div>

## Course path

| Week | Focus | Student outcome |
|:--:|---|---|
| 1 | [GitHub onboarding and Go1 baseline]({{ '/week-01/' | prepend: site.baseurl }}) | Access the repository, use the team branch, run the baseline, and document the work. |
| 2 | [Go1 controller behavior, control, and reinforcement learning]({{ '/week-02/' | prepend: site.baseurl }}) | Explain the ONNX policy, measure command sensitivity, and make one approved change. |
| 3 | Webcam input and hand tracking | Capture webcam data and visualize hand landmarks. |
| 4 | Gesture recognition and temporal filtering | Produce stable symbolic gesture commands. |
| 5 | Gesture-to-command control in MuJoCo | Control the simulated Go1 with validated gestures. |
| 6 | Hardware interface and safety checkout | Verify communication and safety without physical motion. |
| 7 | Supervised hardware integration | Test bounded gesture control on the physical Go1. |
| 8 | Final project definition and architecture | Approve the team design, interfaces, backlog, and test plan. |
| 9 | Final project implementation | Integrate and extend the complete system in simulation. |
| 10 | Reliability testing and maze preparation | Measure repeatability and prepare the demonstration. |
| 11 | Supervised final demonstration rehearsal | Rehearse the complete project under instructor supervision. |
| 12 | Final project demonstration and technical review | Present and evaluate the complete system. |

## Week 1 activity resources

Complete these in order before submitting your individual summary:

<div class="resource-links">
  <a href="{{ '/control-pipeline/' | prepend: site.baseurl }}"><strong>1. Control Pipeline</strong><span>See how input becomes coordinated quadruped motion</span></a>
  <a href="{{ '/mujoco-orientation/' | prepend: site.baseurl }}"><strong>2. MuJoCo Orientation</strong><span>Understand the Go1 world, policy, sensors, and actions</span></a>
  <a class="github-link" href="https://github.com/sriram-2502/go1-mujoco-playground/blob/main/course/week-01-windows-simulation/README.md"><strong><i class="fab fa-github" aria-hidden="true"></i> 3. Windows 11 + MuJoCo Setup</strong><span>Install Git, VS Code, Miniconda, the course environment, and robot assets</span></a>
  <a class="github-link" href="https://github.com/sriram-2502/go1-mujoco-playground/blob/main/course/week-01-github-onboarding/weekly-summary-template.md"><strong><i class="fab fa-github" aria-hidden="true"></i> 4. Individual Summary Template</strong><span>Copy the Markdown template into your team branch</span></a>
</div>

## Week 2 activity resources

<div class="resource-links">
  <a href="{{ '/week-02/' | prepend: site.baseurl }}"><strong>Week 2 activity page</strong><span>Study control and RL, measure sensitivity, modify one parameter, and complete the design challenge</span></a>
  <a class="github-link" href="https://github.com/sriram-2502/go1-mujoco-playground/blob/main/course/week-02-go1-controller/README.md"><strong><i class="fab fa-github" aria-hidden="true"></i> Week 2 task sheet</strong><span>Detailed repository instructions</span></a>
  <a class="github-link" href="https://github.com/sriram-2502/go1-mujoco-playground/blob/main/course/week-02-go1-controller/worksheet.md"><strong><i class="fab fa-github" aria-hidden="true"></i> Week 2 worksheet</strong><span>Data tables, control/RL questions, and design challenge</span></a>
</div>

## Weekly routine

1. Read the goal and prerequisites.
2. Complete the activities with your team.
3. Save screenshots, terminal output, plots, or test results.
4. Commit the weekly summary to your team branch.
5. Review the completion checklist before moving forward.

[Open the project roadmap →]({{ '/roadmap/' | prepend: site.baseurl }})
