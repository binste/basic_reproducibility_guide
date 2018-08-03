---
title: Doing the work
---
Apart from the documentation of your project discussed previously, there are a few other points to follow during your analysis.

## Automate every single step
Seriously, never use the point-and-click capabilities of a software. Instead, use a script or notebook in your prefered programming language to run every step. This is extremely important for reproducibility. If you really need to defer from this practice, document every click you do carefully and provide screenshots or a video of the process.

### Relative paths
Always use relative instead of absolute paths throughout your code base. This is another reason why it was important to put the project into a new directory. `/Users/sbinder/repository_name/data/raw/` then becomes `./data/raw`. This allows others to rerun the code without adjusting any paths.


### Refactor codes
If you follow a notebook-based workflow, your notebooks might get cluttered with functions at one point. To increase reusability of your code and clean up your notebooks, it is worth it to put some of the code into a separate script and call it from inside the notebook. For an example on how this might work in Python, see [![example](../figures/example_icon.png){:height="36px" width="36px"}](https://github.com/binste/chicago_safepassage_evaluation/blob/master/notebooks/1_prepare_data/1.0-binste-routes.ipynb){:target="_blank"}. In the beginning
```python
from src.prepare_data.routes import (read_routes_file, harmonize_dataframe,
                                     check_school_name_id_unique,
                                     harmonize_all_names)
```
imports various functions defined outside of the notebook in the [`src/prepare_data/routes.py`](https://github.com/binste/chicago_safepassage_evaluation/blob/master/src/prepare_data/routes.py) script for better readability of the notebook and such that the functions can be used by multiple notebooks.

[Part 5](https://www.youtube.com/watch?list=PLYCpMb24GpOC704uO9svUrihl-HY1tTJJ&time_continue=1&v=DjpCHNYQodY){:target="_blank"} of Jake Vanderplas' great Reproducible Data Analysis series goes more in-depth on this topic.

In R you can do the same. Following the example above, if you have put some functions in a separate .R script, you can import them by calling
```r
source("src/prepare_data/routes.R")
```
at the beginning of your Jupyter or R notebook. This will run all code in `routes.R` and therefore define all functions in it

### Use random seeds
If your project involves the use of a pseudorandom number generator (or an algorithm which uses one), you should explicitly set the random seed such that a rerun of the experiment gives exactly the same results.

[Back to the table of content](./index.md)