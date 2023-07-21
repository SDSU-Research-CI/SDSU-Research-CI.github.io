---
layout: default
title: Creating an Assignment
parent: Instructor Resources
grand_parent: GitHub Education
nav_order: 3
description: ""
permalink: /github/instructors/creating-assignment
---

# Creating an Assignment
Once your GitHub Classroom has been created, you can start creating assignments. GitHub classroom supports both individual and group assignments as well as making the assignments viewable to other students or private between the student and teacher.

Assignments will be based on an existing GitHub repository, so you must create or find a repo to use for an assignment. 
In this example we will use the GitHub Classroom's [github-starter-course](https://github.com/sandiegostate/github-starter-course) which is available on the [sandiegostate](https://github.com/sandiegostate) GitHub Organization. 
Note that this repository is private, so you must first [request access to GitHub Classroom](/github/instructors/requesting-access).

{: .highlight }
We highly recommend using the github-starter-course assignment as it ensures students have a foundation for using Git and GitHub.

This documentation assumes that you have already [created a GitHub Classroom](/github/instructors/creating-classroom).

Follow these steps to create your first assignment:
1. If not already signed in, sign in to [https://classroom.github.com/](https://classroom.github.com/)
1. Click one of your available classrooms
    - ![](/images/github/pick-classroom1.png)
1. If this is your first assignment for this classroom you will see the below:
    - ![](/images/github/classroom7.png)
    - Click 'Create an assignment'
1. If this is not the first assignment for the classroom, you may instead see the below:
    - ![](/images/github/new-assignment1.png)
    - Click 'New assignment'
1. Fill out the form and then click 'Contine'
    - ![](/images/github/classroom8.png)
    - In this example we have chosen an individual assignment, no deadline and private repos so that each student can only see their own work
1. From the following form, click the 'Select a repository' dropdown and paste in 'github-starter-course'
    - ![](/images/github/classroom9.png)
1. Select the 'sandiegostate/github-starter-course' option
    - ![](/images/github/classroom10.png)
1. Optionally, click the 'Select an editor' dropdown and choose 'Visual Studio Code'
    - ![](/images/github/classroom11.png)
1. Click 'Continue'
    - ![](/images/github/classroom12.png)
1. We will not be using autograding on this example assignment, but feel free to explore the options. When done, click 'Create assignment'
    - ![](/images/github/classroom13.png)
1. You should see your assignment:
    - ![](/images/github/new-assignment2.png)
        1. If instead you run into this page, just click the 'Try going back to classroom dashboard' link
            - ![](/images/github/classroom14.png)
        1. Click on your classroom
            - ![](/images/github/classroom15.png)
        1. Click on your assignment
            - ![](/images/github/classroom16.png)
1. Click 'Got it' on the pop-up
    - ![](/images/github/classroom17.png)
1. Click the copy button to copy the assignment invitation URL
    - ![](/images/github/classroom18.png)
1. You can now share this link with your students however you like (email, Canvas, etc.)
1. Preview the assignment acceptance page by pasting the link in a new tab in your browser
    - ![](/images/github/classroom19.png)
    - Note: Students will be prompted to sign into or to create a GitHub account:
        - ![](/images/github/classroom20.png)
1. Once students accept the assignment invite you will see them populate in the list:
    - ![](/images/github/classroom21.png)
    - Note that you can see the student's progress at a high level with the status pill, in this case it is a red 'Not submitted' status and the commit count is 0
1. Once a student submits their assignment, you can click the 'Repository' link next to their name to check their work:
    - ![](/images/github/classroom22.png)
    - Note that the status pill has changed to a green 'Submitted' status and that the commit count is now greater than 0