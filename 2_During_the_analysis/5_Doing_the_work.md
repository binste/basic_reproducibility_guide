---
title: Other stuff
permalink: /during_the_analysis/other_stuff
---
Apart from the documentation of your project discussed previously, there are a few other practices you should follow during your analysis.

## Automate every single step
This is a very important one. Never use the point-and-click capabilities of a software. Instead, use a script or notebook in your prefered programming language to run every step. This is extremely important for reproducibility.

**Note**: Should you really have a use case where you need to defer from this practice, document every click you make carefully and provide screenshots or a video of the process.
{: .notice}

## Relative paths
Always use relative instead of absolute paths throughout your code base. This is another reason why it was important to put the project into its own directory. `/Users/sbinder/repository_name/data/raw/` for example becomes `./data/raw`. Relative paths allow others to rerun the code without first adjusting any paths.

## Refactor codes
If you follow a notebook-based workflow, your notebooks might get cluttered with functions at one point. To increase reusability of your code and clean up your notebooks, you can put functions into a separate script and call them from inside the notebook. For an example on how this might work in Python, see [![example](../figures/example_icon.png){:height="36px" width="36px"}](https://github.com/binste/chicago_safepassage_evaluation/blob/master/notebooks/1_prepare_data/1.0-binste-routes.ipynb){:target="_blank"}. In the beginning, the statement
```python
from src.prepare_data.routes import (read_routes_file, harmonize_dataframe,
                                     check_school_name_id_unique,
                                     harmonize_all_names)
```
imports various functions defined outside of the notebook in the [`src/prepare_data/routes.py`](https://github.com/binste/chicago_safepassage_evaluation/blob/master/src/prepare_data/routes.py) script.

**Note**: [Part 5](https://www.youtube.com/watch?list=PLYCpMb24GpOC704uO9svUrihl-HY1tTJJ&time_continue=1&v=DjpCHNYQodY){:target="_blank"} of Jake Vanderplas' Reproducible Data Analysis series goes more in-depth on the topic and is certainly worth watching.
{: .notice}

Following the example above, in R you can put some functions in a separate .R script and import them by calling
```r
source("src/prepare_data/routes.R")
```
at the beginning of your Jupyter or R notebook. This will run all code in `routes.R` and therefore define all functions in it.

## Use random seeds
If your project involves the use of a pseudorandom number generator (or an algorithm which uses one), you should explicitly set the random seed such that a rerun of the experiment gives exactly the same results.

You already generated some interesting insights and might be ready to share them with the world? [Let us first quickly look at the legal aspect of licensing your work (this is a short one, I promise)](../sharing_your_work/license).