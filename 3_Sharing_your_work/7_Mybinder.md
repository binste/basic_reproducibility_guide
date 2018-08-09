---
title: Provide a free no-setup-needed computational environment
---
This is a topic I am really excited about. If you have used either Jupyter or R notebooks for your analysis, the repository is on GitHub, and you have created an environment.yml file as explained in the section on "Documentation", you now have the possibility to let everyone run and edit (the changes of course won't be saved) your notebooks online without any setup needed from there side. You might even have already used the service which makes this possible called [mybinder.org](https://mybinder.org/){:target="_blank"}, as the notebooks on [the official Jupyter website's 'Try' section](http://jupyter.org/try){:target="_blank"} which were mentioned in the beginning of this guide were powered by it. For further examples, see [this collection of example repositories](https://github.com/binder-examples/), which demonstrate many awesome things you can do with mybinder.

### Setting up mybinder.org
Head over to [mybinder.org](https://mybinder.org/){:target="_blank"} and follow the instructions posted on the site. The first time you initiate the service for your repository (and everytime there is a new commit), it will take a bit longer. Afterwards, the start up time will be much faster and visitors to your project can start running a notebook in seconds.

> Note: Should mybinder not be able to find your GitHub repository, you might still have it in "private" mode. Go to the settings page of your GitHub.com repository, scroll all the way down and click on the "Make this repository public" button.

#### Limited resources
However, if your analysis has parts, which need a lot of computational ressources, they might not run on mybinder as there are some limitations. Currently, users get at least 1GB of RAM, with a maximum of 2GB. You can find up-to-date information in [the official FAQ](https://mybinder.readthedocs.io/en/latest/faq.html#user-memory){:target="_blank"}.

One option to make at least some steps of the analysis, such as plotting figures, available on mybinder, you can run all the computational expensive operations beforehand and then provide the intermediate data sets on GitHub. For an example of this, see [![example](../figures/example_icon.png){:height="36px" width="36px"}](https://github.com/binste/chicago_safepassage_evaluation#figures-for-website-and-comparison-to-mcmillen-et-al-2017){:target="_blank"}, where the binder badge leads to a notebook where the creation of the figures can be rerun, based on intermediate data sets.

Another possibility for users, is to use [repo2docker](https://github.com/jupyter/repo2docker){:target="_blank"}, one of the tools behind mybinder.org. It will download the repository to the users computer and set up all the necessary dependencies in a separate environment. This frees others of the resource constraints of mybinder, but still allows for a very simple and straightforward reproduction of the results. For an example, see [![example](../figures/example_icon.png){:height="36px" width="36px"}](https://github.com/binste/chicago_safepassage_evaluation#run-analysis-on-your-own-machine){:target="_blank"}

For further information on mybinder.org, [the official documentation](https://mybinder.readthedocs.io/en/latest/#binder-documentation){:target="_blank"} is a great place to start.

You reached the end of this guide. If you want to learn more about reproducible research practices, check out ["Where to go next"](../Where_to_go_next.md).

[Table of content: "Sharing your work"](./index.md)