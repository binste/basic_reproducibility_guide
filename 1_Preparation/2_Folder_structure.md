---
title: Folder structure
permalink: /preparation/folder_structure
toc: false
---
Setting up a well structured project folder makes it significantly easier for you to keep tabs of all the relevant files, and of course it allows others to more quickly get an overview and find what they are looking for.

In the following I propose a minimal folder structure for your project, which heavily leans on [this excellent but more extensive folder template for data science projects](http://drivendata.github.io/cookiecutter-data-science/){:target="_blank"} (some of the folder descriptions are from there too). However, the template below, compared to the original one, focuses more on using the notebooks, which I introduced in the previous section, as the main analysis tool. They are contained in the `notebook` folder and its subfolders, and the `src` folder then contains scripts which only contain functions that can be imported by the corresponding notebooks. The section on "Doing the work" will go more into detail on how to do this.
```
├── data
│   ├── raw            <- The original, immutable data dump
│   ├── interim        <- Intermediate data
│   └── processed      <- The final data sets
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

{% capture structure-example %}
```
├── LICENSE
├── README.md
├── data
│   ├── interim
│   │   ├── blocks.pkl
│   │   ├── schools.pkl
│   │   └── schools_foia.pkl
│   ├── processed
│   │   ├── blocks.pkl
│   │   ├── crimes.db
│   │   ├── est_df.pkl
│   │   ├── est_df_reduced.pkl
│   │   ├── figures
│   │   │   ├── blocks_fig_3.pkl
│   │   │   ├── blocks_with_dummies.pkl
│   │   │   ├── violent_hourly_counts.pkl
│   │   │   ├── violent_yearly_counts.pkl
│   │   │   └── yearly_violent_FBI.pkl
│   │   ├── foia_sp.pkl
│   │   ├── routes.pkl
│   │   └── schools_blocks.pkl
│   └── raw
│       ├── Boundaries\ -\ Census\ Blocks\ -\ 2010
│       │   └── ...
│       ├── Crimes_-_2001_to_present.csv
│       ├── Safe_Passage_Schools_By_Implementation_Year_8.12.16.xlsx
│       ├── routes
│       │   ├── Chicago\ Public\ Schools\ -\ Safe\ Passage\ Routes\ SY1314
│       │   │   └── ...
│       │   ├── Chicago\ Public\ Schools\ -\ Safe\ Passage\ Routes\ SY1415
│       │   │   └── ...
│       │   └── Chicago\ Public\ Schools\ -\ Safe\ Passage\ Routes\ SY1516
│       │       └── ...
│       ├── school_locations
│       │   ├── CPS_School_Locations_SY1415.csv
│       │   ├── CPS_School_Locations_SY1516.csv
│       │   └── Units2013_14.csv
│       └── school_names.xlsx
├── environment.yml
├── install.R
├── models
│   ├── poisson_property.rds
│   ├── poisson_property_reduced.rds
│   ├── poisson_violent.rds
│   ├── poisson_violent_reduced.rds
│   ├── summary_poisson_property.csv
│   ├── summary_poisson_property_reduced.csv
│   ├── summary_poisson_violent.csv
│   └── summary_poisson_violent_reduced.csv
├── notebooks
│   ├── 0_download_data
│   │   └── 0.0-binste-download-data.ipynb
│   ├── 1_prepare_data
│   │   ├── 0.0-binste-foia-sp.ipynb
│   │   ├── 1.0-binste-routes.ipynb
│   │   ├── 2.0-binste-school-locations.ipynb
│   │   └── 3.0-binste-blocks.ipynb
│   ├── 2_set_up_crime_database
│   │   └── 0.0-binste-set-up-crime-database.ipynb
│   ├── 3_match_datasets
│   │   ├── 0.0-binste-blocks-routes.ipynb
│   │   ├── 1.0-binste-schools-foia.ipynb
│   │   ├── 1.1-binste-schools-blocks.ipynb
│   │   └── 2.0-binste-crimes-blocks.ipynb
│   ├── 4_combine_for_analysis
│   │   └── 0.0-binste-create-estimation-dataset.ipynb
│   └── 5_analysis
│       ├── 0.0-binste-estimation-poisson.ipynb
│       ├── 1.0-binste-analyze-crime-results-census-block-level.ipynb
│       └── 2.0-binste-descriptives-for-appendix.ipynb
├── postBuild
├── reports
│   ├── appendix
│   │   ├── Appendix.pdf
│   │   ├── Appendix.tex
│   └── figures
│       ├── mcmillen_fig_3.png
│       ├── mcmillen_fig_a2.png
│       ├── mcmillen_reg_1.png
│       ├── mcmillen_tab_1.png
│       ├── mcmillen_tab_10.png
│       └── mcmillen_tab_2.png
├── run_ipynb.py
├── runtime.txt
├── src
│   ├── __init__.py
│   ├── analysis
│       ├── __init__.py
│   │   └── figures.py
│   ├── calculate
│       ├── __init__.py
│   │   └── distances.py
│   └── prepare_data
│       ├── __init__.py
│       ├── crime_database.py
│       ├── routes.py
└       └── school_locations.py
```
{% endcapture %}

<details>
  <summary>Show the folder structure of the example project</summary>
  <small>
  {{ structure-example | markdownify }}
  </small>
</details>

**Note**: A good naming convention for your notebooks might be: "A number (for ordering), the creator's initials, and a short `-` delimited description, e.g. `1.0-jqp-initial-data-exploration`." - [Cookiecutter Data Science](http://drivendata.github.io/cookiecutter-data-science/){:target="_blank"}.
{: .notice}

Depending on your personal workflow, you might want to change the proposed folder structure to better suit your needs. However, at least try to adhere to the following points (partly inspired by [this post](http://kbroman.org/steps2rr/pages/organize.html){:target="_blank"}):

* Put every new project in a new folder. This makes it not only easier for you to have an overview of everything belonging to the project, but also for putting your project into version control (we'll talk about this later) and sharing it with others.
* Keep your unedited data files in a separate folder (e.g. `data/raw`) in the exact same form you originally received them (using the original file name). Although it might be tempting to open that Excel file and change a few things by hand, don't!
* Put data, code, and produced reports/models into different subdirectories.

After we have neatly arranged our project folder, [let us talk about a very important but often neglected topic: Version control](./version_control).