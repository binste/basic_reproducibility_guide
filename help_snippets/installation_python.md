---
title: Installation instructions for Python
permalink: howto_install_python
layout: single
---
For Python I recommend downloading the Anaconda distribution. It includes the previously mentioned package manager conda as well as preinstalls many useful packages to do data analysis with Python. Note that the preinstalled packages only exist in your root environment. You will create a new environment for your project, where you can easily reinstall all of them.

## Download Anaconda
Head over to [the anaconda.com download page](https://www.anaconda.com/download){:target="_blank"} and get the Python 3.X version of Anaconda. When prompted for "Advanced Installation Options", make sure to enable "Add Anaconda to my PATH environment variable". Apart from that follow the installation instructions on screen. If you want, you can also install Microsoft Visual Studio Code (you'll see a prompt during the installation). I'll recommend you to do that if you don't have a good code editor yet (we'll come back to this later).

Don't use Python 2 as version 3 is the future of the Python programming language (see [python3statement.org](https://python3statement.org/){:target="_blank"} for additional information).

## Setting it all up
For each project, you want to set up a new environment inside conda. Think of it as a separate Python installation + packages. A package installed in an environment will not be available outside of it. This gives the advantage of no version conflicts between projects as well as easy export functions for your packages.

Run the following command in your terminal/command prompt. Replace `environment_name` with a name identifying your project.
```bash
conda create -n environment_name anaconda
```

As you added Anaconda to the end of the command, all the preinstalled packages that come with Anaconda will also be installed inside of this environment.

Activate the environment with:
```bash
source activate environment_name
```

Remember to always do this before working on your project.

After activating the newly created environment, run:
```bash
conda update --all
```
which updates all existing packages.

You are all set up and ready to go.

<a onclick="window.history.back()">Back</a>