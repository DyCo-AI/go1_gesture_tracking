---
layout: home
---

<figure class="course-hero">
  <img src="{{ '/_images/poster_chatgpt3.png' | prepend: site.baseurl }}" alt="Concept artwork showing a gesture-guided Unitree Go1 mission-control interface">
  <figcaption>Mission-control concept artwork developed for the Fall 2026 Creative Inquiry project.</figcaption>
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

Build an AI-enabled mission-control interface for the Unitree Go1 quadruped
robot. Your laptop webcam will recognize hand gestures while the robot's live
camera feed becomes your only view of the maze. You will transform gestures such
as *forward*, *turn*, and *stop* into bounded robot velocity commands using
motion planning, control design, and safety logic.

Start with laptop-webcam experiments and mock commands. Finish with a live team
challenge: guide the Go1 through a student-built modular maze safely, quickly,
and without touching the walls.

<div class="pipeline-strip" aria-label="Project pipeline">
  <div><strong>1. Perceive</strong><span>Recognize human intent</span></div>
  <div><strong>2. Design</strong><span>Plan bounded motion</span></div>
  <div><strong>3. Control</strong><span>Command the Go1 safely</span></div>
</div>

## Quadruped Robot and Camera Setup

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

## Project Roadmap

The project progresses from laboratory orientation and laptop-only development
to gesture recognition, mock robot commands, live camera integration, safety
validation, and supervised maze-navigation demonstrations. Students establish
each subsystem safely before combining it with the physical Go1.

[View the detailed 12-week project roadmap →]({{ '/roadmap/' | prepend: site.baseurl }})

## Open-Ended Team Challenge

After the starter system works reliably, teams may propose additional gestures,
instructor-approved body poses or gaits, and time-limited motion primitives.
Every extension must use the approved command and safety interfaces, remain
bounded, and be interruptible by the stop command.

The required course challenge uses a flat cardboard maze. Optional terrain
modules are considered only after separate instructor review and validation.

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
