---
title: Set up version control
permalink: /preparation/version_control
---
Putting your project under version control can greatly help you make your project reproducible. It let's you try out different versions of an analysis and still revert back to a previous version and recover the code that produced the main results in the first place. Furthermore, it can save yourself a lot of time down the line when you want to track down a bug and you are not sure when it got introduced or how the code looked before you changed that one buggy function.

A prominent option for a version control system is [Git](https://git-scm.com/){:target="_blank"}. It allows to easily keep track of all the changes over time you or your collaboraters make to text based files (text documents, code files, etc.).

The free web service [GitHub](https://www.github.com){:target="_blank"} can host projects, which are versioned using Git, online and includes many useful tools for collaboration with others. GitHub will be the platform, which we will use in the end to share our project with the world. However, while working on it you can also set the project to private mode, which will prevent others from accessing it until you make it public.

Git and GitHub offer a lot of functionality, which might feel overwhelming at first. Just focus on the basics (see the tutorials mentioned below) and you'll get up and running with version control very quickly.

## Installation
Follow the installation guides linked in this [DataCamp Tutorial](https://www.datacamp.com/community/tutorials/setup-data-science-environment#Git){:target="_blank"}.

If you use Jupyter notebooks, also install nbdime via the following command, which allows git to display the difference between two versions of a notebook in an easier understandable way.
```bash
conda install -c conda-forge nbdime
```
Now you need to set up the git integration with
```bash
nbdime config-git --enable --global
```
That's it. Git now is Jupyter notebook compatible. See the [nbdime documentation](https://nbdime.readthedocs.io/en/latest/){:target="_blank"} for further information if you're interested.

Before you go on, we might need to clarify first the term of a *repository*:

>"A repository, or Git project, encompasses the entire collection of files and folders associated with a project, along with each file’s revision history." - [Git Handbook GitHub Guides](https://guides.github.com/introduction/git-handbook/){:target="_blank"}

Think of it as your project folder, which you put under version control.

## Command line vs. GitHub Desktop
Now, you are ready to put your first project under version control and create your first repository. To interact with Git, you have two options. You can either interact with Git over the command line or using a graphical user interface (GUI) such as [GitHub Desktop](https://desktop.github.com/){:target="_blank"}. Compared to the later, the command line offers more flexibility in terms of what you can do as well as where - think of working remotely over command line on a server.

For an introduction to the command line interface, I highly recommend the free DataCamp course [Introduction to Git for Data Science](https://www.datacamp.com/courses/introduction-to-git-for-data-science){:target="_blank"}. Should you plan on doing a smaller project without using Git for collaboration, you're even fine with watching just the first part called "Basic workflow". To connect Git to GitHub over the command line, see the [Set up git](https://help.github.com/articles/set-up-git/){:target="_blank"} tutorial.

If you opt for GitHub Desktop, you can find all informations for an easy setup and user experience in the official guides [Getting Started with GitHub Desktop](https://help.github.com/desktop/guides/getting-started-with-github-desktop/){:target="_blank"} and [Contributing to projects with GitHub Desktop](https://help.github.com/desktop/guides/contributing-to-projects/){:target="_blank"}, which also shows how to add your own project to GitHub using the GUI.

## Data
If you have the permission to publish your raw data files, you can also put them into version control and even upload to GitHub if they fulfill certain size requirements. Single files must be below 100MB and the total repository should stay below 1GB. Should you not be able to upload your raw data (also for legal reasons), make sure to thoroughly document what data you used. More on this in the upcoming section on "Documentation".

{% comment %}
Include link to example project?
Include information on what to do if sizes are above that?
{% endcomment %}

You now already have set up your programming environment, a well organised folder structure, as well as a version control system which will be of immense value. Maybe you have already started to clean your data in some fresh notebooks. [It is then time, to talk about documentation, such that your codebase stays tidy and you have all the important information in the right place](../during_the_analysis/documentation).

[Table of content: "Preparation"](.)