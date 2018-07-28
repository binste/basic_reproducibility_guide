---
title: Provide a free no-setup-needed computational environment
---
This is something I am really excited about. If you have used either Jupyter or R notebooks for your analysis, the repository is on GitHub, and you have created an environment.yml file as previously explained, there exists a really easy, cool, and free way to let everyone run these notebooks online without any setup from there side. Others can then not only rerun your analysis but also expand on it and try out new things. You might even have already used this service called [mybinder.org](https://mybinder.org/){:target="_blank"} if you clicked on the [Jupyter Try link](http://jupyter.org/try){:target="_blank"} in the beginning of this tutorial. A prominent example is the {:target="_blank"}. Just click on the `launch binder` batch on the GitHub repository and you'll be able to rerun their analysis in your browser.

### Setting up mybinder.org
Head over to [mybinder.org](https://mybinder.org/){:target="_blank"} and follow the instructions there. The first time you launch the service (and everytime there is a new commit), it will take a bit longer. Afterwards, the start up time will be much faster.

#### Limited resources
However, there are some limitations on how much resources you can use on mybinder.org. You can find up-to-date information [here](https://mybinder.readthedocs.io/en/latest/faq.html#user-memory){:target="_blank"}. Depending on your analysis, you might therefore not be able to let others run all of your notebooks directly in the browser. If you can provide intermediate data sets, you can do all the computational expensive operations beforehand and let others run on a final data set.

Another option for others is to use [repo2docker](https://github.com/jupyter/repo2docker){:target="_blank"}, one of the tools behind mybinder.org. It allows very much the same thing as mybinder.org, except that it will download the repository to the users computer and runs it their. Still the setup will be automatic. This frees you of the resource constraints of mybinder.

For further information on mybinder.org, the [official documentation](https://mybinder.readthedocs.io/en/latest/#binder-documentation){:target="_blank"} is a great place to start. It contains [sample repositories](https://mybinder.readthedocs.io/en/latest/#sample-repositories){:target="_blank"} as well as a [FAQ](https://mybinder.readthedocs.io/en/latest/faq.html){:target="_blank"} section.

## Publish repository on GitHub
You have finished your analysis, added a LICENSE file, and maybe even added a mybinder badge to the README file? Don't forget to make your repository accessible for everyone. Go to the settings page of your GitHub.com repository, scroll all the way down and click on the "Make this repository public" button.

[Back to the table of content](./index.md)