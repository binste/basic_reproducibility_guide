---
title: Introduction
header:
    overlay_image: /figures/rayi-christian-wicaksono-366-unsplash_cropped.jpg
    caption: "<small>Photo credit: <a href='https://unsplash.com/photos/6PF6DaiWz48' target='_blank'>Rayi Christian Wicaksono</a></small>"
permalink: ./
share: true
toc: false
classes: wide
---
In 2016, the journal *Nature* published a [poll](https://www.nature.com/news/1-500-scientists-lift-the-lid-on-reproducibility-1.19970?WT.mc_id=SFB_NNEWS_1508_RHBox) of more than 1,500 researchers from various fields who were questioned on the topic of reproducibility in research. Over 70% stated that they have attempted to replicate another researcher's experiment -- without success. More than 50% could not even reproduce their own findings. When asked about the factors that lead to research being irreproducible, one of the top reasons stated was the lack of availability of the methods and code used, with more than 80% stating that this always, often, or at least sometimes contributes to irreproducibility. Focusing on exactly this factor, this guide will teach you the basic tools and practices necessary to make the data analysis component of your next research project reproducible, both for you and for others.

You may ask yourself, is this really necessary for me? Is it really *that* important to focus on reproducibility in this specific thesis/dissertation/paper? Sure, not all of our research ends up in a reproducibility study in *Nature*. Maybe you think your research most likely won't be used and reproduced by other researchers anyway, so why bother reading on to the next page? The answer is simple: Reproducibility is not just a standard to which we hold science's greatest and most important discoveries. It is a foundation of scientific research itself:

>*“Only results that can be replicated are truly scientific results. If there is no chance to replicate
research results, they can be regarded as no more than personal views in the opinion or review
section of a daily newspaper.”* - [Huschka (2013)](https://www.ratswd.de/dl/RatSWD_WP_216.pdf){:target="_blank"}

But if you want a more tangible reason than that: I'm convinced that following the practices illustrated throughout this guide will not only make your research more reproducible, it will also make your life a whole lot easier. You'll be more organized, make fewer mistakes, and save time.

At the end of this guide, you'll know how to set up your project in a way that others will be able to easily access it, replicate your findings, as well as build upon them -- and all of this with as little effort as possible, for both them and for yourself. First, you will set up a good development environment and organize your project folder in a way that allows you to actually stick to the structure right until the end of your project. We'll then learn how to put the project under version control. Among many other benefits, this practice will finally put an end to the chaos of file names like `estimate_final_FINAL_v2_superfinal.R`. Next up will be writing and maintaining good documentation of your code and data, followed by some further practices you should adhere to while doing your analysis. Last but not least, it will be time to let everyone in on the fun and enjoy the awesome project you have created and we will look at how to present your research project online and host it for free. Others will then be able to download your code and rerun it until their CPUs melt. Or they can even run some of it in the cloud, for free, without any setup (seems like there is such a thing as a free lunch after all).

## Tools
This guide is primarily written for Python and R users, due to the fact that both languages and corresponding interpreters are open-source and available for free, which already greatly helps in making your research reproducible. They also have huge ecosystems of packages that provide great functionality, from data preparation over visualization to modeling. It certainly also helps that there is a vast sea of tutorials out there for both languages to answer almost all the questions you will ever have. In general, however, most of the tools and practices advertised in this guide also work with other commonly used (and some of them also available for free) languages for data analysis such as Stata, Julia, Scala, C++, or Matlab.

If you want to use Python or R but are completely new to it at this point, I recommend that you first get up to speed with some of these [tutorials](beginner_resources) before continuing with the guide.

## Showing is better than telling
I find it always extremely helpful to see a concept demonstrated on a practical example. That is why I created a data analysis as an example research project and throughout the guide, I will use parts of it to directly show how the advertised tools and practices could be used in a real application.

The project, using Python, estimates the effect of Chicago's Safe Passage program on crime counts. The program aims at keeping students safe on their way to school by posting civilian guards along various routes to the participating schools. In the spirit of reproducible research, the example analysis itself is a replication of parts of an existing paper called ["Do More Eyes on the Street Reduce Crime? Evidence from Chicago’s Safe Passage Program"](https://ignaciomsarmiento.github.io/assets/Safe_Passage_WP.pdf) by Daniel McMillen, Ignacio Sarmiento-Barbieri, and Ruchi Singh from June 22, 2017.

If you are interested, you can find an introduction to the example project [here](example_project/introduction){:target="_blank"}, however, it is not required for the rest of this guide.

[Let's dive right into the guide and set up some tools.](./preparation/development_environment)