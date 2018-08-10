---
title: Writing good documentation
permalink: /during_the_analysis/documentation
---
Writing good and up-to-date documentation is critical for others to be able to quickly understand your project. It is also essential for yourself to later on understand what you did and especially why. It is a good habit to start right from the beginning keep updating your documentations whenever something changes.

## README file
Always create a README file in the root directory of your project. This can be a markdown (.md) or text (.txt) file. It will be the entry point for visitors to your project. First, include a description of your project. If it is multiple paragraphs, provide a short summary in the beginning.

> Note: Your readme file will also be automatically detected by GitHub (and if it is written as a Markdown file also rendered) and displayed when someone visits your GitHub repository.

[![example](../figures/example_icon.png){:height="36px" width="36px"}](https://github.com/binste/chicago_safepassage_evaluation/blob/master/README.md){:target="_blank"}

### Data and code "pipeline"
Another section in your README should provide information on how to reproduce the results (eg. "First execute `.../0.0-bis-download_data.ipynb`, then ..., to reproduce all the main figures and tables in the paper"). To make the later part easier for visitors, you can also provide a single script/notebook which runs all the necessary files in the correct order to get from the raw data to the final results. This is extremely useful for reproducibility and also serves as sort of a documentation of your workflow. If you worked with Jupyter notebooks, you can use [this small script](https://github.com/binste/chicago_safepassage_evaluation/blob/master/run_ipynb.py){:target="_blank"} I wrote.

### Software environment
To reproduce your results, others need to know what software and additional packages you used (and the respective version numbers). You can also specify this in the above discussed README file.

Again, there is a way to greatly simplify this process. If you used the package manager conda and created a new environment for your porject, you can automatically create an environment file which contains exact information on the R or Python version used as well as on all the packages.

First activate the environment, then enter the following command:
```bash
conda env export > environment.yml
```
This exports the specifications of your environment into a file called `environment.yml`. You can then add it to your repository on GitHub (like any other file) and it can be used by others to replicate your environment by downloading it and calling
```bash
conda env create -f environment.yml
```
The name of the copied environment will be by default the same one you have used and can be changed in the first line of the file.

> Note: Your `environment.yml` file can become rather cluttered after you have installed many packages. Some of them will be system-specific dependencies which conda installed automatically and might prevent the installation of the environment on a different operating system. To make it easier for others, you might want to delete packages from the list if you don't remember installing them. You can then create a new environment from the edited file (change the name first!) and rerun your analysis, to see if it still works. [![example](../figures/example_icon.png){:height="36px" width="36px"}](https://github.com/binste/chicago_safepassage_evaluation/blob/master/environment.yml){:target="_blank"}

Don't forget to also include some information in the README on the operating system and the version you used.

### Hardware
Depending on your analysis, it might have certain requirements regarding the hardware needed to run it. It is helpful if you specify this in the README file, such that others can better assess, if they are able to rerun the analysis on their machine. At a minimum, include some information from your machine, such as total RAM available and if a graphics card was used.

### Data
As previously mentioned, if possible (read: allowed) you should provide not only the code but also the raw data used for the analysis. Should you not be able to upload your raw data, but the data is available online for free, you can also provide a notebook or script, which automatically downloads the relevant data from the internet. To do this in Python you can use [this function](../download_function).

If the data is not freely available online, provide an exact documentation of which files you obtained from where, how you applied for the data, and what were the costs if any. Furthermore, provide a screenshot of your `data/raw` folder such that others can better reconstruct it.

In any case it is good if you provide information on when you obtained the data and if applicable a version number.
[![example](../figures/example_icon.png){:height="36px" width="36px"}](https://github.com/binste/chicago_safepassage_evaluation/blob/master/notebooks/0_download_data/0.0-binste-download-data.ipynb){:target="_blank"}

## Code
Documenting your code is very important for others to be able to better and more easily understand it, as well as for yourself if you ever revisit code you have written in the past. This section shows examples of how you can write a general description of a script or notebook, document your functions as well as write inline comments.

### Documentation at beginning of a script
At the beginning of every script or notebook, a brief description should summarize its purpose and functionality.

In Python you can use docstrings for scripts:
```python
"""Loads and prepares median income data as well as
data on racial composition (calculates racial heterogeneity index).
All of it on a census block level.
This data is then merged to the block group dataset.
"""
```

In R you can use standard inline comments.
```r
# Loads and prepares median income data as well as
# data on racial composition (calculates racial heterogeneity index).
# All of it on a census block level.
# This data is then merged to the block group dataset.
```

In a Jupyter/R notebook, you should use the markdown functionality to do the same.

### Function and class documentation
#### Python
If you use Python, a good documentation convention is the [Numpydoc format](https://numpydoc.readthedocs.io/en/latest/){:target="_blank"}, which is used in many popular data science packages. The documentation is quite extensive, but a good place to start using it is inside your functions, classes, and methods.

Take the following example of the first few lines of a function defined in Python:
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
[![example](../figures/example_icon.png){:height="36px" width="36px"}](https://github.com/binste/chicago_safepassage_evaluation/blob/master/src/prepare_data/crime_database.py){:target="_blank"}

The first line of the docstring briefly summarizes the main purpose of the function. The subsequent paragraph goes into more detail. The `Parameters` section names all function arguments (e.g. `min_date`), their type (e.g. `str`), if applicable additional information such as format or if it is an optional argument as well as an explanation. The `Returns` section names the type of the returned object and a brief description.

#### R
In R you can use the lines just before defining a function to do the same. A good introduction can be found in the [tidyverse style guide](http://style.tidyverse.org/documentation.html){:target="_blank"}.

### Inline comments
Throughout your script or notebook, you should provide information on assumptions you make,reasons on why you do non-obvious steps, etc. Remember, this not only helps others but first and foremost yourself!

> “Code tells you how, Comments tell you why.” — [Jeff Atwood (Coding Horror)](https://blog.codinghorror.com/code-tells-you-how-comments-tell-you-why/)

The following example, which I took from [Software development skills for data scientists - treycausey.com](http://treycausey.com/software_dev_skills.html), summarizes rather well what the intent of inline comments should be.

> You've probably heard that you should comment your code many times. So, you wrote things like this:
> ```python
> # import packages
> import pandas as pd
> # load some data
> df = pd.read_csv('data.csv', skiprows=2)
> ```
> These are bad comments. They don't add any information. Why is that skiprows parameter set to 2? Are there comments at the beginning of data.csv? Something like this might be preferable:
> ```python
> # Data contains two lines of description text, skip to avoid errors.
> df = pd.read_csv('data.csv', skiprows=2)
> ```

(I myself am guilty of writing `# load data` way too many times...)

Next to writting informative easily understandable documentation, [there are a few other things you should consider while doing your analsis](./doing_the_work).