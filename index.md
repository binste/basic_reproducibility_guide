---
title: Overview
header:
    overlay_image: /figures/simon-abrams-286276-unsplash_cropped.jpg
    caption: "<small>Photo credit: [Simon Abrams](https://unsplash.com/photos/k_T9Zj3SE8k)</small>"
permalink: ./
author_profile: true
share: true
toc: false
sidebar: false
classes: wide
---
**ATTENTION**: This is a work in progress and subject to major changes.

In 2016, the journal *Nature* published a [poll](https://www.nature.com/news/1-500-scientists-lift-the-lid-on-reproducibility-1.19970?WT.mc_id=SFB_NNEWS_1508_RHBox) of more than 1,500 researchers from various fields who were questioned on the topic of reproducibility. Over 70% have attempted to replicate another researcher's experiment without success. More than half could not even reproduce their own findings. When asked, what where the factors that lead to irreproducibility of research, among the top reasons were the lack of availability of code and raw data, as well as that a lot of technical expertise is often required for reproduction. With a focus on these factors, this guide will show you a minimal set of tools and practices to help you make your next data analysis reproducible. I believe that reproducible research is important out of two key reasons. The first one is credibility:

>*“Only results that can be replicated are truly scientific results. If there is no chance to replicate
research results, they can be regarded as no more than personal views in the opinion or review
section of a daily newspaper.”* - [Huschka (2013)](https://www.ratswd.de/dl/RatSWD_WP_216.pdf){:target="_blank"}

The second one is the reason of enabling future research to build upon existing work.

>*"If I have seen further it is by standing on the shoulders of Giants."* - Isaac Newton (1675)

At the end of this guide, you'll know how to set up your project in a way that others will be able to easily access it, replicate your findings, as well as build upon them, and all of this with as less effort as possible, for them as well as for yourself. First, we will set up a good development environment and organize our project folder in a way, which should hopefully still allow to call it *structured* by the end of the project. You'll then learn how to put your project under version control. Among other benefits, this should put an end to file names like `estimate_finalV2_superfinal.R`. Next up is writing good and up-to-date documentation as well as some other practices you should adhere to while doing your analysis. Wait! Before you go on YouTube, this isn't as boring as it sounds. *<small>Even if it would be, I wouldn't tell you now, as it is one of the most important things, especially for yourself.</small>* Last but not least, it will be time to let everyone in on the fun and enjoy the awesome project you have created. They'll be able to rerun your code until their CPU's melt (if they want to). Or they can just run some of it in the cloud, for free, without any setup (seems like there is such a thing as a free lunch after all).

## Tools
This guide is primarily written for Python and R users, due to the fact that both languages and corresponding interpreters are open-source and available for free, which already greatly helps in making your research reproducible. They also have huge ecosystems of packages, which provide great functionality from data preparation over visualization to modeling. It certainly also helps that there is a vast sea of tutorials out there for both languages to answer almost all the questions you will have. In general, however, most of the tools and practices advertised in this guide also work with other commonly used (and some of them also freely available) languages for data analysis such as Stata, Julia, Scala, C++, or Matlab.

If you want to use either Python or R and are completely new to it, I recommend that you first get up to speed with some of these [tutorials](/beginner_resources) before continuing with the guide.

## Showing is better than telling
Next to this website, I created a data analysis using Python, where I look at geo-tagged crime data, to assess the effectiveness of a crime prevention program in Chicago. Throughout this guide, I will use the analysis as an example to showcase the tools and practices advertised, such that you can see them directly applied on a project. If you are interested, you can find an overview of the analysis [here](https://binste.github.io/chicago_safepassage_evaluation/){:target="_blank"}, however, it is not required for the rest of this guide.

[Let's dive right in and set up the software.](./preparation/development_environment)