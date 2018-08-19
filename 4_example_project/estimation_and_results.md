---
title: Example project - Strategy and results
permalink: /example_project/estimation_and_results
header:
    overlay_image: /figures/accident-barrier-caution-923681_cropped.jpg
    caption: "<small>Photo credit: [Kat Wilcox](https://www.pexels.com/photo/crime-scene-do-not-cross-signage-923681/)</small>"
---
## Strategy
In the movie "Sliding Doors" (1998)[^2], we see the life of Helen in two versions. In one of them, she catches a subway train; in the other one, she misses it by a split second. What unfolds are two completely different stories of her future, and you as a viewer can see both. The movie director therefore allows us to compare the two futures of Helen and derive the exact causal effect for Helen of catching that very train. Unfortunately, when analyzing a policy such as the Safe Passage program, observing an alternate universe, where the program was never implemented, is of course impossible. If it were, policy analysis would be a piece of cake. We have to resort to finding a proxy for the unobservable scenario. Of course we will never know how good our chosen proxy really is, but statisticians have developed techniques that allow us to circumvent some of the pitfalls.

### Difference in differences
In this analysis, instead of observing the life of Helen, we will follow the evolution of violent-crime counts. The crime count data points we'll be working with are aggregated by census block in Chicago and by month per school year between January 2006 and June 2016 (click on the "launch binder" badge in the [Introduction](./introduction) if you're interested in looking at the aggregation in more detail). This time frame allows for observing the evolution of crime in Chicago even before the start of the Safe Passage program in 2009 -- a data feature that will be very helpful for identifying the effect of the program with the chosen strategy. In the following, I will try to describe this strategy and convey the intuition behind it with a little example.

Let us imagine a fictional census block which intersects with street frequently used by kids to get to and from school. Due to various crime incidents, at the start of the school year 2012-2013, the City of Chicago implemented the Safe Passage program for this very street, meaning that civilian guards protect the children on their way to school. In our analysis, we would then mark this census block as "treated" (i.e. directly affected by the program) for all subsequent months. If we want to know the effect of the guards, one idea could be to compare average crime counts per month before and after the program was implemented. Let's say we observe a reduction of 2 violent crimes per month. This scenario is shown with the blue line in the figure below (ignore the red lines for now).

*<font size="-1">Figure 4 - Illustration of DiD example</font>*
![did_illustration](../figures/didfigure.png)
{: .full}
*<font size="-1">"Before" and "After Implementation" refer to the months prior and after the implementation of the Safe Passage program in the "treated" block.<br />
Data source: Example from text</font>*

However, as mentioned at the beginning with the example of Helen and the train, we do not know what would have happened if the program had never been implemented. Maybe there would have been a reduction of 2 crimes anyway, for example due to some other program or initiative, meaning that the Safe Passage program actually had no effect whatsoever. Or maybe there would have been an increase by 3 violent crimes if the program had never started, meaning that it actually prevented 5 violent crimes per month, not 2. This is where the above mentioned proxy comes into play. The key idea behind the empirical approach used in this analysis is that other census blocks, which do not intersect with a Safe Passage route in a given month, can be used to as a proxy for what would have happened in the treated census block in absence of the program. Let's continue with the example from above and imagine a second census block (we'll call it a "control block") which never received a Safe Passage route. Assume that this control block experienced a decrease in crime counts of 1 crime per month, when comparing the same before and after months as for the treated block (i.e. before and after the beginning of the school year 2012-2013). In the above figure, this is depicted as the solid red line.

If we are confident that the control block is a good proxy for the treated block without the Safe Passage program, we can now assume that the treated block would also have experienced a decrease in crime counts of 1 crime per month (had the program never been implemented). This kind of assumption is generally referred to as the "parallel trends assumption." The assumed counterfactual scenario is depicted by the dashed red line in the figure. The implication then is that 1 of the on average 2 prevented crimes in the treated block is due to the program, while the other one is due to other factors which affected both the control block and the treated block (such as, for example, a city-wide program to prevent crime). Simply comparing before and after for the treated block (i.e. the blue line) would therefore lead us to a wrong conclusion about the causal effect of the Safe Passage program. What gives us a much better guess for its effect is to also take into account the before-after comparison of the control block by taking the difference in the trends of the blue line and the dashed red line.

