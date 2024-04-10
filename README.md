**Analyze Death Age Difference of Right Handers with Left Handers**


**Project Description**

In this project, you will explore this phenomenon using age distribution data to see if we can reproduce a difference in average age at death purely from the changing rates of left-handedness over time, refuting the claim of early death for left-handers. This notebook uses pandas and Bayesian statistics to analyze the probability of being a certain age at death given that you are reported as left-handed or right-handed.



**EXPERIMENT AND RESULT**

1. Male and Female Left-Handedness Rates vs. Age:

![C:\Users\Asus\AppData\Local\Microsoft\Windows\INetCache\Content.MSO\E77CB095.tmp](Aspose.Words.a15ba326-5dac-4f56-b9b4-7080dafdbe6b.001.png)





















- In this visual representation, we observe the scatter plot, which demonstrates the left-handedness rates for both males and females across different age groups.
- The plot reveals the distribution of left-handedness within the population across age brackets. It allows us to discern whether there are any age-related patterns in handedness.
- By labelling the axes and incorporating a legend, the plot becomes more interpretable, enabling us to distinguish between the male and female data points. This distinction is valuable for understanding potential gender-based differences in handedness.
1. Rates of Left-Handedness Over Time:

   ![C:\Users\Asus\AppData\Local\Microsoft\Windows\INetCache\Content.MSO\A477846B.tmp](Aspose.Words.a15ba326-5dac-4f56-b9b4-7080dafdbe6b.002.png)


- This plot showcases the temporal evolution of left-handedness rates by computing the mean of male and female left-handedness rates across various birth years. 
- It provides insights into how the prevalence of left-handedness has potentially changed over time, offering a historical perspective on handedness trends. 
- The plot's trend line enables us to identify whether left-handedness has shown any significant shifts or fluctuations across different birth cohorts. 


1. Applying Bayes' rule

   The probability of dying at a certain age given that you're left-handed is not equal to the probability of being left-handed given that you died at a certain age. This inequality is why we need Bayes' theorem, a statement about conditional probability which allows us to update our beliefs after seeing evidence.

   We want to calculate the probability of dying at age A given that you're left-handed. Let's write this in shorthand as P(A | LH). We also want the same quantity for right-handers: P(A | RH).

   Here's Bayes' theorem for the two events we care about: left-handedness (LH) and dying at age A.


   ![](Aspose.Words.a15ba326-5dac-4f56-b9b4-7080dafdbe6b.003.png)

   P(LH | A) is the probability that you are left-handed given that you died at age A. P(A) is the overall probability of dying at age A, and P(LH) is the overall probability of being left-handed. We will now calculate each of these three quantities, beginning with P(LH | A).


1. Death Distribution Data for the United States in 1999

   ![C:\Users\Asus\AppData\Local\Microsoft\Windows\INetCache\Content.MSO\1AFE44B1.tmp](Aspose.Words.a15ba326-5dac-4f56-b9b4-7080dafdbe6b.004.png)

















- The plot representing death distribution data for the United States in 1999 offers an overview of the ages at which individuals passed away during that year. 
- It provides a visual representation of the distribution of ages at death, shedding light on the demographic aspects of mortality in that specific time frame. 
- This analysis is foundational for understanding the typical age at which people passed away during the year 1999, offering context for assessing the age distribution within the population. 

1. The overall probability of left-handedness

In the previous code block we loaded data to give us P(A), and now we need P(LH). P(LH) is the probability that a person who died in our particular study year is left-handed, assuming we know nothing else about them. This is the average left-handedness in the population of deceased people, and we can calculate it by summing up all of the left-handedness probabilities for each age, weighted with the number of deceased people at each age, then divided by the total number of deceased people to get a probability. In equation form, this is what we're calculating, where N(A) is the number of people who died at age A (given by the dataframe death\_distribution\_data):

![](Aspose.Words.a15ba326-5dac-4f56-b9b4-7080dafdbe6b.005.png)


![](Aspose.Words.a15ba326-5dac-4f56-b9b4-7080dafdbe6b.006.png)

1. Putting it all together: dying while left-handed (i)

   Now we have the means of calculating all three quantities we need: P(A), P(LH), and P(LH | A). We can combine all three using Bayes' rule to get P(A | LH), the probability of being age A at death (in the study year) given that you're left-handed. To make this answer meaningful, though, we also want to compare it to P(A | RH), the probability of being age A at death given that you're right-handed.

   We're calculating the following quantity twice, once for left-handers and once for right-handers.

   ![](Aspose.Words.a15ba326-5dac-4f56-b9b4-7080dafdbe6b.007.png)




1. Putting it all together: dying while left-handed (ii)


1. Probability of Age at Death Given Handedness:

   ![C:\Users\Asus\AppData\Local\Microsoft\Windows\INetCache\Content.MSO\205C5AE7.tmp](Aspose.Words.a15ba326-5dac-4f56-b9b4-7080dafdbe6b.008.png)





















- The probability plots reveal the distributions of ages at death for left-handed and right-handed individuals. They offer insights into the likelihood of reaching specific ages at death based on handedness. 
- By contrasting the probability distributions for the two groups, the plots facilitate the identification of potential disparities in age at death between left-handed and right-handed individuals. 
- This analysis underscores the relevance of handedness as a factor in mortality studies, potentially challenging or confirming prevailing assumptions about its impact on the lifespan. 

These visual representations and analyses are essential for extracting meaningful insights from the data, enabling us to draw conclusions and contribute to the overarching research question of whether there is a significant age difference between left-handers and right-handers.

1. Moment of truth: age of left and right-handers at death

   Finally, let's compare our results with the original study that found that left-handed people were nine years younger at death on average. We can do this by calculating the mean of these probability distributions in the same way we calculated P(LH) earlier, weighting the probability distribution by age and summing over the result.

   ![](Aspose.Words.a15ba326-5dac-4f56-b9b4-7080dafdbe6b.009.png)






   ![](Aspose.Words.a15ba326-5dac-4f56-b9b4-7080dafdbe6b.010.png)





1. We got a pretty big age gap between left-handed and right-handed people purely as a result of the changing rates of left-handedness in the population, which is good news for left-handers: you probably won't die young because of your sinister ness. The reported rates of left-handedness have increased from just 3% in the early 1900s to about 11% today, which means that older people are much more likely to be reported more right-handed than left-handed, and so looking at a sample of recently deceased people will have more old right-handers.

   Our number is still less than the 9-year gap measured in the study. It's possible that some of the approximations we made are the cause:

- We used death distribution data from almost ten years after the study (1999 instead of 1991), and we used death data from the entire United States instead of California alone (which was the original study).
- We extrapolated the left-handedness survey results to older and younger age groups, but it's possible our extrapolation wasn't close enough to the true rates for those ages.

One thing we could do next is figure out how much variability we would expect to encounter in the age difference purely because of random sampling: if you take a smaller sample of recently deceased people and assign handedness with the probabilities of the survey, what does that distribution look like? How often would we encounter an age gap of nine years using the same data and assumptions? We won't do that here, but it's possible with this data and the tools of random sampling.

To finish off, let's calculate the age gap we'd expect if we did the study in 2018 instead of in 1990. The gap turns out to be much smaller since rates of left-handedness haven't increased for people born after about 1960. Both the National Geographic study and the 1990 study happened at a unique time - the rates of left-handedness had been changing across the lifetimes of most people alive, and the difference in handedness between old and young was at its most striking.

![](Aspose.Words.a15ba326-5dac-4f56-b9b4-7080dafdbe6b.011.png)




CONCLUSION

From the analysis conducted, we can see that left-handers experience an earlier average age of death than right – handers.





























