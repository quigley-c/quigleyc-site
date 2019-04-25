---
title: "Gatorgrader Development Blog"
date: 2019-03-14T13:34:30-05:00
draft: false
---

This page is dedicated to documenting the development contributed to the
Gatorgrader project over the course of Fall 2019.

## What is [Gatorgrader](https://GitHub.com/GatorEducator/gatorgrader)?

Gatorgrader is an automated assessment tool designed for use with GitHub,
Travis CI, and Gradle that checks the word of programmers and writers.
While there are other tools that check styling or linting, Gatorgrader
focuses specifically on the aspect of using a tool to grade assignments in a
classroom setting. The tool is most generally run using the command
`gradle grade` from the command line, and is also designed to run smoothly
from a Travis CI environment.

## PR [#126](https://github.com/GatorEducator/gatorgrader/pull/126) Add a feature to support checks of the GitHub issue tracker

[PR #126](https://github.com/GatorEducator/gatorgrader/pull/126)

I lead the team working on the Gatorgrader feature to add support for checking the
GitHub issue tracker as well as a number of small fixes and enhancements. This
feature involved implementing a method of authenticating with GitHub to get the
number of issues raised and the comments made on any PRs and issues. We primarily
used [PyGithub](https://pypi.org/project/PyGithub/) to more easily access the
GitHub REST API to grab issues from any given GitHub repository, an example of
which is shown below:

```Python
# import the PyGithub library for GitHub API
from github import Github
```

Once the authentication process had been figured out, grabbing the issues proved
not to be an extremely difficult task. The major stumbling point for our team was
the puzzle of authenticating safely and making the feature available for both
offline use and through Travis CI. We solved this problem by working with the
[GatorGradle](https://github.com/GatorEducator/gatorgradle) team to implement
command-line instructions for the tool to request an access token from the user
to authenticate safely to the GitHub repository. The lines which take the
arguments shown:

in `orchestrate.py`

```Python
# snippet of code showing the code denoting the arguments for the GatorGrader run
if system_arguments.issues is not None:
	actions.append(
		[
			# each `system_arguments. ` line denotes an argument
			INVOKE
			"invoke_issues_check",
			[system_arguments.token, system_arguments.repo,
			system_arguments.name, system_arguments.issues,
			system.arguments.state],
		]
	)
```

The process of working on this tool was extremely enlightening to the difficulties
associated with working on a public, open-source tool while also maintaining a
high degree of security in accordance with the standards in place for projects
on GitHub with the interest of keeping projects completely secure.

Testing the GatorGrader project using a test suite was also a big part of the
development of the project, as the code coverage of the project was already
nearly perfect, so every feature written had to also include an accompanying
test case. These test cases proved a much more tricky task to complete, as testing
would potentially require an access token as well, thus requiring some sort of
work-around to including a GitHub Access Token in the source for the test cases.

in `test_orchestrate.py`

```Python
	# problematic test code containing a token
	chosen_arguments = [
		"--token",
		"TOKEN",
		"other args",
		"..."
	]
```

For now it would seem that the administrator might need to implement a keyserver
to solve this issue, though that is beyond the scope of our ability for this
feature.

## Teamwork and Reflection

For this feature implementation we encountered more difficulties with reasoning
out the solution to the problems we faced in a reasonable and secure way than
we did any actual programming challenge related to writing the code itself. This
is in part due to a critical miscommunication amongst the team members. The
miscommunication had to do with one member of the team working a little too
dilligently, and in the process stepping on the other group member's proverbial
toes. In this way one member of the team was able to contribute most of the ideas
that were discussed as a team individually to the repository, causing some degree
of dissatisfaction among the other member's views of their own individual
performance. Towards the end of the period, the member in question was asked to
stop working on the project temporarily so as to allow other members the
opportunity to contribute. 

Once the deadline had been reached, I found the experience wholly informative
and motivating for my own personal advancement in programming. I now better
understand working in software development teams to achieve a larger goal more
thoroughly, and I also was able to glean some key experience working on a
professional product.
