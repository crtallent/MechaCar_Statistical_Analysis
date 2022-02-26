# MechaCar_Statistical_Analysis

### Linear Regression to Predict MPG

In our [multiple linear regression results](https://github.com/crtallent/MechaCar_Statistical_Analysis/blob/main/Challenge/Images/lm%20sum.png), we see that roughly 71% of our variability can be explained by this linear model.  This indicates that there is a 71% likelihood that this data would represent real-world data points.  The variables that provided a non-random amount of variance to the MPG values in the dataset were vehicle_length and ground_clearance, at 2.60e12 and 5.21e-08, respectively.  The below image shows the detailed results of our multiple linear regression model:

<img src="https://github.com/crtallent/MechaCar_Statistical_Analysis/blob/main/Challenge/Images/lm%20sum.png"/>

In this case, the slope of our linear model is not considered to be zero, as we can see a significant linear relationship between MPG and our vehicle_length and ground_clearance variables.  Additionally, our p-value (5.35e-11) is smaller than 0.05, so we have sufficient evidence to reject our null hypothesis that there is no relationship between MPG and our other variables.  However, this linear model may not effectively predict MPG of MechaCar prototypes effectively due to the lack of significant variables in our dataset.  In other words, there is a likelihood that we may be seeing overfitting, and our model may not work as well in the future to predict data.  It would be advised to add other variables into our linear regression model to gain a better understanding of everything that is impacting MPG for future predictions.

### Additional Images - Linear Regression Plots

<p float="left">
  <img src="https://github.com/crtallent/MechaCar_Statistical_Analysis/blob/main/Challenge/Images/length.png" alt="Vehicle Length Linear Regression Plot" style="height: 300px; width:300px;"/>
 <img src="https://github.com/crtallent/MechaCar_Statistical_Analysis/blob/main/Challenge/Images/ground_clearance.png" alt="Ground Clearance Linear Regression Plot" style="height: 300px; width:300px;"/> 
 <img src="https://github.com/crtallent/MechaCar_Statistical_Analysis/blob/main/Challenge/Images/plot.png" alt="Multiple Variable Regression Plot" style="height: 300px; width:300px;"/> 
<p/>  
  
### Summary Statistics on Suspension Coils

The design specifications for the MechaCar suspension coils dictate that the variance of the suspension coils must not exceed 100 PSI (pounds per square inch).  For this analysis,
we calculated the mean, median, variance, and standard deviations of the suspension coil's PSI column:

<img src="https://github.com/crtallent/MechaCar_Statistical_Analysis/blob/main/Challenge/Images/total_summary.png"/>

As we can see from the above, the average (mean) PSI for all suspension coils in all three lots is 1498.78, while the median PSI value is 1500. We can also see that the variance of the coils is 62.29, which is below the 100 PSI mark as required.  However, when we drill down to the lot level, we see that Lot 3's PSI variance is 170.29, which exceeds the 100 PSI threshold.  While statistically the suspension coils meet this requirement, there appear to be vehicles in Lot 3 in which the requirement is not met.

<img src="https://github.com/crtallent/MechaCar_Statistical_Analysis/blob/main/Challenge/Images/lot_summary.png"/>

```

> lot1 <-subset(susp_table, Manufacturing_Lot=="Lot1")
> lot2 <-subset(susp_table, Manufacturing_Lot=="Lot2")
> lot3 <-subset(susp_table, Manufacturing_Lot=="Lot3")
> t.test(lot1$PSI,mu=1500)

```
