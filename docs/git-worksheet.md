---
layout: page
title: Week 1 Git Worksheet
permalink: /git-worksheet/
---

# Week 1 Git Worksheet

Use this sheet during the onboarding session. Replace values in angle brackets
with your own information.

## 1. Identify yourself

Configure Git once on your computer:

```powershell
git config --global user.name "<Your Name>"
git config --global user.email "<your-github-email>"
git config --global init.defaultBranch main
```

Check the settings:

```powershell
git config --global user.name
git config --global user.email
```

## 2. Get the course repository

```powershell
cd $HOME\Downloads
git clone https://github.com/sriram-2502/go1-mujoco-playground.git
cd .\go1-mujoco-playground
git remote -v
git status
```

A clean repository should report that there is nothing to commit.

## 3. Inspect the course branches

```powershell
git fetch origin
git branch -a
git switch main
git log --oneline -5
```

The instructor's stable code is on **main**. Do not edit or push directly to it.

## 4. Enter your team branch

Use the branch assigned by your instructor:

```powershell
git switch --track origin/team-alpha
```

or:

```powershell
git switch --track origin/team-bravo
```

Confirm where you are:

```powershell
git branch --show-current
git status
```

## 5. Make a weekly summary

Create this file:

```text
weekly-summaries/week-01.md
```

Record your goal, what you did, evidence, one problem, and one thing you learned.

## 6. Save and publish your work

```powershell
git add weekly-summaries/week-01.md
git status
git commit -m "Add week 01 summary"
git log --oneline -1
git push
```

After pushing, refresh your team branch on GitHub and confirm that the file is
visible there.

## 7. Useful inspection commands

```powershell
git status                 # What changed?
git diff                   # What is different but not staged?
git diff --staged          # What will be committed?
git log --oneline -5       # What are the latest commits?
git branch -vv             # Which branch am I tracking?
git remote -v              # Which GitHub repository am I using?
```

## Remember

- Work on `team-alpha` or `team-bravo`, not `main`.
- Read `git status` before committing.
- Make small commits with clear messages.
- Never commit passwords, tokens, robot credentials, private videos, or large
  generated files.
- Git records history; it does not replace the weekly summary.

[Return to Week 1 activities →]({{ '/week-01/' | prepend: site.baseurl }})

