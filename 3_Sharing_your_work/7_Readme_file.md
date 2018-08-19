---
title: Readme file
permalink: /sharing_your_work/readme_file
toc: false
header:
    overlay_image: /figures/rayi-christian-wicaksono-366-unsplash_cropped.jpg
    caption: "<small>Photo credit: <a href='https://unsplash.com/photos/6PF6DaiWz48' target='_blank'>Rayi Christian Wicaksono</a></small>"
---
{% include toc title="On this page" %}
There is one last thing I want to talk about, which is how to tie what we have looked at so far together in a readme file. The readme file will be the entry point for visitors to your project on GitHub. We will use it to explain what is contained in the repository and how this can be used to reproduce the results. You can write the readme file as a markdown (.md) or text (.txt) file, and it will be automatically detected by GitHub and displayed when someone visits your repository. In the following, I'll talk about what sections to include and what they should contain.

### Overview
At the top of the readme file, include a brief description of the project and its goals. You should not go into detail here on the methods and results used (ideally, you have written this down in some other place that you can link to now, like an academic paper, website, blog post, Jupyter notebook, etc. This section should simply provide some context and refer to the main written part of the research project.

### Software environment
To rerun your code and reproduce the results, others need to know what software you used (and the respective version numbers). You can specify this directly in the readme file in the form of a list or table, but there also exists a less tedious way. If you used the package manager conda and created a new environment for your project, as recommended in the section on the development environment, you can automatically create an environment file which contains detailed information on the R or Python version used as well as on all additional packages.

First, activate the environment as usual, then enter the following command in your terminal:
```bash
conda env export > environment.yml
```
This exports the specifications of your environment into a file called `environment.yml`. You can then add it to your repository on GitHub (like any other file), and it can be used by someone else to replicate your environment by downloading it and running:
```bash
conda env create -f environment.yml
```
The name of the copied environment will be by default the same one you have used and can be changed in the first line of the file.

Now you can simply mention in the readme file what programming language was used and then refer to the `environment.yml` file for details on the exact version and any additional packages. Don't forget to also add some information on your operating system.

**Note**: Your `environment.yml` file can become rather cluttered after you have installed many packages. Some of them will be system-specific dependencies which conda installed automatically and can prevent the installation of the environment on a different operating system. To make it easier for others, you might want to keep only the packages in the list which you actually installed and used in a script or notebook. You can then create a new environment from the edited file (first change the name of the environment) and rerun your analysis, to see if it still works.
{: .notice}

{% capture environment-yml %}
```yaml
name: speval
channels:
  - r
  - defaults
  - conda-forge
dependencies:
  - altair=2.1.0
  - feather-format=0.4.0
  - jupyter_contrib_core=0.3.3
  - jupyter_contrib_nbextensions=0.5.0
  - jupyter_nbextensions_configurator=0.4.0
  - vega=1.3.0
  - vega3=0.13.0
  - vega_datasets=0.5.0
  - geopandas=0.3.0
  - ipywidgets=7.2.1
  - jupyter=1.0.0
  - jupyter_client=5.2.3
  - jupyter_console=5.2.0
  - jupyter_core=4.4.0
  - jupyterlab=0.32.1
  - jupyterlab_launcher=0.10.5
  - matplotlib=2.2.2
  - msgpack-python=0.5.6
  - nbconvert=5.3.1
  - nbformat=4.4.0
  - notebook=5.5.0
  - numpy=1.14.5
  - pandas=0.23.1
  - kealib=1.4.7
  - pip=10.0.1
  - python=3.6.5
  - requests=2.19.1
  - scipy=1.1.0
  - seaborn=0.8.1
  - shapely=1.6.4
  - sqlalchemy=1.2.8
  - sqlite=3.23.1
  - tqdm=4.23.4
  - widgetsnbextension=3.2.1
  - xlrd=1.1.0
  - r-essentials=3.4.3
  - rpy2=2.9.1
  - pip:
    - cython==0.28.2
```
{% endcapture %}

<details>
<summary style="cursor:pointer">Show example environment.yml file</summary>
<small>
{{ environment-yml | markdownify }}
</small>
</details><br />

### Hardware
Depending on your analysis, there might be certain requirements regarding the hardware needed to run it. It is helpful if you specify this in the readme file, so that others can better assess if they are able to rerun the analysis on their machine. At a minimum, provide some information on the total amount of memory needed and if a graphic card is required.

### Data
In the section on "Documentation", you have created a document containing information about your raw data files. In your readme file you can now simply refer to this documentation and briefly summarize if data has to be bought, downloaded for free, or if it is already available in the GitHub repository.

### Order of execution
Another very important section in your readme file should provide information on what to run in what order to get from the raw data files described in the previous section to the final results of your research project. You can make a numbered list of files to run in order or describe it in words (eg. "First execute `.../0.0-bis-download_data.ipynb`, then ..., to reproduce all the main figures and tables in the paper"). To make this even easier for visitors, you can also provide a single script/notebook which runs all the necessary files in the correct order. This is extremely useful for reproducibility and also serves as sort of a documentation of your workflow. If you work with Jupyter notebooks, you can use a small example script that I wrote:

{% capture runscript %}
```python
"""Runs all Jupyter notebooks in given folders. Folder names (one or multiple)
can be passed as arguments to the script and can be provided relative to the
folder which contains all notebooks (e.g. "notebooks").
Notebooks are run with their enclosing folder as working directory.

Example
-------
If you have a folder structure as advised in the section on "Folder structure,"
you can put this script in the root folder of your project, and then if you wanted to run all Jupyter notebooks in "notebooks/0_prepare_data," you
type the following command in your terminal (with the directory
set to the root folder):

$ python run_ipynb.py 0_prepare_data
"""
import sys
from pathlib import Path

import nbformat
from nbconvert.preprocessors import CellExecutionError, ExecutePreprocessor


def validate_input(input_args):
    """Extracts folder names from passed arguments and makes sure that
    they are valid.

    Parameters
    ----------
    input_args : iterable
        All input arguments with the first one being the script name
        (i.e. sys.argv)

    Returns
    -------
    list
        All valid folder names
    """
    # Stops execution of script if no folders are given
    if len(input_args) == 1:
        raise Exception('You need to specify either one or multiple folders ' +
                        f'inside "./{str(notebooks_path)}" to run')
    # If folders are given, first check if they exist, else stop
    folders = [Path(f) for f in input_args[1:]]
    for f in folders:
        if not (notebooks_path / f).is_dir():
            raise Exception(
                f'Folder "{str(notebooks_path / f)}" does not exist.')
    return folders


def run_notebook(nb_wd, nb_path):
    """Runs a given notebook and saves it

    Executes the passed notebook with nb_wd as the working directory.
    If an error occurs during the execution, a message is raised to the user
    and the notebook is saved anyway, including the traceback.

    Parameters
    ----------
    nb_wd : Path or str
        Path to the folder which should be used as a working directory for
        the execution of the notebook

    nb_path : Path or str
        Full path to the notebook which should be run.

    Returns
    -------
    Nothing
    """
    if not isinstance(nb_wd, Path):
        nb_wd = Path(nb_wd)
    if not isinstance(nb_path, Path):
        nb_path = Path(nb_path)
    with nb_path.open() as f:
        nb = nbformat.read(f, as_version=nbformat.NO_CONVERT)

    # Configure notebook execution mode
    # Timeout = None means no restriction on runtime of cells
    ep = ExecutePreprocessor(timeout=None, kernel_name='python3')

    # The code for the following error handling is taken from the
    # official nbconvert documentation:
    # https://nbconvert.readthedocs.io/en/latest/execute_api.html
    try:
        # Run notebook
        out = ep.preprocess(nb, {'metadata': {'path': str(nb_wd)}})
    except CellExecutionError:
        out = None
        msg = f'Error executing the notebook "{str(nb_path)}".\n\n'
        msg += 'See the notebook for the traceback.\n'
        print(msg)
        raise
    finally:
        # Save it. Includes tracebacks should an error have occured.
        with nb_path.open('wt') as f:
            nbformat.write(nb, f)
    return


if __name__ == '__main__':
    # Set path to root directory of notebooks
    notebooks_path = Path('notebooks')
    # Validate input and get folder names
    folders = validate_input(sys.argv)
    # Get sorted list of all notebooks to run
    print('-' * 20)
    print('The following notebooks will be executed in order:')
    print('-' * 20)
    notebooks = []
    for f in folders:
        nb_found = sorted([
            x for x in (notebooks_path / f).iterdir() if x.suffix == '.ipynb'
        ])
        print('\n'.join(str(x) for x in nb_found))
        notebooks.append([f, nb_found])
        print('-' * 20)

    # Run notebooks
    for nb_wd, nb_paths in notebooks:
        for nb_p in nb_paths:
            print(f'Run {str(nb_p)}')
            run_notebook(notebooks_path / nb_wd, nb_p)
        print('-' * 20)
```
{% endcapture %}

<details>
  <summary style="cursor:pointer">Show script to run multiple Jupyter notebooks in order</summary>
  <small>
  {{ runscript | markdownify }}
  </small>
</details><br />

To see how this could look like, check out the readme file of the example project in the following:

{% capture readme-example %}
## Overview
This repository contains an example project for [A Basic Guide to Reproducible Research](https://binste.github.io/basic_reproducibility_guide/). It is an analysis of the effect of Chicago's Safe Passage program on crime counts. The program aims at keeping students safe on their way to school by posting civilian guards along various routes to the participating schools. The empirical approach chosen for the analysis follows one of the specifications in the working paper ["Do More Eyes on the Street Reduce Crime? Evidence from Chicago’s Safe Passage Program"](https://ignaciomsarmiento.github.io/assets/Safe_Passage_WP.pdf) by Daniel McMillen, Ignacio Sarmiento-Barbieri, and Ruchi Singh from June 22, 2017. The analysis aims to replicate some of their results. For more information on the replication, as well as an introduction on the topic and a summary of the analysis and the results, see the corresponding [website](https://binste.github.io/basic_reproducibility_guide/example_project/introduction).

This policy evaluation is part of my master thesis (2018) at the University of Zurich under the supervision of [Prof. Pietro Biroli](https://sites.google.com/site/pietrobiroli/home).

## Software environment
The data preparation was done in Python using Jupyter notebooks. R was used for the estimation of the Poisson regression. Details on the exact versions as well as additional packages can be found in the [`environment.yml`](environment.yml) file, which can also be used to recreate the conda environment used to create this analysis. As an operating system, macOS High Sierra 10.13.5 was used.

> **Note**: This repository is [repo2docker](https://github.com/jupyter/repo2docker) compatible.

## Hardware
The analysis was developed on a 3.1 GHz Intel Core i5 with 16 GB RAM. However, a reproduction of the results was tested and worked with only 10 GB RAM in a Docker container.

## Data
With the exception of the crime dataset, all raw data files are provided under `data/raw`. The crime dataset is over 1.5 GB and could therefore not be hosted on GitHub. However, the notebook in the folder `0_download_data` will by default download it for you and put it in the correct folder. The information on crimes should not change much for the years used in this analysis, and a download from the original source should work.

Some of the processed datasets are included. However, the dataset used to estimate the Poisson regressions (`est_df`) could, due to its size, not be uploaded to GitHub. It will be reproduced if you follow the order of execution explained in the following section.

For a detailed description of all data sources used, see the section "Data" in the [Appendix](https://github.com/binste/chicago_safepassage_evaluation/blob/master/reports/appendix/Appendix.pdf).

## Order of execution
To reconstruct the results starting out from the raw data, run all notebooks in the `notebooks` folders in the order of their numbering. No other scripts have to be run apart from the notebooks. The `src` folder contains scripts with only functions, which are imported by the notebooks.

Should you want to run the whole pipeline with one command, you can do this using the Python script `run_ipynb.py` which resides in the root folder of the project:
```bash
python run_ipynb.py 0_download_data 1_prepare_data 2_set_up_crime_database 3_match_datasets 4_combine_for_analysis 5_analysis
```
Note however, that this will not give you much of an indication on the progress of the computations, you'll only see the name of the notebook currently processed. This can take up to multiple hours, depending on your hardware.

## Analysis notebooks
As the analysis notebooks are probably of the most interest (they produce the main figures and results), the main two are briefly described in the following. They can be found in the folder `notebooks/5_analysis`.

| Notebook | Description |
| -------- | ----------- |
| `0.0-binste-estimation-poisson.ipynb` | Estimates all the Poisson regressions for both violent and property crimes and saves models as well as results into the folder `model`. [![nbviewer](https://img.shields.io/badge/render-nbviewer-orange.svg)](https://nbviewer.jupyter.org/github/binste/chicago_safepassage_evaluation/blob/master/notebooks/5_analysis/0.0-binste-estimation-poisson.ipynb)|
| `1.0-binste-analyze-crime-results-census-block-level.ipynb` | Replicates Figure 3, Figure A.2, Table 1, and Table 10 (column 3 and 7) from McMillen et al. (2017) and compares them to the originals. The notebook also produces additional figures for the website. [![Binder](https://mybinder.org/badge.svg)](https://mybinder.org/v2/gh/binste/chicago_safepassage_evaluation/master?filepath=notebooks%2F5_analysis%2F1.0-binste-analyze-crime-results-census-block-level.ipynb) [![nbviewer](https://img.shields.io/badge/render-nbviewer-orange.svg)](https://nbviewer.jupyter.org/github/binste/chicago_safepassage_evaluation/blob/master/notebooks/5_analysis/1.0-binste-analyze-crime-results-census-block-level.ipynb)|

> **Tip**: To view static versions of the Jupyter notebooks in your browser, you can paste their URL into [Jupyter nbviewer](http://nbviewer.jupyter.org/).

## How to run it
If you are not sure how to set up the software specified in `environment.yml` to rerun the analysis, you could do the following:

Download the repository as .zip file from GitHub and unpack it or clone it using:
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
{% endcapture %}

<details>
<summary style="cursor:pointer">Show readme file of example project</summary>
<small>
<div style="background-color:#eef7fa">
{{ readme-example | markdownify }}
</div>
</small>
</details><br />

>**Note**: Mybinder and repo2docker, both mentioned in the above readme, are two tools that facilitate the running of someone else's code stored in a GitHub repository (mybinder lets you run it in your browser, repo2docker on your own computer). If you're interested in these (pretty awesome!) tools, check out [this page](../mybinder_repo2docker) for more information.
{: .notice}

You have reached the end of this guide, and I hope it was of help to you. If you want to learn more about good practices, useful tools, and reproducible research in general, head over [to this list](../further_readings), which contains various blog posts, tutorials, and papers on the topic. If you're interested, take a closer look at the [example project](../example_project/introduction) and [the code and data behind it](https://github.com/binste/chicago_safepassage_evaluation/){:target="_blank"} to see how all of this could be implemented in a research project in practice.