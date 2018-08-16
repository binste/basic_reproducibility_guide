---
title: Writing good documentation
permalink: /during_the_analysis/documentation
---
Writing good and up-to-date documentation is critical for others to be able to quickly understand your project. It is also essential for yourself to later on understand what you did and especially why. It is a good habit to start right from the beginning and to keep updating your documentations whenever something changes.

## README file
Always create a README file in the root directory of your project. This can be a markdown (.md) or text (.txt) file. It will be the entry point for visitors to your project and should at first give them a brief description of the project, it's goals, and provide some context. If you have a corresponding website to the project, which further describes it, make sure to link it here. The following sections will go into details on what else you should include in your README file.

**Note**: Your readme file will also be automatically detected by GitHub (and if it is written as a Markdown file also rendered) and displayed when someone visits your GitHub repository.
{: .notice}

{% capture readme-example %}
## Overview
This repository contains an analysis of the effect of Chicago's Safe Passage program on crime counts. The program aims at keeping students safe on their way to school by posting civilian guards along various routes to the participating schools. The empirical approach chosen for the analysis follows one of the specifications in the working paper ["Do More Eyes on the Street Reduce Crime? Evidence from Chicago’s Safe Passage Program"](https://ignaciomsarmiento.github.io/assets/Safe_Passage_WP.pdf) by Daniel McMillen, Ignacio Sarmiento-Barbieri, and Ruchi Singh from June 22, 2017, and is an attempt to replicate their findings. For more information on the replication, as well as an introduction on the topic and a summary of the analysis and the results, see the corresponding [website](https://binste.github.io/chicago_safepassage_evaluation/).

