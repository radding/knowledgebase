.. Intro to git file

Git Quick Intro and Reference
=============================

Introduction
++++++++++++

Git is a version control system (VCS) used with programming projects, from individual projects up
to large scale enterprise development. Git is extremely useful both for individuals and teams and
is an industry standard tool; becoming familiar with it will benefit both your academic career and
also make yourself an attractive applicant to companies in industry.

This guide aims to familiarize you with git and to provide a quick reference for your use in the
future, as well as to supplement whatever knowledge you may have gained from classes.

So, to kick it off, the big question:

What is git for?
++++++++++++++++

Git, at its lowest level, is for keeping track of versions of a project in multiple locations,
allowing you to both share your project across multiple locations, and to keep those locations in
sync, while also allowing you to jump back to points in your project history.

Git also provides functionality for keeping different versions of the same project in parallel with
'branches', allowing you to preserve a functional copy of your project while you add features.

This is useful for several reasons:

 #. as you make changes to your project, potentially breaking things along the way, you always have
    access to older, working versions

 #. it allows you to keep your projects in sync across multiple computers with more functionality
    than a tool like Dropbox allows

 #. it makes it easy for your team to collaborate on a project together without stepping on
     each-others' toes.

 #. working on the same project across different computers is super easy--when you leave one
     computer, you commit and push your changes to the remote server. When you arrive at the other
     computer, you pull down the changes and resume work.


What is git not for?
++++++++++++++++++++

 #. Storing/versioning binary data. Git, having been designed as a programming tool, works best with
    plain text data. Its algorithms get very, very confused when handed binary data.

 #. Automatic synchronization of files; git is not automatic, you have to tell it what to commit
    and push and when.


Why should you use git?
+++++++++++++++++++++++

 #. Backup -- you don't have to worry about if your laptop suddenly dies; your data is stored
    remotely, accessible via git!

 #. Manually keeping versions -- Say goodbye to ``project5_actually_working_no_really-17.cpp``, let
    git handle keeping track of the different versions of your code!

 #. Sharing files with your team is a cakewalk -- no more shuffling emails back and forth with zips
    named ``team-project-3_edited_friday_by_jake-5.zip``, or passing around a flash drive, or two
    people working on it at once and having to manually integrate the changes later. Git can
    handle all of that!

 #. When you make a change at the last minute that breaks your code and you don't know how to fix
    it; reverting to a working version to hand it is only two commands away!


An Important Note
+++++++++++++++++

Git is not `GitHub <https://github.com>`__. Git is an open source application, GitHub is a website
that provides hosting for projects that use git, as well as many resources used to get started with
git. They are very different, and git has no official association with GitHub, beyond the fact that
GitHub employs many developers who contribute to the git open source project.

Getting Started
+++++++++++++++

There are a bazillion guides to getting started with git, all of them much better written than
anything we could produce. So, to get you started:

`an interactive guide to using git on the command line
<https://try.github.io/levels/1/challenges/4>`__.

`a step by step guide to your first GitHub repository
<https://guides.github.com/activities/hello-world/>`__.

`a guide to using branching in your projects
<https://guides.github.com/introduction/flow/>`__.
