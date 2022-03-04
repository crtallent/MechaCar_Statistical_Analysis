# MechaCar_Statistical_Analysis

## Overview

For this project, we are tasked with performing the following objectives:

* Perform multiple linear regression analysis to identify which variables in the dataset predict the mpg of MechaCar prototypes
* Collect summary statistics on the pounds per square inch (PSI) of the suspension coils from the manufacturing lots
* Run t-tests to determine if the manufacturing lots are statistically different from the mean population
* Design a statistical study to compare vehicle performance of the MechaCar vehicles against vehicles from other manufacturers. 

## Resources
* Sofware: RStudio 2022.02.0+443

* Data Sources: MechaCar_mpg.csv, Suspension_Coil.csv


### Linear Regression to Predict MPG

In our [multiple linear regression results](https://github.com/crtallent/MechaCar_Statistical_Analysis/blob/main/Challenge/Images/lm%20sum.png), we see that roughly 71% of our variability can be explained by this linear model.  This indicates that there is a 71% likelihood that this data would represent real-world data points.  The variables that provided a non-random amount of variance to the MPG values in the dataset were vehicle_length and ground_clearance, at 2.60e12 and 5.21e-08, respectively.  The below image shows the detailed results of our multiple linear regression model:

<img src="https://github.com/crtallent/MechaCar_Statistical_Analysis/blob/main/Challenge/Images/lm%20sum.png"/>

In this case, the slope of our linear model is not considered to be zero, as we can see a significant linear relationship between MPG and our vehicle_length and ground_clearance variables.  Additionally, our p-value (5.35e-11) is smaller than 0.05, so we have sufficient evidence to reject our null hypothesis that there is no relationship between MPG and our other variables.  However, this linear model may not effectively predict MPG of MechaCar prototypes effectively due to the lack of significant variables in our dataset.  In other words, there is a likelihood that we may be seeing overfitting, and our model may not work as well in the future to predict data.  It would be advised to add other variables into our linear regression model to gain a better understanding of everything that is impacting MPG for future predictions.

### Additional Images - Linear Regression Plots

<p float="left">
  <img src="https://github.com/crtallent/MechaCar_Statistical_Analysis/blob/main/Challenge/Images/length.png" alt="Vehicle Length Linear Regression Plot" style="height: 300px; width:300px;"/>
 <img src="https://github.com/crtallent/MechaCar_Statistical_Analysis/blob/main/Challenge/Images/ground_clearance.png" alt="Ground Clearance Linear Regression Plot" style="height: 300px; width:300px;"/> 
 <img src="https://github.com/crtallent/MechaCar_Statistical_Analysis/blob/main/Challenge/Images/plot.png" alt="Multiple Variable Regression Plot" style="height: 300px; width:300px;"/> 
 <img src="https://github.com/crtallent/MechaCar_Statistical_Analysis/blob/main/Challenge/Images/leverage.png" style="height: 300px; width:300px;"/>  
 <img src="https://github.com/crtallent/MechaCar_Statistical_Analysis/blob/main/Challenge/Images/Scale.png" style="height: 300px; width:300px;"/>  
 <img src="https://github.com/crtallent/MechaCar_Statistical_Analysis/blob/main/Challenge/Images/Quantiles.png" style="height: 300px; width:300px;"/>  
 <img src="https://github.com/crtallent/MechaCar_Statistical_Analysis/blob/main/Challenge/Images/Fitted.png" style="height: 300px; width:300px;"/>    
<p/>  
  
### Summary Statistics on Suspension Coils

The design specifications for the MechaCar suspension coils dictate that the variance of the suspension coils must not exceed 100 PSI (pounds per square inch).  For this analysis,
we calculated the mean, median, variance, and standard deviations of the suspension coil's PSI column:

<img src="https://github.com/crtallent/MechaCar_Statistical_Analysis/blob/main/Challenge/Images/total_summary.png"/>

As we can see from the above, the average (mean) PSI for all suspension coils in all three lots is 1498.78, while the median PSI value is 1500. We can also see that the variance of the coils is 62.29, which is below the 100 PSI mark as required.  However, when we drill down to the lot level, we see that Lot 3's PSI variance is 170.29, which exceeds the 100 PSI threshold.  While statistically the suspension coils meet this requirement, there appear to be vehicles in Lot 3 in which the requirement is not met.

<img src="https://github.com/crtallent/MechaCar_Statistical_Analysis/blob/main/Challenge/Images/lot_summary.png"/>

#### Boxplot Showing Outliers in Lot 3

<img src="https://github.com/crtallent/MechaCar_Statistical_Analysis/blob/main/Challenge/Images/boxplot.png"/>

### T-Tests on Suspension Coils

In order to determine if the PSI results varied statistically throughout MechaCar's production lots, a Shapiro-Wilk normality test and a distribution plot were completed.  First, a Shapiro-Wilk normality test was completed to determine whether the results followed a normal distribution.  As we can see in the below image, the p-value from the Shapiro-Wilk test was above 0.05, and the distribution plot follows a normal bell-curve, so we determine that the results are normally distributed:

<img src="https://github.com/crtallent/MechaCar_Statistical_Analysis/blob/main/Challenge/Images/shapiro_test.png"/>

<img src="https://github.com/crtallent/MechaCar_Statistical_Analysis/blob/main/Challenge/Images/dist_plot.png"/>

In order to complete our t-tests, we first determined our hypotheses:

1. Null hypothesis - there is no statistical difference between the observed sample mean and its presumed population mean
2. Alternative hypothesis - there is a statistical difference between the observed sample mean and its presumed population mean

Then, we created a sample of 50 datasets from our suspension coils dataset (susp_table), and performed a t-test on the results, to get a mean PSI of 1497.22:

<img src="https://github.com/crtallent/MechaCar_Statistical_Analysis/blob/main/Challenge/Images/sample_t.png"/>

As we can see from the p-value of 0.2528 (over 0.05), we fail to reject our Null hypothesis that the sample results deviate statistically from our population dataset.

Next, we separate our dataset into three sets (Manufacturing Lots: 1, 2, and 3) using the subset() function and test our hypotheses again in three t-tests:

```

> lot1 <-subset(susp_table, Manufacturing_Lot=="Lot1")
> lot2 <-subset(susp_table, Manufacturing_Lot=="Lot2")
> lot3 <-subset(susp_table, Manufacturing_Lot=="Lot3")
> t.test(lot1$PSI,mu=1497.22)

```

<p float="left">
  <img src="https://github.com/crtallent/MechaCar_Statistical_Analysis/blob/main/Challenge/Images/lot1_t.png" alt="Lot 1" style="height: 400px; width:400px;"/>
 <img src="https://github.com/crtallent/MechaCar_Statistical_Analysis/blob/main/Challenge/Images/lot2_t.png" alt="Lot 2" style="height: 400px; width:400px;"/> 
 <img src="https://github.com/crtallent/MechaCar_Statistical_Analysis/blob/main/Challenge/Images/lot3_t.png" alt="Lot 3" style="height: 400px; width:400px;"/> 
<p/> 

As we can see from our three additional t-tests by lot, we again fail to reject our Null hypothesis for Lot 3.  However, for lots 1 and 2, we see that our p-values are very close to zero (less than 0.05), so we reject our Null hypothesis.  In other words, the values from Lots 1 and 2 do vary statistically from our sample data.  Based on our T-Test results and the outliers seen in our bell curve and our boxplot, it would be prudent for MechaCar to look into these discrepencies to ensure all vehicles are meeting the PSI requirements.

### Study Design: MechaCar vs Competition

In order to quantify how MechaCar performs against the competition, an additional study could be completed.  This would need to take into consideration the factors that consumers look at prior to buying a car, such as the cost of the vehicle, gas mileage, horse power, and safety rating.  The null hypothesis would be that MechaCars vehicles do not differ statistically from their competitors' products.  The alternate hypothesis would be that MechaCars vehicles do differ statistically from their competitor's products.  A chi-squared test could be completed to determine if any of the previously discussed factors increase the likelihood of consumers purchasing one vehicle over another (difference in categorical frequencies between groups).  In order to complete the study, data from MechaCar's consumers would need to be gathered including number of sales, cost of vehicles, gas mileage, horse power, and safety ratings.