This approach is generally referred to as difference in differences (DiD): What is the *difference* between the two *before-after differences* for the two blocks?  How close the estimated effect of the DiD approach is to the unobservable truth depends on how well the crime trend for the control block represents the unobservable crime trend that the treated block would have experienced in absence of the Safe Passage program.

### Finding good control blocks
As mentioned in the Introduction, Safe Passage routes are predominantly implemented in high-crime, low-income, and segregated neighborhoods.[^1] Therefore, by picking control blocks at random from all blocks in Chicago, you might end up comparing fundamentally different areas. You'll have a hard time convincing people that the poorer neighborhoods of Chicago can be compared to some of the richer ones regarding crime trends. They are fundamentally different in many factors, not just income levels, which can influence crime patterns -- racial-ethnic heterogeneity could be an example. To be more confident in the comparability of treated and control blocks, McMillen et al. (2017)[^1] choose those census blocks as controls that lie right next to the treated ones. This should lead to the control blocks having similar demographic characteristics as their treated counterparts. It might therefore be more reasonable to assume that the trends of treated and control blocks would have been approximately the same in the absence of the implementation of the crime prevention program, compared to the more naive approach of picking control blocks at random from all available ones.

McMillen et al. (2017)[^1] further subdivide the control blocks into three groups. A block which itself is not treated but is adjacent to a treated block is called a "One over" block. A block which has a "One over" block between itself and a "treated" block will be called "Two over." The same logic applies for "Three over" blocks.

*<font size="-1">Figure 5 - Illustration of block categorization</font>*
![block_groups](../figures/blockgroups.png)
{: .full}
*<font size="-1">Example using the Safe Passage route of Bogan High School in the school year 2013-2014 as well as the surrounding blocks.<br />
Data sources: See the section "Data" in the <a href="https://github.com/binste/chicago_safepassage_evaluation/tree/master/reports/appendix/Appendix.pdf" target="_blank">Appendix</a></font>.*

This categorization of control blocks allows to not only more accurately assess the effect of the program on the treated blocks, but also to analyze possible displacement effects. If such effects would be present, crimes might not be prevented, but simply happen in areas close by, where the guards can't see them. The following figure shows the number of blocks over the school years that are labelled as belonging to one of the four block categories. You can see the big expansion of the program in the school year 2013-2014, which I had mentioned in the introduction.

*<font size="-1">Figure 6 - Number of treated and control blocks per school year</font>*
![block_trend](../figures/blocktrend.png)
{: .full}
*<font size="-1">Data sources: See the section "Data" in the <a href="https://github.com/binste/chicago_safepassage_evaluation/tree/master/reports/appendix/Appendix.pdf" target="_blank">Appendix</a></font>.*

To get a feeling for how good the comparability of treatment and control units is, we can look at the evolution of crime counts before the implementation. As the approach relies on the crime count trends of control and treated blocks to be approximately the same in absence of treatment, it is reassuring if the pre-treatment trends are similar. The following figure visualizes average violent-crime counts per block per weekday. The school years on the horizontal axis are relative to the implementation of the Safe Passage program of the corresponding "Treated" block (each control block has the closest treated block assigned to it).

*<font size="-1">Figure 7 - Difference in differences plot for violent crimes</font>*
![did_violent](../figures/didfigureviolent.png)
{: .full}
*<font size="-1">To create this figure, each block needs to be assigned to exactly one group. The data used here is therefore not exactly representative of the one used in the final estimation of the effect, as there, blocks are allowed to change their status. They can for example first be a "Two over" block and then become a "One over" block, if a Safe Passage route gets implemented in an adjacent block. However, this can be seen as a close approximation.<br />
This figure is an approximate replication of Figure 3a in McMillen et al. (2017)<br />
Data sources: See the section "Data" in the <a href="https://github.com/binste/chicago_safepassage_evaluation/tree/master/reports/appendix/Appendix.pdf" target="_blank">Appendix</a></font>.*

