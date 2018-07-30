---
title: Writing good documentation
---
* TOC
{:toc}

Remember, documentation is only useful if it is kept up to date! Otherwise, it might cause confusion and even be counterproductive. However, don't get into the habit of writing the documentation last, to avoid having outdated comments. Start good habits right from the beginning and keep updating your documentations whenever something changes. This will also help you later on understand what you did and especially why you did it.

## README in the root directory
Always create a README file in the root directory of your project. This can be a markdown (.md) or (.txt) file.
>**Note**: A readme file in the root directory gets automatically detected by GitHub (and if it is written as a Markdown file also rendered) and displayed when someone visits your GitHub repository.

As a minimum, it should briefly explain what the project is about, as well as provide information on how to reproduce the results (eg. "First execute `.../0.0-bis-download_data.ipynb`, then ..., to reproduce all the main figures and tables in the paper"). To make the later part easier for visitors, you can provide a single script/notebook which runs all others in the correct order to get from the raw data to the final results. This is extremely useful for reproducibility and serves as sort of a documentation of your workflow. If you worked with Jupyter notebooks, I wrote [this small script](https://github.com/binste/chicago_safepassage_evaluation/blob/master/run_ipynb.py){:target="_blank"} which you might find useful (for an example see the first few lines).

[![example](../figures/example_icon.png){:height="36px" width="36px"}](https://github.com/binste/chicago_safepassage_evaluation/blob/master/README.md){:target="_blank"}

## Add an environment.yml file
To reproduce your results, others need to know what software and additional packages you used (and the respective version numbers). You can either specify this in the above discussed README file, or, if you used the package manager conda, you can automatically create an environment file which contains all the necessary information. This allows others to get the same Python or R installation with a single command.

If you have created a new environment with conda for your project, activate it and then enter the following command:
```bash
conda env export > environment.yml
```
This exports the specifications of your environment into a file called `environment.yml` (and will overwrite an already existing one). You can now add this to your repository on GitHub (like any other file) and it can be used by others to replicate your environment by calling

```bash
conda env create -f environment.yml
```
The name of the environment will be the same and is determined by the first line of the `environment.yml` file.
{% comment %}
Expand by information of deleting a lot of the content of the environment file...
{% endcomment %}

[![example](../figures/example_icon.png){:height="36px" width="36px"}](https://github.com/binste/chicago_safepassage_evaluation/blob/master/environment.yml){:target="_blank"}

## Data
As already mentioned, if possible (and especially allowed) you want to provide not only your code but also the raw data used for the analysis. Should you not be able to upload your raw data but the data is available online for free, you should provide a notebook which automatically downloads the relevant data from the internet. To do this in Python you can use [this function](../help_snippets/download_function.md). If the data is not available online, provide an exact documentation of where you obtained what files, how you applied for them, and what were the costs. To speed up the documentation you could provide a screenshot of your `data/raw` folder.

In any case it is good if you provide information on when you obtained the data and if applicable a version number.
[![example](../figures/example_icon.png){:height="36px" width="36px"}](https://github.com/binste/chicago_safepassage_evaluation/blob/master/notebooks/0_download_data/0.0-binste-download-data.ipynb){:target="_blank"}

## Code
Documenting your code is very important for others to be able to better and more easily understand it, as well as for yourself if you ever revisit code you have written in the past. This section shows examples of how you can write a general description of a script or notebook, document your functions as well as write inline comments.

### Function and class documentation
#### Python
If you use Python, a good documentation convention is the [Numpydoc format](https://numpydoc.readthedocs.io/en/latest/){:target="_blank"}, which is used in many popular data science packages. The documentation is quite extensive, but a good place to start using it is inside your functions and classes (and methods) which allow for docstrings.

Take the following beginning of a function defined in Python as an example:
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
        Further keyword arguments directly passed on to pd.read_sql_query call

    Returns
    ------
    pd.DataFrame
        Dataframe containing loaded crimes
    """
```
[![example](../figures/example_icon.png){:height="36px" width="36px"}](https://github.com/binste/chicago_safepassage_evaluation/blob/master/src/prepare_data/crime_database.py){:target="_blank"}

The first line briefly summarizes the main purposes of the function. The following paragraph goes into more detail. The `Parameters` section names all function arguments (e.g. `min_date`), their type (e.g. `str`), if applicable additional information such as format or if it is an optional argument (mention what the default is!) as well as a explanation. The `Returns` section names the type of the returned object and a brief description.

#### R
In R you can use the lines just before defining a function to do the same. You can find a good introduction in the [tidyverse style guide](http://style.tidyverse.org/documentation.html){:target="_blank"}.

### Inline comments
Throughout your script or notebook, you should provide information on assumptions you make, reasons on why you do non-obvious steps, etc. Remember, this not only helps others but first and foremost yourself!

> “Code tells you how, Comments tell you why.” — [Jeff Atwood (Coding Horror)](https://blog.codinghorror.com/code-tells-you-how-comments-tell-you-why/)

### Documentation at beginning of a script
At the beginning of a script you can place a short summary on what the script does.

In Python you can use docstrings:
```python
"""Loads and prepares median income data as well as
data on racial composition (calculates racial heterogeneity index).
All of it on a census block level.
This data is then merged to the block group dataset.
"""
```

In R simply put inline comments at the beginning of a script.
```r
# Loads and prepares median income data as well as
# data on racial composition (calculates racial heterogeneity index).
# All of it on a census block level.
# This data is then merged to the block group dataset.
```

In a Jupyter/R notebook, use the markdown functionality to do the same.

[Back to the table of content](./index.md)