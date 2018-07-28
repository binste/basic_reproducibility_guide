---
title: Set up version control
---
* TOC
{:toc}

A prominent option for a version control system is [Git](https://git-scm.com/){:target="_blank"}. It allows to easily keep track of all the changes over time you or your collaboraters make to text based files (text documents, code files, etc.). Although this might be not be per se a requirement for reproducibility, it most certainly helps in achieving it. It let's you try out different versions of an analysis and still revert back to a previous version and recover the code that produced the main results in the first place. Furthermore, it can save yourself a lot of time down the line when you want to track down a bug and you are not sure when it got introduced or how the code looked before you changed that one buggy function.

Additionally to the local copy of your project, you can host it online, using a free web service such as [GitHub](https://www.github.com){:target="_blank"}. This can serve as a backup, but also allows for easier collaboration with others.

Git and GitHub offer a lot of functionality, which might feel overwhelming at first. Just focus on the basics (see the tutorials mentioned below) and you'll get up and running with version control very quickly.

## Installation
Follow the installation guides linked in this [DataCamp Tutorial](https://www.datacamp.com/community/tutorials/setup-data-science-environment#Git){:target="_blank"}.

If you use Jupyter notebooks, also install nbdime via the following command, which allows git to display the difference between two versions in a better readable way.
```bash
pip install nbdime
```
Now you need to set up the git integration with
```bash
nbdime config-git --enable --global
```
Thats it. Git now is Jupyter notebook compatible. See the [nbdime documentation](https://nbdime.readthedocs.io/en/latest/){:target="_blank"} for further information if you're interested.

Now you are ready to put your first project under version control, or in other words: Create your first repository.

>"A repository, or Git project, encompasses the entire collection of files and folders associated with a project, along with each file’s revision history." - [Git Handbook GitHub Guides](https://guides.github.com/introduction/git-handbook/){:target="_blank"}

So think of it as your project folder, which you want to put in version control. Git is especially useful for text-based files, i.e. code, .tex/.md reports, etc.

Next, head over to [GitHub.com](https://github.com/){:target="_blank"} and make yourself an account. It's completely free. You will be able to host your repositories there. Don't worry, you can set a repository to "private", such that only you can see it.

## Command line vs. GitHub Desktop
You can either use Git together with GitHub over the command line or using a graphical user interface (GUI) such as [GitHub Desktop](https://desktop.github.com/){:target="_blank"}. Compared to the later, the command line offers more flexibility in terms of what you can do as well as where - think of working remotely over command line on a server. I highly recommend the free DataCamp course [Introduction to Git for Data Science](https://www.datacamp.com/courses/introduction-to-git-for-data-science){:target="_blank"}. Should you plan on doing a smaller project without using Git for collaboration, you're even fine with watching just the first part called "Basic workflow" as a starter. To connect command line Git with GitHub see the [Set up git](https://help.github.com/articles/set-up-git/){:target="_blank"} tutorial.

If you opt for GitHub Desktop, you can find all informations for an easy setup and user experience in the official guides [Getting Started with GitHub Desktop](https://help.github.com/desktop/guides/getting-started-with-github-desktop/){:target="_blank"} and [Contributing to projects with GitHub Desktop](https://help.github.com/desktop/guides/contributing-to-projects/){:target="_blank"}, which also shows how to add your own project to GitHub using the GUI.

## Data
If you have the permission to do publish your raw data you can also put it into version control and upload it to GitHub. However, the single files must be below 100MB and the total repository should stay below 1GB. Should you not be able to upload your raw data (also for legal reasons), you can find tips on how to handle this in the section on documenting your project.

[Back to the table of content](./index.md)