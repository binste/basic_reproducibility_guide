---
title: "Overview"
---
**ATTENTION**: This is a work in progress and subject to major changes.

In 2016, the journal *Nature* published a [poll](https://www.nature.com/news/1-500-scientists-lift-the-lid-on-reproducibility-1.19970?WT.mc_id=SFB_NNEWS_1508_RHBox) of more than 1,500 researchers from various fields who were questioned on the topic of reproducibility. Over 70% have attempted to replicate another researcher's experiment and have failed. More than half could not reproduce their own findings.

When asked, what where the factors that contribute to irreproducible research, among the top factors where technical barriers of code or raw data not being available and that there is a lot of technical expertise required for reproducing the results.

This website presents a basic workflow which makes your next data analysis reproducible by others with minimal effort. I believe that reproducible research is important out of two key reasons. The first one is credibility:

>*“Only results that can be replicated are truly scientific results. If there is no chance to replicate
research results, they can be regarded as no more than personal views in the opinion or review
section of a daily newspaper.”* - [Huschka (2013)](https://www.ratswd.de/dl/RatSWD_WP_216.pdf){:target="_blank"}

The other one is the reason of enabling future research to build upon existing work instead of creating the need to first painfully recreate what has already been done.

## Tools
This guide is primarily written for Python and R users. Both languages are open-source, which greatly helps in making your research reproducible. Furthermore, they have huge ecosystems of extensions and tutorials. However, most of the tools and practices advertised should work with other commonly used languages for data analysis such as Stata, Julia, Scala, C++, or Matlab.

If you want to use either Python or R and are completely new to it, I recommend that you first get up to speed with [these tutorials](./help_snippets/starter_python_r.md) before continuing with this guide. In the section on "Programming environment" I'll also go into the details on setting up Python and R in a way which is favorable for reproducible research.

## Content
The guide is split into three parts.

1. [Preparation and setup](./1_Preparation/)
2. [During the analysis](./2_During_the_analysis/)
3. [Sharing your work](./3_Sharing_your_work/)

Furthermore, I compiled a [list of tutorials and documentations](./Where_to_go_next.md) which go more in-depth on reproducible research.

## About
This website is part of my thesis for obtaining a Master of Arts in Economics (major) and Data Science (minor) at the University of Zurich. The second part is an evaluation of the effectiveness of a crime prevention program in Chicago. You can find an overview of the analysis [here](https://binste.github.io/chicago_safepassage_evaluation/). The code in the corresponding [GitHub repository](https://github.com/binste/chicago_safepassage_evaluation) can be seen as an example for the practices I'll advertise in this guide. Throughout the guide, the ![example](./figures/example_icon.png){: height="36px" width="36px"} icon will take you to relevant files and folders such that you can see it all in action.
