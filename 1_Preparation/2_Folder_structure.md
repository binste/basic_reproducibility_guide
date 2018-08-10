---
title: Folder structure
permalink: /preparation/folder_structure
toc: false
---
Setting up a well structured project folder makes it not only for you easier to keep tabs of all the relevant files but also helps others to more easily find their way.

A minimal folder structure is proposed in the following. It heavily leans on [this excellent but more extensive folder template for data science projects](http://drivendata.github.io/cookiecutter-data-science/){:target="_blank"} (most of the folder descriptions are from there). However, the template below focuses more on using notebooks as the main analysis tool (see previous section). They are contained in the `notebook` folder. The `src` folder then contains scripts which only contain functions which can be imported by the corresponding notebooks. The section on "Doing the work" will go more in-depth on how to do this.

```
├── data
│   ├── interim        <- Intermediate data
│   ├── processed      <- The final data sets
│   └── raw            <- The original, immutable data dump
│
├── models             <- Serialized models, summaries
│
├── notebooks          <- Jupyter notebooks
│   │
│   ├── 0_download_data
│   │
│   │── 1_prepare_data
│   │
│   └── other folders
│
├── references         <- Data dictionaries, manuals, etc.
│
├── reports            <- HTML, PDF, LaTeX, etc.
│   └── figures
│
├── src                <- Functions for notebooks
│   │
│   ├── download_data
│   │
│   │── prepare_data
│   │
└   └── other folders
```
[![example](../figures/example_icon.png){:height="36px" width="36px"}](https://github.com/binste/chicago_safepassage_evaluation){:target="_blank"}

> Note: A good naming convention for your notebooks might be: "A number (for ordering), the creator's initials, and a short `-` delimited description, e.g. `1.0-jqp-initial-data-exploration`." [![example](../figures/example_icon.png){:height="36px" width="36px"}](https://github.com/binste/chicago_safepassage_evaluation/tree/master/notebooks/1_prepare_data){:target="_blank"} (taken from the above mentioned cookie cutter template).

Depending on your personal workflow you might want to change the proposed folder structure. However, at least try to adhere to the following points (partly inspired by [this post](http://kbroman.org/steps2rr/pages/organize.html){:target="_blank"}):

* Put every new project in a new folder. This makes it not only easier for yourself to have an overview of everything belonging to the project, but also for putting your project into version control (we'll talk about this later) and sharing it with others.
* Keep your unedited data files in a separate folder (e.g. `data/raw`) as you originally received them (using the original file name). Although it might be tempting to open that Excel file and change a few things by hand, don't!
* Put data, code, and produced reports/models into different subdirectories.

After we have neatly arranged our project folder, [let us talk about a very important, but often neglected topic: Version control](./version_control).