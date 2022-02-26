# MechaCar_Statistical_Analysis

### Linear Regression to Predict MPG

In our [multiple linear regression results](https://github.com/crtallent/MechaCar_Statistical_Analysis/blob/main/Challenge/Images/lm%20sum.png), we see that roughly 71% of our variability can be explained by this linear model.  This indicates that there is a 71% likelihood that this data would represent real-world data points.  The variables that provided a non-random amount of variance to the MPG values in the dataset were vehicle_length and ground_clearance, at 2.60e12 and 5.21e-08, respectively.  The below image shows the detailed results of our multiple linear regression model:

<img src="https://github.com/crtallent/MechaCar_Statistical_Analysis/blob/main/Challenge/Images/lm%20sum.png"/>

In this case, the slope of our linear model is not considered to be zero, as we can see a significant linear relationship between MPG and our vehicle_length and ground_clearance variables.  Additionally, our p-value (5.35e-11) is smaller than 0.05, so we have sufficient evidence to reject our null hypothesis that there is no relationship between MPG and our other variables.  However, this linear model may not effectively predict MPG of MechaCar prototypes effectively due to the lack of significant variables in our dataset.  In other words, there is a likelihood that we may be seeing overfitting, and our model may not work as well in the future to predict data.  It would be advised to add other variables into our linear regression model to gain a better understanding of everything that is impacting MPG for future predictions.


