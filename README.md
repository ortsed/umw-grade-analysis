## Analysis of Grade Distributions of the University of Wisoncsin, Madison.

As part of our second project on hypothesis testing for Flatiron, we chose to look at the Kaggle dataset on grades from the University of Wisconsin.

Data is available here: https://www.kaggle.com/Madgrades/uw-madison-courses#course_offerings.csv

On preview of the data, we assembled a few hypotheses for potential analysis:

1. if STEM fields had different grade distributions than traditional liberal arts subjects
2. Did large classes (more than 32 students, which is the 75th percentile of enrollment) had different grade distribution than smaller classes, 3. Does the time of day (before or after lunch) make a difference in grades, 
4. Has there been a change in grade distributions over the 10 years of the dataset. 

After loading the data in via the sqlite database included in the distribution into pandas, we did some preliminary analysis and cleaning.

In the grade_distributions table, grade counts were cast as ints. Based on a description of grades (A-F, NW, etc..) found on the UW's registrar site, we compiled a total enrollment based on the total grades reported for each class.

More than 100,000 or 52% classes have zero grades, which is the proxy for class enrollment. After some investigation based on the class names, most of these referred to "research" and "independent study" potentially related to non-graded graduate level work.

These numbers did not affect grade distribution and were not relevant to our analysis and were therefore dropped.

Using the registrars guide for calcuating a numerical value for certain grades, and ignoring grades without a definitive value (e.g. incomplete), we calculated a cumulative grade point for the class (e.g. 4 * num_of_a + 3 * num_of_b...). And then a class GPA was calculated.

Also, a percentage of grade for the class was calculated for each grade. E.g. percentage of A per class.

For each hypothesis, we plotted distributions, calculated t-tests, and effect sizes.

TKTK


