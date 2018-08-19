---
title: Coding practices
permalink: /during_the_analysis/coding_practices
header:
    overlay_image: /figures/rayi-christian-wicaksono-366-unsplash_cropped.jpg
    caption: "<small>Photo credit: <a href='https://unsplash.com/photos/6PF6DaiWz48' target='_blank'>Rayi Christian Wicaksono</a></small>"
---
Apart from the documentation of your project discussed previously, there are a few other practices you should follow during your analysis.

## Automate every single step
This is an extremely important point in making your research reproducible. Never use the point-and-click capabilities of a software to perform a step in your analysis. Instead, use a script or notebook in your preferred programming language to run everything, from data preparation, over visualization, up to the modeling.

**Note**: Should you really need to defer from this practice, document every click you make carefully and provide screenshots or a video of the process.
{: .notice}

## Relative paths
Another thing that is important to remember is to always use relative instead of absolute paths throughout your code base. This is another reason why it was important to put the project into its own directory. `/Users/sbinder/repository_name/data/raw/` for example becomes `./data/raw`. Relative paths allow others to rerun the code without first adjusting any paths.

## Refactor codes
If you follow a notebook-based workflow, your notebooks might get cluttered with a lot of code at one point which you might even end up copying from one notebook to the next. To increase the reusability of your code and clean up your notebooks, you can put code into functions and then into a separate script. This allows to import the same functions in multiple notebooks. If you have, for example, some code which loads data from a SQL database, and you want to do this in multiple notebooks, this would be a perfect use case for a function in a separate script. You can see this example implemented in the following Jupyter notebook:

<details>
<summary style="cursor:pointer">Show notebook</summary>
<iframe src="https://nbviewer.jupyter.org/github/binste/chicago_safepassage_evaluation/blob/master/notebooks/3_match_datasets/2.0-binste-crimes-blocks.ipynb" height="1100" width="100%" style="border:none;"></iframe>
</details><br />

In the beginning, the line
```python
from src.prepare_data.crime_database import load_relevant_crimes
```
imports the function `load_relevant_crimes` that is defined in the script `src/prepare_data/crime_database.py`.

{% capture crime-database-script %}
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
    -------
    pd.DataFrame
        Dataframe containing loaded crimes
    """
    # Code
    ...
    return ...
```
{% endcapture %}

<details>
<summary style="cursor:pointer">Show function in crime_database.py</summary>
<small>
{{ crime-database-script | markdownify }}
</small>
</details>


**Note**: For more information on how to refactor your Jupyter notebooks, see [Part 5](https://www.youtube.com/watch?list=PLYCpMb24GpOC704uO9svUrihl-HY1tTJJ&time_continue=1&v=DjpCHNYQodY){:target="_blank"} of Jake Vanderplas' Reproducible Data Analysis series.
{: .notice}

For R users, the process is exactly the same, and you can import functions defined in an .R script by calling (sticking with the above example):
```r
source("src/prepare_data/crime_database.R")
```
at the beginning of your notebook, be it Jupyter or R.

## Use random seeds
Another random but important note: If your project involves the use of a pseudorandom number generator (or an algorithm which uses one), you should explicitly set the random seed such that a rerun of the experiment gives exactly the same results.

So assume you've finished your first research project that adheres to the basic tools and principles of reproducible research outlined in this guide, and you're now ready to share your work with the world through GitHub. [In order to do this, we need to spend 60 seconds talking about the legal aspect of licensing your work.](../sharing_your_work/license).