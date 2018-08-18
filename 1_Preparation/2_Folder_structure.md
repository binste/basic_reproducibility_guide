---
title: Folder structure
permalink: /preparation/folder_structure
toc: false
---
Setting up a well-structured project folder makes it significantly easier for you to keep tabs on all the relevant files, and of course it allows others to more quickly get an overview and find what they are looking for.

In the following I propose a minimal folder structure for your project, which heavily leans on [this excellent but more extensive folder template for data science projects](http://drivendata.github.io/cookiecutter-data-science/){:target="_blank"} (some of the folder descriptions are from there, too). However, compared to the original template, my version below focuses more on using the notebooks (introduced in the previous section) as the main analysis tool. They are contained in the `notebook` folder and its subfolders. The `src` is made up of scripts which only contain functions that can then be imported by the corresponding notebooks. The section on "Doing the work" will go more into detail on how to do this.
```
├── data
│   ├── raw            <- The original, immutable data dump
│   ├── interim        <- Intermediate data
│   └── processed      <- The final datasets
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

**Note**: A good naming convention for your notebooks might be: "A number (for ordering), the creator's initials, and a short `-` delimited description, e.g. `1.0-jqp-initial-data-exploration`." - [Cookiecutter Data Science](http://drivendata.github.io/cookiecutter-data-science/){:target="_blank"}.
{: .notice}

Depending on your personal workflow, you might want to change the proposed folder structure to better suit your needs. However, at least try to adhere to the following key points (partly inspired by [this post](http://kbroman.org/steps2rr/pages/organize.html){:target="_blank"}):

* Put every new project into a new folder. This makes it not only easier for you to have an overview of everything belonging to the project, but also for putting your project into version control (we'll talk about this later) and sharing it with others.
* Keep your unedited data files in a separate folder (e.g. `data/raw`) in the exact same form you originally received them (using the original file name). Although it might be tempting to open that Excel file and change a few things by hand, don't!
* Put data, code, and produced reports/models into different subdirectories.

After we have neatly arranged our project folder, [let us talk about a very important but often neglected topic: Version control](./version_control).