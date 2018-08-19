---
title: XXX
permalink: /repo2docker_mybinder
header:
    overlay_image: /figures/rayi-christian-wicaksono-366-unsplash_cropped.jpg
    caption: "<small>Photo credit: <a href='https://unsplash.com/photos/6PF6DaiWz48' target='_blank'>Rayi Christian Wicaksono</a></small>"
---
## How to run it
If you want to rerun this analysis, a good option might be to clone the repository:
```bash
git clone https://github.com/binste/chicago_safepassage_evaluation
```
and then install and activate the conda environment by running:
```bash
conda env create -f environment.yml
conda activate speval
```
Now start a Jupyter notebook server in the root directory of the project:
```bash
jupyter notebook
```
See [Order of execution](#order-of-execution) on how to proceed.

##### Run it in a Docker container


##### Run it online for free with no setup needed





### Where and how to run it?
#### Compare results to McMillen et al. (2017) and replicate figures from website
By clicking on the badge below, you can compare the results to the ones of McMillen et al. (2017) and replicate the figures used on the website of the analysis, all directly in your browser without any setup required.

[![Binder](https://mybinder.org/badge.svg)](https://mybinder.org/v2/gh/binste/chicago_safepassage_evaluation/master?filepath=notebooks%2F5_analysis%2F1.0-binste-analyze-crime-results-census-block-level.ipynb)

For a static version of the same Jupyter notebook, click on

[![nbviewer](https://img.shields.io/badge/render-nbviewer-orange.svg)](https://nbviewer.jupyter.org/github/binste/chicago_safepassage_evaluation/blob/master/notebooks/5_analysis/1.0-binste-analyze-crime-results-census-block-level.ipynb)

#### Run complete analysis on your own machine
Due to resource constraints on the above used service called mybinder.org, you can not run the estimations of the Poisson regression or even start out from the raw data files in your browser. In the following I will present two options which should allow you to do this as easily as possible.

##### Set up a conda environment
XXX

This approach should give you the exact same Python and R version as well as the same versions of the main packages used. However, system dependencies might differ and I was not able to test it on a Windows machine. Should you experience any problem with this, you might want to try out the next approach.

##### Run it in a Docker container
Should you have problems with the above approach due to your operating system, you can also run the analysis in a tested and operating-system-independent environment (using Docker). In the following, I will explain all the necessary steps and use the amazing tool repo2docker, which will copy the repository to your own computer and setup everything for you.

1. Install the [Docker Community Edition](https://store.docker.com/search?type=edition&offering=community) for your operating system
2. Set the available memory for Docker to 4GB and the number of CPU cores to 2.
    * On Mac this can be set by clicking on the Docker symbol in the status bar -> Preferences -> Advanced
3. Install repo2docker from source to get the latest version:
    ```bash
    git clone https://github.com/jupyter/repo2docker.git
    cd repo2docker
    pip install -e .
    ```
4. Build and launch Docker image of GitHub repository:
    ```bash
    jupyter-repo2docker https://github.com/binste/chicago_safepassage_evaluation
    ```
5. After it run through, there is an URL, which will lead you to a running Jupyter notebook server. There is currently a bug with Jupyter notebooks and Docker, where the displayed URL might not work without a slight modification. To fix it, change the host name before the port to `127.0.0.1`. Example: `http://d2f78b8191fd:55484/?token=...` becomes `http://127.0.0.1:55484/?token=...`.

See [Order of execution](#order-of-execution) on how to proceed.
