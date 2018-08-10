---
title: Overview
layout: page
image: /figures/simon-abrams-286276-unsplash_cropped.jpg
---
<a style="background-color:black;color:white;text-decoration:none;padding:4px 6px;font-family:-apple-system, BlinkMacSystemFont, &quot;San Francisco&quot;, &quot;Helvetica Neue&quot;, Helvetica, Ubuntu, Roboto, Noto, &quot;Segoe UI&quot;, Arial, sans-serif;font-size:12px;font-weight:bold;line-height:1.2;display:inline-block;border-radius:3px" href="https://unsplash.com/@flysi3000?utm_medium=referral&amp;utm_campaign=photographer-credit&amp;utm_content=creditBadge" target="_blank" rel="noopener noreferrer" title="Download free do whatever you want high-resolution photos from Simon Abrams"><span style="display:inline-block;padding:2px 3px"><svg xmlns="http://www.w3.org/2000/svg" style="height:12px;width:auto;position:relative;vertical-align:middle;top:-1px;fill:white" viewBox="0 0 32 32"><title>unsplash-logo</title><path d="M20.8 18.1c0 2.7-2.2 4.8-4.8 4.8s-4.8-2.1-4.8-4.8c0-2.7 2.2-4.8 4.8-4.8 2.7.1 4.8 2.2 4.8 4.8zm11.2-7.4v14.9c0 2.3-1.9 4.3-4.3 4.3h-23.4c-2.4 0-4.3-1.9-4.3-4.3v-15c0-2.3 1.9-4.3 4.3-4.3h3.7l.8-2.3c.4-1.1 1.7-2 2.9-2h8.6c1.2 0 2.5.9 2.9 2l.8 2.4h3.7c2.4 0 4.3 1.9 4.3 4.3zm-8.6 7.5c0-4.1-3.3-7.5-7.5-7.5-4.1 0-7.5 3.4-7.5 7.5s3.3 7.5 7.5 7.5c4.2-.1 7.5-3.4 7.5-7.5z"></path></svg></span><span style="display:inline-block;padding:2px 3px">Simon Abrams</span></a>


**ATTENTION**: This is a work in progress and subject to major changes.

In 2016, the journal *Nature* published a [poll](https://www.nature.com/news/1-500-scientists-lift-the-lid-on-reproducibility-1.19970?WT.mc_id=SFB_NNEWS_1508_RHBox) of more than 1,500 researchers from various fields who were questioned on the topic of reproducibility. Over 70% have attempted to replicate another researcher's experiment and have failed. More than half could not reproduce their own findings.

When asked, what where the factors that contribute to irreproducible research, among the top factors where technical barriers of code or raw data not being available and that there is a lot of technical expertise required for reproducing the results.

This website presents a basic workflow which makes your next data analysis reproducible by others with minimal effort. I believe that reproducible research is important out of two key reasons. The first one is credibility:

>*“Only results that can be replicated are truly scientific results. If there is no chance to replicate
research results, they can be regarded as no more than personal views in the opinion or review
section of a daily newspaper.”* - [Huschka (2013)](https://www.ratswd.de/dl/RatSWD_WP_216.pdf){:target="_blank"}

The other one is the reason of enabling future research to build upon existing one instead of creating the need to first painfully recreate what has already been done.

## Tools
This guide is primarily written for Python and R users. Both languages are open-source, which greatly helps in making your research reproducible. Furthermore, they have huge ecosystems of extensions and tutorials. However, most of the tools and practices advertised should work with other commonly used languages for data analysis such as Stata, Julia, Scala, C++, or Matlab.

If you want to use either Python or R and are completely new to it, I recommend that you first get up to speed with [these tutorials](/beginner_resources) before continuing with this guide. In the section on "Programming environment" I'll also go into the details on setting up Python and R in a way which is favorable for reproducible research.

## Content
The guide is split into three parts.

1. [Preparation and setup](./preparation/)
2. [During the analysis](./during_the_analysis/)
3. [Sharing your work](./sharing_your_work/)

Furthermore, I compiled a [list of tutorials and documentations](/where_to_go_next) which go more in-depth on reproducible research.

You can always use the navigation button on the top right of the page to switch between the sections.

## About
This website is part of my thesis for obtaining a Master of Arts in Economics (major) and Data Science (minor) at the University of Zurich. The second part is an evaluation of the effectiveness of a crime prevention program in Chicago. You can find an overview of the analysis [here](https://binste.github.io/chicago_safepassage_evaluation/). The code in the corresponding [GitHub repository](https://github.com/binste/chicago_safepassage_evaluation) can be seen as an example for the practices I'll advertise in this guide. Throughout the guide, the ![example](./figures/example_icon.png){: height="36px" width="36px"} icon will take you to relevant files and folders such that you can see it all in action.
