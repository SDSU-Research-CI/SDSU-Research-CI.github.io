---
layout: default
title: Submitting an Assignment
parent: Student Resources
grand_parent: GitHub Education
nav_order: 3
description: ""
permalink: /github/students/submitting-assignment
---

# Submitting an Assignment
Once you have completed your assignment, you must add your work to a git commit and then push this commit to your assignment repository. Your assignment is considered submitted each time you push a commit to your repo until the assignment deadline is reached.
This documentation assumes that you have created a [GitHub account](/github/students/creating-account) and have downloaded & installed [git](https://git-scm.com/downloads).
This documentation assumes that you have been working on the assignment locally, meaning that you cloned the repo to your computer as opposed to editing directly on GitHub.

Follow these instructions to submit your assignment:
1. Open up a terminal with git installed and navigate to the directory where you cloned your assignment repository
1. Copy and paste the following command to see if your repo has detected changes
    - `git status`
1. If you do have changes (modified, created or deleted files) you should see something similar to the following
    ```
    On branch main
    Your branch is up to date with 'origin/main'.
    Untracked files:
    (use "git add <file>..." to include in what will be committed)
        new-file.txt
    nothing added to commit but untracked files present (use "git add" to track)
    ```
    - If you do not have changes you may instead see the following
        ```
        On branch main
        Your branch is up to date with 'origin/main'.
        nothing to commit, working tree clean
        ```
1. Add your changes to a commit with this command
    - `git add *`
1. Save your commit with a message, indicating what you changed in 50 characters or less
    - Think of this as a Tweet about your changes
    - `git commit -m "I added new-file.txt"`
    - You may see output similar to the following, depending on what you changed
    ```
    [main 11f063f] I added new-file.txt
    1 file changed, 2 insertions(+)
    create mode 100644 new-file.txt
    ```
1. Submit your assignment by pushing your commit to your assignment repository with the following command
    - `git push -u origin main`
    - You should see output similar to the following
    ```
    Enumerating objects: 4, done.
    Counting objects: 100% (4/4), done.
    Delta compression using up to 8 threads
    Compressing objects: 100% (2/2), done.
    Writing objects: 100% (3/3), 335 bytes | 335.00 KiB/s, done.
    Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
    remote: This repository moved. Please use the new location:
    remote:  https://github.com/sandiegostate/sample-assignment-KyKri.git
    To https://github.com/sandiegostate/sample-assignment-kykri.git
    66ccbe9..11f063f main -> main
    branch 'main' set up to track 'origin/main'.
    ```
1. Navigate to your assignment repository on GitHub
    - ![](/images/github/submitting-assignment-1.png)
    - Verify that you see your changes were recently pushed

Congratulations! You have submitted your assignment to GitHub Classroom. You can repeat this process as you work on the assignment, but be mindful to push your final changes before the assignment deadline.
