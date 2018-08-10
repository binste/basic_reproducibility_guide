---
title: Programming environment
permalink: /preparation/programming_environment
---
## Package manager
With new versions being released, naturally, software changes its behaviour. Even though this might be desired, it can make reproducing someone elses work a lot harder, if you don't have access to the exact same software as was used in the analysis. Furthermore, if you update a tool for a project, this might break some code in another one, as the latter might depend on the old functionality of the software.

Both of these issues can be solved easily, if you take them into consideration when setting up your programming environment. The key is to create a fresh installation of the software you use for a project.

To do this, if you decided on doing your project in Python or R, I highly recommend to install them as well as additional packages, using the package manager conda. You can find the corresponding installation instructions below:

* [Installation instructions for Python](../howto_install_python)
* [Installation instructions for R](../howto_install_r)

Conda not only greatly simplifies the installation of most of the packages you'll ever need, it also makes it possible to create the before mentioned separate environments for each of your projects. At the start of a project, you will create a fresh installation of Python or R in a new folder (see the corresponding link above on how it works) and all packages which will be needed for the analysis, can be subsequently installed there too. Don't worry, this is much less work then you might initially think.

When working on the project, you will always use the corresponding environment (read: Python or R installation). If you then update a package to get some new functionality, this will only happen for the chosen project and it will not interfer with other environments and therefore projects in any way. An added benefit is, that you can easily export the specifications of this environment to a file, which others then can use to recreate the exact same environment, consisting of the same Python or R as well as package versions. More on this in the section on "Documentation".

## Notebooks
You have now set up your programming environment and are ready to go. When doing a data analysis, you end up producing a lot of output in form of figures, text, tables, etc. as well as writing down your findings. Furthermore, you might not want to write whole scripts and execute them, but want to interactively execute commands and then inspect the output.

Wouldn't it be nice to not have to write your code into scripts such as .py or .R and put the corresponding figures and equations in some LaTeX or Word document far far way? This is were so called *notebooks* shine. They allow you to integrate code as well as visualizations, mathematical equations and narrative text (using markdown or even latex), all in one document. This allows for an iterative exploration of your data as well as a rich-formatted documentation right next to it. You can even export the notebooks as .html, .pdf, .tex, etc. Notebooks will be an important aspect of the workflow presented in this guide, with the most prominent proponent being *Jupyter notebooks*.

A live demo will probably give you a better idea of what notebooks are. Head over to the [official Jupyter website's 'Try' section](http://jupyter.org/try){:target="_blank"}. to try out example notebooks for Python, R, Julia, and C++, directly runnable in your browser without any installation! Python users should furthermore check out [the discovery of gravitational waves by the LIGO collaboration](https://mybinder.org/v2/gh/minrk/ligo-binder/master?filepath=index.ipynb). For R users, [R notebooks by RStudio](https://rmarkdown.rstudio.com/r_notebooks) are also a great option.

Jupyter notebooks support way more than the previously mentioned languages, and you can do your analysis in Stata, Matlab and dozens of more languages. Head over to [this list of all available languages in Jupyter](https://github.com/jupyter/jupyter/wiki/Jupyter-kernels) for further information on how to set them up.

If you have followed the installation instructions for Python, you already have Jupyter notebooks preinstalled. Just type
```bash
jupyter notebook
```
into your console. Otherwise, head over to [the official Jupyter installation guide](http://jupyter.org/install.html){:target="_blank"}.

There are many good beginner tutorials on Jupyter out there, such as [this one from DataQuest](https://www.dataquest.io/blog/jupyter-notebook-tutorial/){:target="_blank"}.

**Note**: There also exists [Jupyter lab](http://jupyterlab.readthedocs.io/en/latest/){:target="_blank"}. It contains all of the functions of Jupyter notebooks plus many additional cool features and will eventually be the successor of the notebooks. It is certainly worth checking out. However, you are able to switch easily between the two, even on already existing documents, and it does therefore not matter much with what you start.
{: .notice}

## Code editor
Even if you follow a notebook-based workflow, you'll end up needing a code editor sooner or later, for example when putting functions into separate scripts to declutter your notebooks, but more on this in the section on "Doing the work".

Personally, I use [Microsoft Visual Studio Code](https://code.visualstudio.com/){:target="_blank"}, but other good alternatives include [Atom](https://atom.io/){:target="_blank"} and [Sublime Text](https://www.sublimetext.com/){:target="_blank"}.

**Note**: Microsoft Visual Studio Code offers a very good and easily installable Python integration (you only need to install the official Python extension) as well as many other desirable features. It can also handle R scripts and many other languages. This website was written as markdown files in VS Code!
{: .notice}

You're programming environment should now be set up in a way, which not only is convenient for you, but is highly favourable for reproducible research. [Next, we will create a well structured project folder to keep everything well organised from the beginning.](./folder_structure)
