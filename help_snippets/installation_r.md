---
title: Installation instructions for R
permalink: howto_install_r
---
If you only want to use R, you might not want the preinstalled Python packages that come with Anaconda. Instead, download [Miniconda](https://conda.io/miniconda.html){:target="_blank"}. It contains the conda package manager but without the Python packages. Still you need to choose the default version of Python when downloading Miniconda. Go with Python 3.X. Don't worry, you'll never need to do anything in Python, we'll only use the package manager.

## Setting it up
Create a new environment for your project
```bash
conda create -n environment_name
```

Installs R + Jupyter Kernel + [a lot of useful packages](https://docs.anaconda.com/anaconda/packages/r-language-pkg-docs#){:target="_blank"}
```bash
conda install -c r r-essentials
```
This should get you up and running with some very useful packages for doing data analysis such as "tidyverse".

Activate the environment with:
```bash
source activate environment_name
```
Remember to always do this before working on your project.

After activating the newly created environment, run:
```bash
conda update --all
```

Continue with the installation of RStudio, a very good integrated development environment (IDE) for programming in R.
```bash
conda install -c r rstudio
```

[RStudio](https://www.rstudio.com/){:target="_blank"} also provides R Notebooks as a viable alternative to Jupyter notebooks. Feel free to choose whatever you prefer if using R. For the rest of this tutorial, it does not matter what you choose.

You are all set up and ready to go.

<a onclick="window.history.back()">Back</a>