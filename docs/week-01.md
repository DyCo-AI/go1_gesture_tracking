---
layout: page
title: Week 1 — GitHub onboarding and Go1 baseline
permalink: /week-01/
---

<div class="week-hero">
  <div>
    <p class="eyebrow">WEEK 01 · 2 HOURS · TEAM ONBOARDING</p>
    <h1>GitHub onboarding and Go1 baseline</h1>
    <p class="week-hero-lede">Get access, find your team branch, run the existing simulation, and leave a clear record of what you learned.</p>
  </div>
  <div class="week-hero-badge"><strong>Goal</strong><span>Ready to work safely as a team</span></div>
</div>

<div class="week-steps">
  <div class="week-step"><span>01</span><strong>Access</strong><small>GitHub + repository</small></div>
  <div class="week-step"><span>02</span><strong>Branch</strong><small>team-alpha or team-bravo</small></div>
  <div class="week-step"><span>03</span><strong>Run</strong><small>existing Go1 baseline</small></div>
  <div class="week-step"><span>04</span><strong>Document</strong><small>weekly summary</small></div>
</div>

<div class="week-start-panel">
  <p class="eyebrow">START HERE</p>
  <h2>Complete these five items in order</h2>
  <div class="week-start-links">
    <a class="github-link" href="https://github.com/sriram-2502/go1-mujoco-playground/blob/main/course/week-01-windows-simulation/README.md"><strong><i class="fab fa-github" aria-hidden="true"></i> 1. Complete Windows 11 setup</strong><span>Install Git, VS Code, Miniconda, and MuJoCo dependencies before class</span></a>
    <a href="{{ '/control-pipeline/' | prepend: site.baseurl }}"><strong>2. Study the control pipeline</strong><span>How commands become Go1 motion</span></a>
    <a href="{{ '/mujoco-orientation/' | prepend: site.baseurl }}"><strong>3. Study the MuJoCo setup</strong><span>World, robot model, policy, and commands</span></a>
    <a class="github-link" href="https://github.com/sriram-2502/go1-mujoco-playground/blob/main/course/week-01-github-onboarding/README.md"><strong><i class="fab fa-github" aria-hidden="true"></i> 4. Run the existing playground</strong><span>Clone the repository, enter your team branch, and run the baseline</span></a>
    <a href="{{ '/git-worksheet/' | prepend: site.baseurl }}"><strong>5. Document and submit</strong><span>Complete the Git worksheet and your individual weekly summary</span></a>
  </div>
</div>

<div class="prereq-callout">
  <strong>Before class:</strong>
  <span>Complete the <a class="github-link" href="https://github.com/sriram-2502/go1-mujoco-playground/blob/main/course/week-01-windows-simulation/README.md"><i class="fab fa-github" aria-hidden="true"></i> Windows 11 and MuJoCo setup</a>. During the two-hour session we verify it, study the system, and run the baseline.</span>
</div>

<div class="week-flow">
  <div><span>01</span><strong>Study</strong><p>Read the <a href="{{ '/control-pipeline/' | prepend: site.baseurl }}">Control Pipeline</a> and <a href="{{ '/mujoco-orientation/' | prepend: site.baseurl }}">MuJoCo Orientation</a>.</p></div>
  <div><span>02</span><strong>Run</strong><p>Use your team branch to launch the existing Go1 MuJoCo Playground. Do not change code.</p></div>
  <div><span>03</span><strong>Question</strong><p>Propose one safer input idea and record it in your individual summary.</p></div>
  <div><span>04</span><strong>Submit</strong><p>Push only your named summary file to your team branch.</p></div>
</div>

## Goal

In this two-hour session, you will understand the system you are about to work
with, run the instructor-provided Go1 baseline, ask an open-ended design
question, and record your own findings in a one-page weekly summary.

No controller changes are required this week.

## What you will do this week

Read the one-page [Control Pipeline overview]({{ '/control-pipeline/' | prepend: site.baseurl }}) to see how a high-level velocity request becomes coordinated quadruped motion.

Use the short [Week 1 Git Worksheet]({{ '/git-worksheet/' | prepend: site.baseurl }}) while setting up your team branch and weekly summary. The Git worksheet is for practicing commands; your named weekly summary is the file you submit.

Then read the [MuJoCo Orientation]({{ '/mujoco-orientation/' | prepend: site.baseurl }}) before launching the simulation. You are learning how the pieces connect, not building a new controller yet.

## MuJoCo setup path

