---
layout: page
title: Project Roadmap
permalink: /roadmap/
---

## Current Week 1

Begin with [GitHub onboarding and the Go1 baseline]({{ '/week-01/' | prepend: site.baseurl }}).
This two-hour session covers repository access, team branches, running the
existing simulation baseline, and documenting the work.

[View all weekly activities]({{ '/weekly-activities/' | prepend: site.baseurl }}).

The next activity is [Week 2: Read, measure, and modify the Go1 controller]({{ '/week-02/' | prepend: site.baseurl }}).

The anticipated 12-week progression is flexible for holidays, preparation,
make-up work, additional testing, and changes in project progress. Weeks 1-5
build the gesture-to-Go1 simulation path, Weeks 6-7 cover supervised hardware
integration, and Week 8 begins the final project phase.

## Weekly Activities

| Week | Topic and Activity |
|:--:|:--|
| 1 | Project introduction, human–robot teaming objective, laboratory orientation, and robot safety |
| 2 | Read, measure, and modify the Go1 controller; basic control systems and reinforcement learning |
| 3 | Webcam input and hand tracking |
| 4 | Gesture recognition and temporal filtering |
| 5 | Gesture-to-command control in MuJoCo |
| 6 | Hardware interface and safety checkout |
| 7 | Supervised hardware integration |
| 8 | Final project definition and architecture |
| 9 | Final project implementation |
| 10 | Reliability testing and maze preparation |
| 11 | Supervised final demonstration rehearsal |
| 12 | Final project demonstration and technical review |

<div class="section-spacer" aria-hidden="true"></div>

## Course Milestones

Students progress through the following technical checkpoints:

1. **Development environment:** Verify the laptop software environment, webcam, and version-control workflow.
2. **Gesture recognition:** Demonstrate the starter gesture vocabulary using a laptop webcam and document its performance.
3. **Mock commands:** Show that gestures produce bounded abstract commands without operating the physical robot.
4. **Safety behavior:** Demonstrate default-stop behavior, command expiration, confidence checks, and obstacle-proximity stopping.
5. **Remote interface:** Operate laptop gesture recognition alongside the live Go1 camera feed.
6. **Maze design:** Build an instructor-approved modular maze that meets dimensional, visibility, and safety requirements.
7. **Final integration:** Navigate the Go1 through the approved maze under supervision using the complete gesture-based interface.

Laptop-webcam, mock-command, and safety milestones must be completed before live
robot testing. Hardware access remains subject to instructor approval and
laboratory supervision.

For the complete course requirements, see the
[preliminary Fall 2026 syllabus]({{ '/course_docs/CI_COURSE_SYLLABUS_FALL_2026.pdf' | prepend: site.baseurl }}).