This policy evaluation is one of two parts of my master thesis (2018) at the University of Zurich under the supervision of [Prof. Pietro Biroli](https://sites.google.com/site/pietrobiroli/home). The second one is [A Basic Guide to Reproducible Research](https://binste.github.io/basic_reproducibility_guide/), where this analysis serves as an example.

## Replicate analysis
### Compare results to McMillen et al. (2017) and replicate figures from website
By clicking on the badge below, you can compare the results to the ones of McMillen et al. (2017) and replicate the figures used on the website  of the analysis, all directly in your browser without any setup required.

[![Binder](https://mybinder.org/badge.svg)](https://mybinder.org/v2/gh/binste/chicago_safepassage_evaluation/master?filepath=notebooks%2F5_analysis%2F1.0-binste-analyze-crime-results-census-block-level.ipynb)

For a static version of the same Jupyter notebook, click on

[![nbviewer](https://img.shields.io/badge/render-nbviewer-orange.svg)](https://nbviewer.jupyter.org/github/binste/chicago_safepassage_evaluation/blob/master/notebooks/5_analysis/1.0-binste-analyze-crime-results-census-block-level.ipynb)

### Run analysis on your own machine
Due to resource constraints on the above used service called mybinder.org, you can not run the estimations of the Poisson regression or even start out from the raw data files in your browser. If you want to do that, you need to do it on your own machine. To do it, you might want to choose one of the following two options, depending on your knowledge and your goal.

#### Set up a conda environment
If you want to continue working on this project, your best option might be to clone the repository:
```bash
git clone https://github.com/binste/chicago_safepassage_evaluation
```
and then install and activate the conda environment by running:
```bash
conda env create -f environment.yml
source activate speval
```
Now start a Jupyter notebook server in the root directory of the project:
```bash
jupyter notebook
```
See [Order of execution](#order-of-execution) on how to proceed.

This approach should give you the exact same Python and R version as well as the same versions of the main packages used. However, system dependencies might differ and I was not able to test it on a Windows machine. Should you experience any problem with this, you might want to try out the next approach.

#### Run it in a Docker container
If you want to rerun the analysis in an isolated and tested environment, you can use the amazing tool repo2docker. It will copy the repository on your own computer and setup everything for you in an isolated and OS independent environment (using Docker). However, if you are not familiar with Docker, it is not straightforward to save any changes you make to the files.

1. Install the [Docker Community Edition](https://store.docker.com/search?type=edition&offering=community) for your operating system
2. Set the available memory for Docker to 4GB.
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

### Data
For a detailed description of all data sources used, see the section "Data" in the Appendix (XXX).

With the exception of the crime dataset, all raw data files are provided under `data/raw`. The crime dataset is over 1.5 GB and could therefore not be hosted on GitHub. However, the notebook in the folder `0_download_data` will by default download it for you and put it in the correct folder. The information on crimes should not change much for the years used in this analysis and therefore a download from the original source should work.

Some of the processed datasets are included. However, the dataset used to estimate the Poisson regressions (`est_df`) could, due to its size, not be uploaded to GitHub. It will be reproduced if you follow the order of execution explained in the following.

### Order of execution
To reconstruct the results starting out from the raw data, run all notebooks in the `notebooks` folders in order of their numbering. No other scripts have to be run apart from the notebooks. The `src` folder does contain scripts with only functions, which are imported by the notebooks.

Should you want to run the whole pipeline with one command you can do this using the Python script `run_ipynb.py` which resides in the root folder of the project. Note however, that this will not give you much of an indication on the progress of the computations, you'll only see the name of the notebook currently processed. In the "Home" view of Jupyter notebook (where you can open files), click on the top right on "New" -> "Terminal". Now you should be able to run the following command to rerun the whole analysis from the raw data files to the end results:

```bash
python run_ipynb.py 0_download_data 1_prepare_data 2_crime_database 3_match 4_combine_for_analysis 5_analysis
```

This can take up to multiple hours, depending on your hardware.

### Analysis notebooks
As the analysis notebooks are probably of the most interest, as they produce the main figures and results, the main two are briefly described in the following. They can be found in the folder `notebooks/5_analysis`.

| Notebook | Description |
| -------- | ----------- |
| `0.0-binste-estimation-poisson.ipynb` | Estimates all the Poisson regressions for both violent and property crimes and saves models as well as results into the folder `model`.
| `1.0-binste-analyze-crime-results-census-block-level.ipynb` | Replicates Figure 3, Figure A.2, Table 1, and Table 10 (column 3 and 7) from McMillen et al. (2017) and compares them to the originals. The notebook also produces additional figures for the website. |

> **Tip**: To view static versions of the Jupyter notebooks in your browser, you can paste their url into [Jupyter nbviewer](http://nbviewer.jupyter.org/).

### Hardware
I used a MacBook Pro (macOS High Sierra 10.13.5) 3.1 GHz Intel Core i5 with 16 GB RAM to develop the project. No graphic card is needed. The end results were tested and replicated in a Docker container, as explained [above](#run-it-in-a-docker-container).
{% endcapture %}

<details>
<summary>Show README file of example project</summary>
<small>
<div style="background-color:#eef7fa;border-radius:4px">
{{ readme-example | markdownify }}
</div>
</small>
</details>

### Data and code "pipeline"
Another section in your README file should provide information on how to reproduce the results. You can make a numbered list of files to run in order or describe it (eg. "First execute `.../0.0-bis-download_data.ipynb`, then ..., to reproduce all the main figures and tables in the paper"). It is important that you include all the necessary steps starting from the raw data files up to the end results. To make reproducing the main tables and figures easier for visitors, you can also provide a single script/notebook which runs all the necessary files in the correct order to get from the raw data to the final results. This is extremely useful for reproducibility and also serves as sort of a documentation of your workflow. If you work with Jupyter notebooks, you can use a small script that I wrote. Click on the following link for the code and an example on how to use it:

{% capture runscript %}
```python
"""Runs all Jupyter notebooks in given folders. Folder names (one or multiple)
can be passed as arguments to the script and can be provided relative to the
folder which contains all notebooks (e.g. "notebooks").
Notebooks are run with their enclosing folder as working directory.

Example
-------
If you have a folder structure as adviced in the section on "Folder structure",
you can put this script in the root folder of your project, and then if you
would want to run all Jupyter notebooks in "notebooks/0_prepare_data", you
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
  <summary>Show script to run multiple Jupyter notebooks in order</summary>
  <small>
  {{ runscript | markdownify }}
  </small>
</details>

### Software environment
To reproduce your results, others need to know what software and additional packages you used (and the respective version numbers). You can specify this in the README file. Again, there is a way to greatly simplify this process. If you used the package manager conda and created a new environment for your project, you can automatically create an environment file which contains exact information on the R or Python version used as well as on all the packages.

First activate the environment, then enter the following command in your terminal:
```bash
conda env export > environment.yml
```
This exports the specifications of your environment into a file called `environment.yml`. You can then add it to your repository on GitHub (like any other file), and it can be used by others to replicate your environment by downloading it and running the following:
```bash
conda env create -f environment.yml
```
The name of the copied environment will be by default the same one you have used and can be changed in the first line of the file.

Don't forget to also include some information in the README on the operating system and version you used.

**Note**: Your `environment.yml` file can become rather cluttered after you have installed many packages. Some of them will be system-specific dependencies which conda installed automatically and might prevent the installation of the environment on a different operating system. To make it easier for others, you might want to delete packages from the list if you don't remember installing them. You can then create a new environment from the edited file (change the name first!) and rerun your analysis, to see if it still works.
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
<summary>Show example environment.yml file</summary>
<small>
{{ environment-yml | markdownify }}
</small>
</details><br />

### Hardware
Depending on your analysis, there might be certain requirements regarding the hardware needed to run it. It is helpful if you specify this in the README file, so that others can better assess if they are able to rerun the analysis on their machine. At a minimum, include some information from your machine, such as total RAM available and if a graphics card was used.

### Data
As previously mentioned, if possible you should provide not only the code but also the raw data used for the analysis. Should you not be able to upload your raw data, but the data is available online for free, you can also provide a notebook or script which automatically downloads the relevant data from the internet. To do this in Python I have prepared a function, which you should be able to just copy and use for your own project:

{% capture download-function %}
```python
import requests
from pathlib import Path

from tqdm import tqdm_notebook


def download_file(url,
                 filename,
                 force_download=False):
    """Downloads file from the url and saves it to specified filename
    (can contain a path).

    Parameters
    ----------
    url : str
        Url from which file should be downloaded

    filename : str
        Filename under which it should be saved (including file ending).
        This can also include a folder change.

    force_download : bool, optional (default=False)
        If True, forces download even if file already exists

    Returns
    -------
    bool
        If download was completed (can be used for follow up actions such as unzipping)

    Example
    -------
    >>> download_file('https://test.com/school_location_1415.csv',
                      '../../data/raw/school_location/sch_location_1415.csv')

    Notes
    -----
    This function heavily leans on these two stackoverflow threads:
    * https://stackoverflow.com/questions/45978295/saving-a-downloaded-csv-file-using-python
    * https://stackoverflow.com/questions/37573483/progress-bar-while-download-file-over-http-with-requests/37573701
    """
    filename = Path(filename)
    # Check if file already exists
    if not filename.is_file() or force_download:
        print(f'Downloading {filename}')
        r = requests.get(url, stream=True)
        # Check if the response is ok (200)
        if r.status_code == 200:
            # Get total file size in bytes. If download server supports it,
            # this will be a compressed version and the total file size on your
            # hard disk may be larger!
            total_size = int(r.headers.get('content-length', 0))
            block_size = 1024
            wrote = 0
            # Open file and write the content
            with filename.open('wb') as f:
                for block in tqdm_notebook(
                        r.iter_content(block_size),
                        total=math.ceil(total_size // block_size),
                        unit='KB',
                        unit_scale=True):
                    wrote = wrote + len(block)
                    f.write(block)
            if total_size != 0 and wrote != total_size:
                raise Exception(f'Could only download {wrote}/{total_size}')
            download_success = True
        else:
            raise Exception(f'Could not download file. Request status code: {r.status_code}')
    else:
        print(
            'File already exists. Nothing was downloaded. Set force_download=True',
            'to download the file anyway and replace the existing one.')
        download_success = False
    return download_success
```
{% endcapture %}

<details>
<summary>Show download function</summary>
<small>
{{ download-function | markdownify }}
</small>
</details><br />

<details>
<summary>Show full "download-data" Jupyter notebook which contains information and sources on all raw data files</summary>
<iframe src="https://nbviewer.jupyter.org/github/binste/chicago_safepassage_evaluation/blob/master/notebooks/0_download_data/0.0-binste-download-data.ipynb" height="1100" width="100%" style="border:none;"></iframe>
</details><br />

If the data is not freely available online, provide an exact documentation of which files you obtained from where and when, how you applied for the data, and what, if any, the costs were. Furthermore, provide a screenshot in the readme file of your `data/raw` folder such that others can better reconstruct it. In any case, even if you can host the raw data, it is good if you provide information on when you obtained the data and if applicable a version number.

## Code
Documenting your code is very important to make your code better more easily understandable. This section shows examples of how you can write a general description of a script or notebook, document your functions, as well as write inline comments.

### Documentation at the beginning of a script
At the beginning of every script or notebook, a brief description should summarize its purpose and functionality.

In Python, you can use docstrings for scripts:
```python
"""Contains various helper functions
to load crimes from the SQL database.
"""
```

In R, you can use standard inline comments:
```r
# Contains various helper functions
# to load crimes from the SQL database.
```

In notebooks (be it Jupyter or R), you should use the markdown functionality to do the same.

### Function and class documentation
#### Python
If you use Python, a good documentation convention is the [Numpydoc format](https://numpydoc.readthedocs.io/en/latest/){:target="_blank"}, which is used to document many popular data science packages. The documentation convention is quite extensive and you certainly don't need to know all of it. A good place to start using it is inside your functions, classes, and methods.

Take the following example of a function defined in Python:

```python
def read_routes_file(shapefile_path, school_year):
    """Reads shapefile of Safe Passage route
    and adds the respective school year as a column

    Parameters
    ----------
    shapefile_path : str
        Path to shapefile which should be read

    school_year : str
        School year in the format of 'SYXXYY',
        for example 'SY1516' for school year 2015-2016

    Returns
    -------
    gpd.DataFrame
        Contains parsed shapefile as well as
        corresponding school year
        as column 'school_year'
    """
    # Code
    ...
    return
```

{% capture extended-function %}
```python
def load_relevant_crimes(min_date,
                         max_date=None,
                         sqldb_path='data/processed/crimes.db',
                         chunksize=None,
                         disk_engine=None,
                         **kwargs):
    """Loads relevant violent and property crimes

    Wrapper around load_crimes which only loads violent and property crimes.
    Furthermore this function provides an easier interface to load
    relevant columns. If add_violent_col is True an additional column is
    added to the returned dataset with a dummy which is 1 for a violent crime
    and 0 for a property crime.

    Parameters
    ----------
    min_date : str, format = "YYYY-MM-DD"
        Min date which should be loaded

    max_date : str, format = "YYYY-MM-DD", optional (default=None)
        Max date which should be loaded

    sqldb_path : str, optional (default='data/processed/crimes.db')
        Path to SQL database, defaults to relative path
        to crimes database from project root. Useful to change
        for example when using Jupyter notebooks in other directories.

    chunksize : int, optional (default=None)
        If specified, return an iterator where chunksize
        is the number of rows to include in each chunk.

    kwargs : keyword arguments, optional
        Further keyword arguments directly passed on to pd.read_sql_query

    Returns
    ------
    pd.DataFrame
        Dataframe containing loaded crimes
    """
    # Code
    ...
    return
```
{% endcapture %}

<details>
<summary>Show another, more extended, example of a documented function</summary>
<small>
{{ extended-function | markdownify }}
</small>
</details><br />

The first sentence of the docstring briefly summarizes the main purpose of the function. A subsequent paragraph could go into more detail if needed (see the extended example). The `Parameters` section names all function arguments (e.g. `shapefile_path`), their type (e.g. `str`), additional information such as the format or if it is an optional argument if applicable, as well as an explanation. The `Returns` section names the type of the returned object and gives a brief description.

#### R
In R you can use the lines just before defining a function to do the same. A good introduction can be found in the [tidyverse style guide](http://style.tidyverse.org/documentation.html){:target="_blank"}.

### Inline comments
Throughout your script or notebook, you should provide information on assumptions you make and reasons for why you do non-obvious steps. Remember, this not only helps others, but also yourself!

> “Code tells you how, comments tell you why.” — [Jeff Atwood (Coding Horror)](https://blog.codinghorror.com/code-tells-you-how-comments-tell-you-why/)

The following example, which I took from Trey Causey, summarizes rather well what the intent of inline comments should be.

> You've probably heard that you should comment your code many times. So, you wrote things such as:
> ```python
> # import packages
> import pandas as pd
> # load some data
> df = pd.read_csv('data.csv', skiprows=2)
> ```
> These are bad comments. They don't add any information. Why is that skiprows parameter set to 2? Are there comments at the beginning of data.csv? Something like this might be preferable:
> ```python
> # Data contains two lines of description text,
> # skip to avoid errors.
> df = pd.read_csv('data.csv', skiprows=2)
> ```

*<small>Source: [Software development skills for data scientists - treycausey.com](http://treycausey.com/software_dev_skills.html)</small>*

(I myself am guilty of writing `# load data` way too many times...)

Next to writing informative easily understandable documentation, [there are a few other things you should consider while doing your analsis](./other_stuff).