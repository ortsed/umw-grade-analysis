## Analysis of Grade Distributions of the University of Wisoncsin, Madison.

As part of our second project on hypothesis testing for Flatiron, we chose to look at the Kaggle dataset on grades from the University of Wisconsin.

Data is available here: https://www.kaggle.com/Madgrades/uw-madison-courses#course_offerings.csv

On preview of the data, we assembled a few hypotheses for potential analysis:

1. if STEM fields had different grade distributions than traditional liberal arts subjects
2. Did large classes (more than 32 students, which is the 75th percentile of enrollment) had different grade distribution than smaller classes, 
3. Does the time of day (before or after lunch) make a difference in grades, 
4. Has there been a change in grade distributions over the 10 years of the dataset. 

After loading the data in via the sqlite database included in the distribution into pandas, we did some preliminary analysis and cleaning.

In the grade_distributions table, grade counts were cast as ints. Based on a description of grades (A-F, NW, etc..) found on the UW's registrar site, we compiled a total enrollment based on the total grades reported for each class.

More than 100,000 or 52% classes have zero grades, which is the proxy for class enrollment. After some investigation based on the class names, most of these referred to "research" and "independent study" potentially related to non-graded graduate level work.

These numbers did not affect grade distribution and were not relevant to our analysis and were therefore dropped.

Using the registrars guide for calcuating a numerical value for certain grades, and ignoring grades without a definitive value (e.g. incomplete), we calculated a cumulative grade point for the class (e.g. 4 * num_of_a + 3 * num_of_b...). And then a class GPA was calculated.

Also, a percentage of grade for the class was calculated for each grade. E.g. percentage of A's per class.

For the first question on STEM grade distributions, we imported class categories from the National Science Foundation and H1B classifications. Classes that matched the list of classes listed categories in those STEM categories were classified as STEM, although there is some potential inaccuracy in this designation.

For each hypothesis, we plotted distributions, calculated t-tests, and effect sizes. For the first and third hypotheses, distributions did not differ in any substantial way and we moved on to the other questions.

For class size, class size was separated out by the 75th percentile for class size, largely to get a substantially even split in sample sizes and to get a good cutoff in midrange of class size. The distribution was substantially different and used Central Limit theorem to further analyze differences. Additionally, distribution of grade percentages—percent of a class with a particular grade—were plotted to show the skewed effect of small classes handing out all A's to a class.

To account for potential misrepresentation of averages of small classes, since small classes represent small samples, similar calculations and plots were made for sample GPAs. That is, rather than averaging the GPA of each class over a sample (an average of an average), total sample GPA was used to better represent the sample's average. This corrected the distribution and means, but the end result was still the same. Small classes differed from larger ones in grade distribution.

And finally, t-values were plotted for different cutoffs in class size, from 32 students per class down to 5. The plot showed a large change happening around 6-8 students per class.

For yearly change, medians, means, and distributions were plotted for each year, showing all three increasing on a yearly basis. Further analysis showed support for the idea that the distributions of each year differed, but effect size was small and p-values were just under the alpha.

ANOVA was used to compare coefficients with respectable f-values and distinct coefficients, but because the effect size was still so small and without a better understanding as to what might constitute "grade inflation" , we held out on making a firm determination.






