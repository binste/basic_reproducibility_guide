---
title: Interesting stuff
permalink: /interesting_stuff
layout: single
sidebar:
    nav: "guide"
---
This page first presents in no particular order a list of interesting blog posts, tutorials, and papers by some of which this guide was inspired by. Afterwards, I want to quickly introduce you to two awesome projects I stumbled upon while writing this guide and which I believe can really make a difference in making research accessible to a wider audience.

## Blog posts, tutorials, papers
* [Wilson, Greg, et al. "Good enough practices in scientific computing." - PLoS computational biology 13.6, 2017](http://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1005510){:target="_blank"}
* [Orozco, Valérie, et al. "How To Make A Pie: Reproducible Research for Empirical Economics & Econometrics." - No. 18-933. Toulouse School of Economics (TSE), 2018](https://www.tse-fr.eu/publications/how-make-pie-reproducible-research-empirical-economics-econometrics){:target="_blank"}
* [Broman, Karl. "Initial steps toward reproducible research"](http://kbroman.org/steps2rr/){:target="_blank"}
* [Vanderplas, Jake. "Reproducible data analysis in Jupyter", 2017](https://jakevdp.github.io/blog/2017/03/03/reproducible-data-analysis-in-jupyter/){:target="_blank"}
* ["Reproducibility Guide", ropensci](http://ropensci.github.io/reproducibility-guide/sections/introduction/){:target="_blank"}
* ["Reproducible Research", CRAN Task View](https://cran.r-project.org/web/views/ReproducibleResearch.html){:target="_blank"}
* ["Data Science Cookiecutter Template"](http://drivendata.github.io/cookiecutter-data-science/){:target="_blank"}
* ["Reproducible Research", Coursera](https://www.coursera.org/learn/reproducible-research){:target="_blank"}
* [Bryan, Jennifer. "Excuse me, do you have a moment to talk about version control?," The American Statistician 72.1, 2018: 20-27](https://amstat.tandfonline.com/doi/abs/10.1080/00031305.2017.1399928?casa_token=FrgyUebyLgsAAAAA%3AhHUqKa4G2BdXeZ0TlB3m3WhvHX22EXBoCbFku0XfMiWLd2v_PAn8udQmw02zYDZXiiVl_LjVUw0D&#.W3kHZpMzbUI){:target="_blank"}
* [Ellis, Shannon E., and Jeffrey T. Leek. "How to share data for collaboration." The American Statistician 72.1, 2018: 53-57](https://amstat.tandfonline.com/doi/full/10.1080/00031305.2017.1375987?src=recsys#.W3kHl5MzbUI)
* [Kitzes, Justin, et al. "The Practice of Reproducible Research"](https://www.practicereproducibleresearch.org/){:target="_blank"}
* [Boettiger, Carl. "An introduction to Docker for reproducible research (with examples from the R environment)." ACM SIGOPS Operating Systems Review 49.1, 2015: 71-79](https://dl.acm.org/citation.cfm?id=2723882){:target="_blank"}
* [Stodden, Victoria, and Sheila Miguez. "Best Practices for Computational Science: Software Infrastructure and Environments for Reproducible and Extensible Research", 2013](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=2322276){:target="_blank"}
* ["Comparing Workflows (Git)", Atlassian.com](https://www.atlassian.com/git/tutorials/comparing-workflows){:target="_blank"}
* [Monroy, Tania S. "Down the rabbit hole. A 101 on reproducible workflows with Python", Youtube.com, 2018](https://www.youtube.com/watch?v=VAXCrDrAPo0){:target="_blank"}

## Mybinder.org
This is a topic I am really excited about. If a project is hosted on GitHub, uses either a Jupyter or R notebook for the analysis, and a requirements file such as an `environment.yml` is provided, you now have the possibility to run this notebook online without any setup needed (changes of course won't be saved). That's really cool isn't it? You might have already used the service which makes this possible called [mybinder.org](https://mybinder.org/){:target="_blank"}, as the notebooks on [the official Jupyter website's 'Try' section](http://jupyter.org/try){:target="_blank"} which were mentioned in the beginning of this guide were powered by it. For further examples, see [this collection of example repositories](https://github.com/binder-examples/){:target="_blank"}, which demonstrate many awesome things you can do with mybinder.org.

However, if some parts of the analysis need a lot of computational resources, they might not run on mybinder as there are some limitations. Currently, users get at least 1GB of RAM, with a maximum of 2GB. You can find up-to-date information in [the official FAQ](https://mybinder.readthedocs.io/en/latest/faq.html#user-memory){:target="_blank"}.

If you tried out mybinder for your own analysis, don't forget to include a binder badge in your readme to let others know of this great possibility. For an example, see the end of the readme file in the [GitHub repository of the example project](https://github.com/binste/chicago_safepassage_evaluation/).

## Repo2docker
One of the awesome tools behind mybinder.org is [repo2docker](https://github.com/jupyter/repo2docker){:target="_blank"}. If the same requirements are fulfilled as for mybinder.org, you can use it to download a GitHub repository to your computer and it will automatically set up all the necessary dependencies (using a requirements file such as `environment.yml` in the repository) in an isolated environment using [Docker](https://www.docker.com/){:target="_blank"} and start a Jupyter or R notebook in the end. Imagine it as a ultra-lightweight sort of virtual machine which will provide the exact same environment independent of the operating system of the user. You can also use this for sharing your own analysis by first testing it on your own computer and you can then be pretty assured that it will work on anyones if they have the necessary computational resources.