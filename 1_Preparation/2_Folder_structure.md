---
title: Folder structure
---
Setting up a well structured project folder makes it not only for you easier to keep tabs of all the relevant files but also helps others to more easily find their way.

A minimal folder structure is proposed in the following. It heavily leans on [this excellent but more extensive folder template for data science projects](http://drivendata.github.io/cookiecutter-data-science/){:target="_blank"} (most of the folder descriptions are from there). However, the template below focuses more on using notebooks as the main analysis tool (see previous section). They are contained in the `notebook` folder. The `src` folder contains functions which can be imported by the corresponding notebooks.

```
├── data
│   ├── interim        <- Intermediate data that has been transformed.
│   ├── processed      <- The final, canonical data sets for the analysis.
│   └── raw            <- The original, immutable data dump.
│
├── models             <- Trained and serialized models/regressions, model predictions, or model summaries
│
├── notebooks          <- Jupyter notebooks.
│   │
│   ├── 0_download_data  <- Notebooks to download data
│   │
│   │── 1_prepare_data   <- Notebooks to prepare data (clean, merge, etc.)
│   │
└   └── other folders  <- Depending on your analysis you might want additional folders such as model, visualization, analysis, etc.
│
├── references         <- Data dictionaries, manuals, and all other explanatory materials.
│
├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
│   └── figures         <- Generated graphics and figures to be used in reporting
│
├── src                <- Source code for use in this project (e.g. all .py/.r files). Might contain mostly functions which can be imported by the notebooks
│   │
│   ├── download_data  <- Scripts to download data
│   │
│   │── prepare_data   <- Scripts to prepare data (clean, merge, etc.)
│   │
└   └── other folders  <- Depending on your analysis you might want additional folders such as model, visualization, analysis, etc.
```
[![example](../figures/example_icon.png){:height="36px" width="36px"}](https://github.com/binste/chicago_safepassage_evaluation){:target="_blank"}

A good naming convention for your notebooks might be:
"*A number (for ordering), the creator's initials, and a short `-` delimited description, e.g. `1.0-jqp-initial-data-exploration`."*
[![example](../figures/example_icon.png){:height="36px" width="36px"}](https://github.com/binste/chicago_safepassage_evaluation/tree/master/notebooks/1_prepare_data){:target="_blank"} (taken from the above mentioned cookie cutter template).

Depending on your personal workflow you might want to change the proposed folder structure. However, at least try to adhere to the following points (partly inspired by [this post](http://kbroman.org/steps2rr/pages/organize.html){:target="_blank"}):

* Put every new project in a new folder. This makes it not only easier for yourself to have an overview of everything belonging to the project, but also for putting your project into version control (we'll talk about this later) and sharing it with others.
* Keep your unedited data files in a separate folder (e.g. `data/raw`) as you originally received them (using the original file name). Although it might be tempting to open that Excel file and change a few things by hand, don't!
* Put data, code, and produced reports/models into different subdirectories.

After we have neatly arranged our project folder, [let us talk about a very important, but often neglected topic: Version control](./3_Version_control.md).

[Table of content: "Preparation"](./index.md)