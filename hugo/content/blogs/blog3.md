---
title: "QuizAGator Development Blog"
date: 2019-04-25T15:15:06-04:00
draft: false
---

This page is dedicated to documenting the development contributed to the
QuizAGator project over the course of Spring 2019.

## What is [QuizAGator](https://GitHub.com/GatorEducator/quizagator)?

QuizAGator is a web application that provides an interface for creating quizzes
without the overhead of a GUI making quiz creation tedious and--in the case that
the design of the GUI tool changes--confusing.

## Development and Contribution

The development of this tool began slowly, as we needed to decide on a framework
to use as well as the method we wanted to use to implement the tool. We decided
to use Flask due to the overall confortability level of the team with flask as
well as one of our members having developed a tool in the past that we would be
able to use as reference for the beginning of the project. To this end we were
able to quickly get the Flask server running and the database entries organized
in a way that was beneficial to our end goal.

My contribution to this project consists of a myriad of commits in `teachers.py`,
`students.py`, and most of the HTML templates for the project, as well as writing
the README for the project. 
[PR #9 Added updated README](https://GitHub.com/GatorEducator/quizagator/pull/9).
Some of the most interesting parts of the project to me were in the Flask database
code, particularly in `teachers.py` and `students.py`. I enjoyed learning about
Flask database use and creating endpoints for functions that would later return
an HTML template file with the desired information. Finally, I wrote a simple
navigation bar for the web-interface that allows users to quickly and easily
move between the pages from any endpoint, as well as a logout button.

Here is a sample of the navigation bar for the teacher user type:

``teachers/base_template.html``

```HTML
<!-- simple list-style navbar -->
<div class="navbar">
  <ul>
    <li> <a href="/teachers/">Dashboard</a></li>
    <li> <a href="/teachers/classes/create">Create a Class</a></li>
    <li style="float:right;"> <a href="/logout/">Logout</a></li>
  </ul>
<div class="navbar">
  <ul>
    <li> <a href="/teachers/">Dashboard</a></li>
    <li> <a href="/teachers/classes/create">Create a Class</a></li>
    <li style="float:right;"> <a href="/logout/">Logout</a></li>
  </ul>
</div>
```

This creates a simple navbar for teachers that allows one to quickly select
the dashboard where the list of classes created can be viewed or a create
quiz page where new quizzes can be uploaded. I also styled this navbar myself
with a local custom css file.

## Teamwork and Reflection

In general the team worked well together, though at times getting everyone
together was difficult. In general however, everyone did their job and we were
able to get a great tool built during the time we had to work on it. We have a
minimum viable product complete for now and in the future will have a full
featured and completely styled tool for use in the department of computer
science here at Allegheny College.
