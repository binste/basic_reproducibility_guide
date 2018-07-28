---
title: Programming environment
---
* TOC
{:toc}

### Conda - Package manager
If you decided on doing your project in Python or R, I recommend to use the free package manager conda. It offers easy installation of most of the libraries you'll ever need. Furthermore it allows to create separate environments (i.e. installations of Python or R) for each of your projects. This helps in avoiding version conflicts of packages between projects, as well as makes it easier to share the specifications of your programming environment with others. Forget about making a list of all packages and their version numbers, conda can do this for you.

* [Installation instructions for Python](../help_snippets/installation_python.md)
* [Installation instructions for R](../help_snippets/installation_r.md)

### Notebooks
After you've made yourself familiar with the programming language of your choice, let us quickly talk about an important aspect of the workflow presented in this guide. Instead of writing your code into scripts such as .py or .R and the corresponding figures and equations in some LaTeX document far far way, you'll learn about so called notebooks with the most prominent proponent being *Jupyter notebooks*. They allow you to integrate code as well as visualizations, mathematical equations and narrative text (using markdown or even latex), all in one document. This is extremely convenient when doing a data analysis, as it allows for an iterative exploration of your data as well as a rich-formatted documentation right next to it. You can even export the notebooks as .html, .pdf, .tex, etc. These files can then be used as reports to send to other people (you can even hide the code and only show the output).

A live demo will probably give you a better idea of what notebooks are capable of. Head over to the [official Jupyter website's 'Try' section](http://jupyter.org/try){:target="_blank"}. to try out example notebooks for Python, R, Julia, and C++, directly runnable in your browser without any installation! Python users should also check out[the discovery of gravitational waves by the LIGO collaboration](https://mybinder.org/v2/gh/minrk/ligo-binder/master?filepath=index.ipynb). For R users, [R notebooks by RStudio](https://rmarkdown.rstudio.com/r_notebooks) are a great alternative.

Jupyter notebooks support not only Python and R but many other languages such as Stata, Julia, Scala, C++, or Matlab. If you use one of the former, head over to [this list of all available languages in Jupyter](https://github.com/jupyter/jupyter/wiki/Jupyter-kernels) for further information on how to set them up.


If you have followed the installation instructions for Python or R using conda, you already have Jupyter notebooks preinstalled. Just type
```bash
jupyter notebook
```
into your console. Otherwise, head over to [the official Jupyter installation guide](http://jupyter.org/install.html){:target="_blank"}.

There are many good beginner tutorials on Jupyter out there, such as [this one from DataQuest](https://www.dataquest.io/blog/jupyter-notebook-tutorial/){:target="_blank"}.

As a side note, there also exists [Jupyter lab](http://jupyterlab.readthedocs.io/en/latest/){:target="_blank"}. It contains many cool features in addition to the notebook functionality, such as a code editor and a .csv file viewer. However, it does not yet has such a wide ecosystem of extensions as the notebooks but it is certainly worth a look.

### Code editor
Even if you follow a notebook-based workflow, you'll end up needing a code editor sooner or later, for example when putting functions into separate scripts to declutter your notebooks, but more on this later.

Personally, I use [Microsoft Visual Studio Code](https://code.visualstudio.com/){:target="_blank"} as it offers a very good and easily installable Python integration (you only need to install the official Python extension) as well as many other desirable features. Plus it is free! It can also handle R scripts and many other languages. This website was written as markdown files in VS Code!

Other good alternatives include [Atom](https://atom.io/){:target="_blank"} and [Sublime Text](https://www.sublimetext.com/){:target="_blank"}.

[Back to the table of content](./index.md)