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
  <h2>Complete these four items in order</h2>
  <div class="week-start-links">
    <a href="{{ '/control-pipeline/' | prepend: site.baseurl }}"><strong>1. Understand the pipeline</strong><span>How commands become Go1 motion</span></a>
    <a href="{{ '/mujoco-orientation/' | prepend: site.baseurl }}"><strong>2. Learn the MuJoCo setup</strong><span>World, robot model, policy, and commands</span></a>
    <a href="https://github.com/sriram-2502/go1-mujoco-playground/blob/main/course/week-01-github-onboarding/windows-setup.md"><strong>3. Set up Windows 11</strong><span>Install Git, Miniconda, and dependencies</span></a>
    <a href="{{ '/git-worksheet/' | prepend: site.baseurl }}"><strong>4. Complete the Git worksheet</strong><span>Clone, branch, document, and push</span></a>
  </div>
</div>

## Goal

In this two-hour onboarding session, you will join the course GitHub workflow,
access your team's branch, run the instructor-provided Go1 baseline, and record
what you did in a one-page weekly summary.

No controller changes are required this week.

## Before you code

Read the one-page [Control Pipeline overview]({{ '/control-pipeline/' | prepend: site.baseurl }}) to see how a high-level velocity request becomes coordinated quadruped motion.

Use the short [Week 1 Git Worksheet]({{ '/git-worksheet/' | prepend: site.baseurl }}) while setting up your team branch and weekly summary.

Then read the [MuJoCo Orientation]({{ '/mujoco-orientation/' | prepend: site.baseurl }}) before launching the simulation.

## The standard weekly workflow

Most weeks follow the same pattern:

1. Fetch the latest instructor materials and read the week's activity page.
2. Open the relevant code in the course repository and understand the baseline.
3. Complete the worksheet, experiment log, or analysis requested for the week.
4. Push the worksheet and documentation to your team branch.
5. Propose code changes only when the activity calls for them.

Documentation is the default deliverable. If you believe a code change would
improve the system, discuss it with the instructor first. After instructor
consent, make the change on your team branch, explain it in your weekly summary,
and include evidence that it still works.

## Course code repository

The actual simulation code lives in
[sriram-2502/go1-mujoco-playground](https://github.com/sriram-2502/go1-mujoco-playground).

<div class="resource-links">
  <a href="https://github.com/sriram-2502/go1-mujoco-playground/tree/main"><strong>Instructor baseline</strong><span>Stable main branch</span></a>
  <a href="https://github.com/sriram-2502/go1-mujoco-playground/blob/main/course/week-01-github-onboarding/README.md"><strong>Complete task sheet</strong><span>Step-by-step instructions</span></a>
  <a href="https://github.com/sriram-2502/go1-mujoco-playground/tree/team-alpha"><strong>Team Alpha</strong><span>Team branch</span></a>
  <a href="https://github.com/sriram-2502/go1-mujoco-playground/tree/team-bravo"><strong>Team Bravo</strong><span>Team branch</span></a>
  <a href="https://github.com/sriram-2502/go1-mujoco-playground/blob/main/mujoco_playground/experimental/sim2sim/play_go1_keyboard.py"><strong>Keyboard controller</strong><span>Baseline simulation code</span></a>
</div>

## Two-hour activity

| Time | Activity |
|---:|---|
| 0:00–0:15 | Read the control-pipeline and MuJoCo orientation pages |
| 0:15–0:35 | Create or verify a GitHub account and review repository rules |
| 0:35–0:55 | Clone the course repository and enter the team branch |
| 0:55–1:25 | Run the existing Go1 keyboard simulation |
| 1:25–1:45 | Add a documentation-only weekly summary |
| 1:45–2:00 | Commit, push, and answer the open-ended design question |

## Team workflow

main is the instructor-maintained baseline. Students work on team-alpha or
team-bravo and must not push directly to main.

Create this file in your team branch:

weekly-summaries/week-01.md

Use the
[Week 1 summary template](https://github.com/sriram-2502/go1-mujoco-playground/blob/main/course/week-01-github-onboarding/README.md#weekly-summary-template).

## Safety and repository rules

Do not commit passwords, API keys, robot network credentials, private videos,
or other sensitive data. The repository is public. Do not connect to or command
the physical robot; this week uses the existing simulation baseline only.

## Completion evidence

By the end of the session, your team should have:

- the correct team branch checked out;
- a screenshot or short recording of the baseline simulation;
- a committed and pushed weekly-summaries/week-01.md; and
- a one-sentence explanation of the difference between main and a team branch.

[Open the complete Week 1 task sheet →](https://github.com/sriram-2502/go1-mujoco-playground/blob/main/course/week-01-github-onboarding/README.md)