The code repository contains the complete Windows 11 setup for this course. Begin with [Week 1: Run the Go1 simulation on Windows 11](https://github.com/sriram-2502/go1-mujoco-playground/blob/main/course/week-01-windows-simulation/README.md). It walks you through Git and Miniconda, the `go1-mj-playground` environment, the Python dependencies, robot assets, the 48-value policy input, the 12 motor actions, and the keyboard simulation check.

The shorter [Week 1 GitHub onboarding task sheet](https://github.com/sriram-2502/go1-mujoco-playground/blob/main/course/week-01-github-onboarding/README.md) is the activity guide for the two-hour session. Use the simulation setup path first if the software is not installed.

### What counts as a successful run?

- The MuJoCo viewer opens and shows the Go1 model.
- Arrow keys produce forward, backward, and turning motion.
- Enter sends a zero command; Backspace stops and resets the simulation.
- You capture a screenshot or short recording and note one problem and its solution.

The current keyboard command persists after a key is released. Press **Enter** to stop. Do not connect to or command a physical robot.

## The standard weekly workflow

Most weeks follow the same pattern:

1. Fetch the latest instructor materials and read the week's activity page.
2. Open the relevant code in the course repository and understand the baseline.
3. Complete the worksheet, experiment log, or analysis requested for the week.
4. Push your documentation to your team branch. The Week 1 submission is an individual summary stored in the shared team branch.
5. Propose code changes only when the activity calls for them.

Documentation is the default deliverable. If you believe a code change would
improve the system, discuss it with the instructor first. After instructor
consent, make the change on your team branch, explain it in your weekly summary,
and include evidence that it still works.

## Course code repository

The actual simulation code lives in
<a class="github-link" href="https://github.com/sriram-2502/go1-mujoco-playground"><i class="fab fa-github" aria-hidden="true"></i> sriram-2502/go1-mujoco-playground</a>.

<div class="resource-links">
  <a class="github-link" href="https://github.com/sriram-2502/go1-mujoco-playground/tree/main"><strong><i class="fab fa-github" aria-hidden="true"></i> Instructor baseline</strong><span>Stable main branch</span></a>
  <a class="github-link" href="https://github.com/sriram-2502/go1-mujoco-playground/blob/main/course/week-01-github-onboarding/README.md"><strong><i class="fab fa-github" aria-hidden="true"></i> Complete task sheet</strong><span>Step-by-step instructions</span></a>
  <a class="github-link" href="https://github.com/sriram-2502/go1-mujoco-playground/tree/team-alpha"><strong><i class="fab fa-github" aria-hidden="true"></i> Team Alpha</strong><span>Team branch</span></a>
  <a class="github-link" href="https://github.com/sriram-2502/go1-mujoco-playground/tree/team-bravo"><strong><i class="fab fa-github" aria-hidden="true"></i> Team Bravo</strong><span>Team branch</span></a>
  <a class="github-link" href="https://github.com/sriram-2502/go1-mujoco-playground/blob/main/mujoco_playground/experimental/sim2sim/play_go1_keyboard.py"><strong><i class="fab fa-github" aria-hidden="true"></i> Keyboard controller</strong><span>Baseline simulation code</span></a>
</div>

## Two-hour activity

Setup is completed before class. The two-hour activity begins with reading and verification:

| Time | Activity |
|---:|---|
| 0:00–0:15 | Review the control-pipeline and MuJoCo orientation pages |
| 0:15–0:35 | Verify GitHub access and review repository rules |
| 0:35–0:55 | Clone the course repository and enter your assigned team branch |
| 0:55–1:25 | Run the existing Go1 keyboard simulation |
| 1:25–1:45 | Add a documentation-only weekly summary |
| 1:45–2:00 | Commit, push, and answer the open-ended design question |

Students work on `team-alpha` or `team-bravo`. `main` is read-only for students and is maintained by the instructor. Do not push directly to `main`.

### Individual submission

The weekly summary is an **individual** assignment. Each student fills out and
submits their own copy, even though the file is pushed to the shared team
branch. Use a unique filename so teammates do not overwrite one another:

<a class="github-link" href="https://github.com/sriram-2502/go1-mujoco-playground/blob/main/course/week-01-github-onboarding/weekly-summary-template.md"><i class="fab fa-github" aria-hidden="true"></i> Download the Markdown template</a>

Save your completed copy as:

<div class="code-callout">weekly-summaries/week-01-firstname-lastname.md</div>

Your summary should describe your own contribution, observations, problems,
and learning. Team members may share experiment evidence, but each student
should write their own reflection.

## Safety and repository rules

Do not commit passwords, API keys, robot network credentials, private videos,
or other sensitive data. The repository is public. Do not connect to or command
the physical robot; this week uses the existing simulation baseline only.

## Completion evidence

By the end of the session, you should have:

- the correct team branch checked out;
- a screenshot or short recording of the baseline simulation;
- your individual `weekly-summaries/week-01-firstname-lastname.md` committed and pushed to the shared team branch; and
- a one-sentence explanation of the difference between main and a team branch.
