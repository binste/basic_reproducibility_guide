---
title: Mybinder and repo2docker
permalink: /mybinder_repo2docker
layout: single
sidebar:
    nav: "guide"
header:
    overlay_image: /figures/rayi-christian-wicaksono-366-unsplash_cropped.jpg
    caption: "<small>Photo credit: <a href='https://unsplash.com/photos/6PF6DaiWz48' target='_blank'>Rayi Christian Wicaksono</a></small>"
---
I want to quickly introduce you to two awesome projects I stumbled upon while writing this guide and which I believe can really make a difference in making research accessible to a wider audience.

## Mybinder.org
If a project is hosted on GitHub, uses either a Jupyter or R notebook for the analysis, and a requirements file such as an `environment.yml` is provided, you now have the possibility to run this notebook online without any setup needed (changes of course won't be saved). That's really cool isn't it? You might have already used the service which makes this possible called [mybinder.org](https://mybinder.org/){:target="_blank"}, as the notebooks on [the official Jupyter website's 'Try' section](http://jupyter.org/try){:target="_blank"} which were mentioned in the beginning of this guide were powered by it. For further examples, see [this collection of example repositories](https://github.com/binder-examples/){:target="_blank"}, which demonstrate many awesome things you can do with mybinder.org.

However, if some parts of the analysis need a lot of computational resources, they might not run on mybinder as there are some limitations. Currently, users get at least 1GB of RAM, with a maximum of 2GB. You can find up-to-date information in [the official FAQ](https://mybinder.readthedocs.io/en/latest/faq.html#user-memory){:target="_blank"}.

If you tried out mybinder for your own analysis, don't forget to include a binder badge in your readme to let others know of this great possibility. For an example, see the end of the readme file in the [GitHub repository of the example project](https://github.com/binste/chicago_safepassage_evaluation/){:target="_blank"}.

## Repo2docker
One of the awesome tools behind mybinder.org is [repo2docker](https://github.com/jupyter/repo2docker){:target="_blank"}. If the same requirements are fulfilled as for mybinder.org, you can use it to download a GitHub repository to your computer and it will automatically set up all the necessary dependencies (using a requirements file such as `environment.yml` in the repository) in an isolated environment using [Docker](https://www.docker.com/){:target="_blank"} and start a Jupyter or R notebook in the end. Imagine it as a ultra-lightweight sort of virtual machine which will provide the exact same environment independent of the operating system of the user. You can also use this for sharing your own analysis by first testing it on your own computer and you can then be pretty assured that it will work on anyones if they have the necessary computational resources.

If you have tested that your analysis can be reproduced using repo2docker, it is of course also nice for others if you add step-by-step instructions on how to do this to your readme file. Again, for an example, see the end of the readme file in the [GitHub repository of the example project](https://github.com/binste/chicago_safepassage_evaluation/){:target="_blank"}.