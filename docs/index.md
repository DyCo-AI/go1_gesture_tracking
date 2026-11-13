---
layout: home
---

> **Current course implementation:** the course keeps its Go1 name. Students use
> Go1 simulation first, then **Go2 on Windows 11 over Wi-Fi/WebRTC**. Physical Go1
> integration is under development; Go1/ROS/Jetson/ZED descriptions are legacy
> architecture references, not the hardware instructions for this course version.
> Use the [student code and weekly labs](https://github.com/sriram-2502/go1-mujoco-playground)
> and [current Go2 onboarding](https://github.com/sriram-2502/go1-mujoco-playground/blob/main/course/GO2_HARDWARE.md).


<figure class="course-hero">
  <img src="{{ '/_images/poster_chatgpt3.png' | prepend: site.baseurl }}" alt="Concept artwork showing human gestures translated into intelligent motion for a Unitree Go1">
  <figcaption>From human gestures to intelligent robot motion: mission-control concept artwork for the Fall 2026 Creative Inquiry project.</figcaption>
</figure>

<div class="course-facts">
  <div><strong>Course</strong><span>ME 2900/3900/4900</span></div>
  <div><strong>Credit</strong><span>1 credit hour</span></div>
  <div><strong>Meeting</strong><span>Friday, 10:00 a.m.–12:00 noon</span></div>
  <div><strong>Location</strong><span>EIB 257, in person</span></div>
  <div><strong>Teams</strong><span>Primarily teams of two</span></div>
  <div><strong>Enrollment</strong><span>Instructor consent</span></div>
</div>

> **Syllabus status:** The linked Fall 2026 syllabus is preliminary. The final version is TBA.

<div class="document-actions">
  <a class="document-button primary" href="{{ '/course_docs/CI_COURSE_SYLLABUS_FALL_2026.pdf' | prepend: site.baseurl }}">Read the preliminary syllabus (PDF)</a>
  <a class="document-button" href="{{ '/course_docs/CI_COURSE_POSTER_FALL_2026.pdf' | prepend: site.baseurl }}">View the recruitment poster (PDF)</a>
</div>

## Your Mission

Build an AI-enabled mission-control interface for a Unitree quadruped.
This version uses Go1 simulation followed by Go2 hardware. Your laptop webcam will recognize hand gestures while the robot's live
camera feed becomes your only view of the maze. You will transform gestures such
as *forward*, *turn*, and *stop* into bounded robot velocity commands using
motion planning, control design, and safety logic.

Start with laptop-webcam experiments and mock commands. Finish with a live team
challenge: guide the Go2 through a student-built modular maze safely, quickly,
and without touching the walls.

<div class="pipeline-strip" aria-label="Project pipeline">
  <div><strong>1. Perceive</strong><span>Recognize human intent</span></div>
  <div><strong>2. Design</strong><span>Plan bounded motion</span></div>
  <div><strong>3. Control</strong><span>Command the robot safely</span></div>
</div>

## See the instructor baseline in action

This 15-second dashboard clip shows the **instructor's baseline version**:
hand-gesture recognition alongside the Go2's onboard camera, voxel view, and
requested, supervised, transmitted, and measured velocity. It is the starting
point students will build on throughout the course.

<figure class="baseline-demo">
  <video controls muted playsinline preload="none" width="1280" height="648" poster="{{ '/assets/go2-instructor-baseline.png' | prepend: site.baseurl }}" aria-label="15-second instructor baseline: Go2 gesture-navigation dashboard" aria-describedby="baseline-caption">
    <source src="{{ '/assets/go2-instructor-baseline.mp4' | prepend: site.baseurl }}" type="video/mp4">
    Your browser does not support embedded video. <a href="{{ '/assets/go2-instructor-baseline.mp4' | prepend: site.baseurl }}">Watch the dashboard clip.</a>
  </video>
  <figcaption id="baseline-caption">Instructor baseline · 15 seconds · silent. Robot views, extracted hand landmarks, and velocity feedback share one dashboard. This clip predates the supplied Jump once / Bound gait buttons; those optional behaviors are not demonstrated here.</figcaption>
</figure>

### Your next step: build the maze, extend the robot

Teams will **design and build a modular maze** that represents features of
unstructured environments: narrow passages, irregular layouts, and changing
obstacle arrangements. Start with flat cardboard walls, then use the same
course to compare the baseline with your own extensions.

- **Extend the interface:** bring your own gesture classifier and add deliberate commands for new behaviors.
- **Explore robot behaviors:** study the supplied Jump once / Bound gait controls or design deliberate behavior-selection interfaces. Check the existing transport/recovery logic offline before separately approved hardware trials; the Go1 simulation baseline is not a Go2 jumping model.
- **Build and evaluate:** rearrange your maze, navigate from the robot's camera view, and compare completion time, wall contacts, and stop responses using recorded runs.

The goal is to turn a working baseline into your team's own navigation system.
Jumping and terrain modules are optional extensions requiring separate
instructor approval; the core challenge remains a flat maze.

### Use the reference to get started

| Stage | Use this repository / interface |
| --- | --- |
| Weeks 1–6: simulation and reports | [go1-mujoco-playground](https://github.com/sriram-2502/go1-mujoco-playground); individual reports on the assigned team branch |
| Week 7: stationary Basic checkout | [Clemson DyCo-AI/go2-webRTC](https://github.com/DyCo-AI/go2-webRTC); Basic UI on port 5173, no MediaPipe |
| Weeks 8–9 onward: gesture hardware | [Personal go2-gesture-nav](https://github.com/sriram-2502/go2-gesture-nav); Clemson UI on port 5174 plus the Python gesture service |

The [**go2-gesture-nav instructor reference**](https://github.com/sriram-2502/go2-gesture-nav)
provides the Windows 11 Clemson dashboard, supervised velocity commands,
local recording/replay, and the optional Jump once / Bound gait controls. Use
[the course setup page]({{ '/setup/' | prepend: site.baseurl }}) to distinguish
the Week 7 Basic starter from the later personal Clemson UI.

- Explore the [system design](https://github.com/sriram-2502/go2-gesture-nav#system-design) and [default gesture guide](https://github.com/sriram-2502/go2-gesture-nav#default-gestures).
- Follow [the student hardware onboarding](https://github.com/sriram-2502/go1-mujoco-playground/blob/main/course/GO2_HARDWARE.md) after the simulation checkpoint.
- Bring your earlier gesture classifier into [the reference integration point](https://github.com/sriram-2502/go2-gesture-nav/blob/main/webrtc/STUDENT_INTEGRATION.md), while retaining command supervision and robot checks.

Use the reference to understand and extend the system; keep your own development
history and follow the course's team-branch README submission policy. Hardware
motion remains instructor-supervised, with credentials obtained privately.

## Earlier Go1 Robot and Camera Reference

<div class="setup-grid">
  <figure>
    <img src="{{ '/_images/go1_setup.jpg' | prepend: site.baseurl }}" alt="Laboratory Unitree Go1 with its ZED 2i and Jetson compute stack">
  </figure>
  <div>
    <h3>Two cameras, two different jobs</h3>
    <p><strong>Laptop webcam:</strong> observes the operator's hand and recognizes the starter gesture vocabulary—stop, forward, backward, left, and right.</p>
    <p><strong>Robot-mounted ZED 2i:</strong> connects to the Jetson AGX Xavier and publishes the live robot view. The operator navigates from this video instead of looking directly at the maze.</p>
    <p><strong>Operator laptop:</strong> uses validated gesture intent and robot-camera information to design a safe, intelligent, and bounded velocity plan. It then sends approved high-level velocity commands to the Go1 through the laboratory's Unitree interface.</p>
    <p><strong>Safety layer:</strong> converts only validated gestures into approved, bounded actions and stops the robot when commands are stale or uncertain, communication or perception is lost, or an obstacle enters the stopping region.</p>
    <p><a href="{{ '/setup/' | prepend: site.baseurl }}">Explore the system setup →</a></p>
  </div>
</div>

## What You Will Learn

- Understand how sensing, computation, planning, control, and actuation form an integrated robotic system.
- Use AI-based computer vision to recognize hand gestures and interpret human intent.
- Translate human intent into bounded robot motion using motion planning, control design, and safety constraints.
- Build, test, and communicate a human–robot teaming system through mock-mode and hardware experiments.
- Apply version control, experimental testing, data analysis, teamwork, and technical communication in a real robotics project.

Curiosity matters more than prior coding experience. The project builds the
required Python, computer-vision, Git, and robot-communication skills as the
teams progress.

[View the complete project overview and learning outcomes →]({{ '/project/' | prepend: site.baseurl }})

[Weekly reports and experiment data]({{ '/student-work/' | prepend: site.baseurl }}): individual README reports on team branches; full recordings stay local.

## Project Roadmap

The project progresses from laboratory orientation and laptop-only development
to gesture recognition, mock robot commands, live camera integration, safety
validation, and supervised maze-navigation demonstrations. Students establish
each subsystem safely before combining it with the physical Go2.

[View the detailed 12-week project roadmap →]({{ '/roadmap/' | prepend: site.baseurl }})

## Open-Ended Team Challenge

Build on the [instructor baseline](#see-the-instructor-baseline-in-action) with
your own gesture vocabulary, experiments using the supplied gait/jump controls,
or a deliberate behavior-selection interface. Design the maze as part of the experiment and measure what each
extension changes. See the [team challenge and extension progression]({{ '/project/#open-ended-extensions' | prepend: site.baseurl }})
for how to move from a flat maze to optional, reviewed terrain modules.

## About the DyCo-AI Lab

<div class="lab-intro">
  <img src="{{ '/_images/dyco_ai_lab_research_thrusts.png' | prepend: site.baseurl }}" alt="DyCo-AI Lab research thrusts in autonomy, robotics, control, and learning">
  <p>The <strong>Dynamics and Control for Autonomy and Intelligence (DyCo-AI) Lab</strong> in Clemson Mechanical Engineering designs data-driven controllers for next-generation robots, including quadrupeds and humanoids. We combine dynamics, control, learning, and safety to help autonomous systems operate reliably in complex environments. <a href="https://dyco-ai.github.io/dycoailab_web/">Visit the DyCo-AI Lab website →</a></p>
</div>

## Project Advisors

<div class="advisor-grid">
  <div class="advisor-card">
    <img class="advisor-photo" src="{{ '/_images/umesh.jpg' | prepend: site.baseurl }}" alt="Dr. Umesh Vaidya">
    <div>
      <h3>Dr. Umesh Vaidya</h3>
      <p>Professor<br>
      Department of Mechanical Engineering<br>
      125A Fluor Daniel Building<br>
      <a href="mailto:uvaidya@clemson.edu">uvaidya@clemson.edu</a><br>
      Office hours by appointment</p>
    </div>
  </div>
  <div class="advisor-card">
    <img class="advisor-photo" src="{{ '/_images/sriram.png' | prepend: site.baseurl }}" alt="Sriram Krishnamoorthy, Ph.D.">
    <div>
      <h3>Sriram Krishnamoorthy, Ph.D.</h3>
      <p>Post-doctoral Fellow<br>
      Department of Mechanical Engineering<br>
      121 Fluor Daniel Building<br>
      <a href="mailto:sriramk@clemson.edu">sriramk@clemson.edu</a><br>
      Office hours by appointment</p>
    </div>
  </div>
</div>

Students may have the opportunity to present at Clemson University's annual
Focus on Creative Inquiry Forum. With advisor approval, technically mature work
may also be developed toward an IEEE conference or robotics competition.

<div class="document-actions bottom-actions">
  <a class="document-button primary" href="{{ '/course_docs/CI_COURSE_SYLLABUS_FALL_2026.pdf' | prepend: site.baseurl }}">Download preliminary syllabus</a>
  <a class="document-button" href="{{ '/course_docs/CI_COURSE_POSTER_FALL_2026.pdf' | prepend: site.baseurl }}">Download the poster</a>
</div>
