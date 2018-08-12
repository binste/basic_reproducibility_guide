---
title: Overview
header:
    overlay_image: /figures/simon-abrams-286276-unsplash_cropped.jpg
    caption: "Photo credit: [Simon Abrams](https://unsplash.com/photos/k_T9Zj3SE8k)"
permalink: ./
author_profile: true
share: true
toc: false
sidebar: false
classes: wide
---
**ATTENTION**: This is a work in progress and subject to major changes.

In 2016, the journal *Nature* published a [poll](https://www.nature.com/news/1-500-scientists-lift-the-lid-on-reproducibility-1.19970?WT.mc_id=SFB_NNEWS_1508_RHBox) of more than 1,500 researchers from various fields who were questioned on the topic of reproducibility. Over 70% have attempted to replicate another researcher's experiment and have failed. More than half could not reproduce their own findings.

When asked, what where the factors that contribute to irreproducible research, among the top factors where technical barriers of code or raw data not being available, and that there is a lot of technical expertise required for reproducing the results.

I believe that reproducible research is important out of two key reasons. The first one is credibility:

>*“Only results that can be replicated are truly scientific results. If there is no chance to replicate
research results, they can be regarded as no more than personal views in the opinion or review
section of a daily newspaper.”* - [Huschka (2013)](https://www.ratswd.de/dl/RatSWD_WP_216.pdf){:target="_blank"}

The second one is the reason of enabling future research to build upon existing work. Why do others first need to painfully recreate what you already have done before? That would not be very nice of you, except of course that's what you want...

This guide will show you a minimal set of tools and pratices, which will make your next data analysis reproducible. In the end, others will be able to easily access your project, replicate your findings, as well as build upon them, and all of this with as less effort as possible, for them as well as for yourself.

First, we will set up all the software needed and organise our project folder in a way, which should hopefully still allow to call it *structured* by the end of the project. You'll then learn on how to put your project under version control to prevent `estimate_finalV2superfinal_wheredidthestarsgo_outdated.R`.

Next up is writing good and up-to-date documentation as well as some other practices you should adhere to while doing your analysis. Wait! Before you go on YouTube, this isn't as boring as it sounds. *<small>Even if it would be, I wouldn't tell you now, as it is one of the most important things, especially for yourself.</small>*

Last but not least, it will be time to let everyone in on the fun and enjoy the awesome project you have created. They'll be able to rerun your code until their CPU's melt (if they want to). Or they can just run some of it in the cloud, for free, without any setup. Seems like there is such a thing as a free lunch after all.

## Tools
This guide is primarily written for Python and R users. Both languages and corresponding interpreters are open-source and available for free, which greatly helps in making your research reproducible. Furthermore, they have huge ecosystems of extensions and tutorials. However, most of the tools and practices advertised should work with other commonly used (and some of them also freely available) languages for data analysis such as Stata, Julia, Scala, C++, or Matlab.

If you want to use either Python or R and are completely new to it, I recommend that you first get up to speed with [this list of tutorials](/beginner_resources) before continuing with the guide.

## Showing is better than telling
Next to this guide, I created a data analysis, which showcases the tools and practices advertised in this guide. In there, I look at geo-tagged crime data, to assess the effectiveness of a crime prevention program in Chicago. You can find an overview of the analysis [here](https://binste.github.io/chicago_safepassage_evaluation/). Throughout the guide, the ![example](./figures/example_icon.png){: height="36px" width="36px"} icon will take you to relevant files and folders of the examplary data analysis, such that you can see it all in action.

[Let's dive right in and set up the software.](./preparation/programming_environment)