When looking at the overall level of the crime counts, treated blocks do suffer from more incidents then the control blocks. Therefore, even though the control blocks are right next to the treated blocks, they are not comparable in terms of the number of incidents. This again confirms that the Safe Passage program was implemented primarily in high-crime areas. However, as mentioned before, what we need for the difference-in-difference approach to make sense is that the *changes* in crime over time would be similar in absence of treatment.

**Note**: The average areas of treatment and control blocks are very similar and can therefore not be the cause for the level difference in crime counts in Figure 7 and Figure 8.
{: .notice}

We see that the changes in crime counts are quite similar between the different block categories before the implementation of the program, with slightly stronger differences between treatment and control blocks from the 4th to the 5th school year prior to the implementation. In the first school year after the implementation of the program, we see a drop in crime counts for the treated blocks. No such jump is visible for the three control block categories.

*<font size="-1">Figure 8 - Difference in differences plot for property crimes</font>*
![did_property](../figures/didfigureproperty.png)
{: .full}
*<font size="-1">To create this figure, each block needs to be assigned to exactly one group. The data used here is therefore not exactly representative of the one used in the final estimation of the effect, as there, blocks are allowed to change their status. They can for example first be a "Two over" block and then become a "One over" block, if a Safe Passage route gets implemented in an adjacent block. However, this can be seen as a close approximation.<br />
This figure is an approximate replication of Figure 3b in McMillen et al. (2017)<br />
Data sources: See the section "Data" in the <a href="https://github.com/binste/chicago_safepassage_evaluation/tree/master/reports/appendix/Appendix.pdf" target="_blank">Appendix</a></font>.*

When we look at property crimes in Figure 8, we again see rather similar pre-treatment trends (the exceptions are the 5th and 4th school year prior to the implementation). However, visually there is no clue that the implementation led to an effect on property crime, since all groups experienced a similar downwards trend.

In order to quantify the effects (or lack thereof) that we can now see in the figures, I followed McMillen et al. (2017) and used a so-called Poisson regression. This approach is particularly useful given the nature of the outcome variable, a count variable. Details on the specification can be found in the [Appendix](https://github.com/binste/chicago_safepassage_evaluation/tree/master/reports/appendix/Appendix.pdf){:target="_blank"} in the section "Empirical Strategy."

## Results
Following the estimation strategy used in McMillen et al. (2017), I found that the Safe Passage program reduces violent crime by 12.5% on average between 6.30am and 5.30pm for the week days of a school year. The result is therefore very similar to the findings in the original paper, where a 13.4% reduction was estimated. Furthermore, no displacement effects to the adjacent areas were found, neither by McMillen et al. (2017) nor by me. Similarly, both estimations find no evidence of a reduction in crime for property crime.

All in all this speaks for a rather successful replication of their findings regarding the effect of the Safe Passage program on crime on the level of census blocks. A more detailed comparison of the main results and the figures presented here can be found by clicking on the "launch binder" badge in the Introduction to the example project.

Of course a thorough policy evaluation contains much more than the part I replicated for this project. The paper by McMillen, Sarmiento-Barbieri, and Singh includes various further analyses (like an analysis of the effect of the program on attendance rates or a cost-benefit analysis of the program) and robustness checks.

Again, I would like to refer to the [Appendix](https://github.com/binste/chicago_safepassage_evaluation/tree/master/reports/appendix/Appendix.pdf){:target="_blank"} for more details on McMillen et al. (2017), the data, the empirical strategy, and the results. The code, data, and further instructions on how to reproduce the analysis are available in the corresponding [GitHub repository](https://github.com/binste/chicago_safepassage_evaluation){:target="_blank"}.

## References
[^1]: [Do More Eyes on the Street Reduce Crime? Evidence from Chicago’s Safe Passage Program; June 22, 2017; accessed on April 6, 2018](https://ignaciomsarmiento.github.io/assets/Safe_Passage_WP.pdf){:target="_blank"}
[^2]: [Sliding Doors (1998) - imdb.com; accessed on August 2, 2018](https://www.imdb.com/title/tt0120148/){:target="_blank"}