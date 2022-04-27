# MechaCar_Statistical_Analysis
# Overview:
The idea in this challenge was to help Jeremy and the data analytics team do the following:

- Perform multiple linear regression analysis to identify which variables in the dataset predict the mpg of MechaCar prototypes
- Collect summary statistics on the pounds per square inch (PSI) of the suspension coils from the manufacturing lots
- Run t-tests to determine if the manufacturing lots are statistically different from the mean population
- Design a statistical study to compare vehicle performance of the MechaCar vehicles against vehicles from other manufacturers. 

# Deliverable 1
## Linear Regression to Predict MPG
The MechaCar_mpg.csv dataset contains mpg test results for 50 prototype MechaCars. The MechaCar prototypes were produced using multiple design specifications to identify ideal vehicle performance. Multiple metrics, such as vehicle length, vehicle weight, spoiler angle, drivetrain, and ground clearance, were collected for each vehicle. 

Using R we are to design a linear model that predicts the mpg of MechaCar prototypes using several variables from the MechaCar_mpg.csv file.

### Results:
mpg = (6.267)vehicle_length + (0.0012)vehicle_weight + (0.0688)spoiler_angle + (3.546)ground_clearance + (-3.411)AWD + (-104.0)
<img width="705" alt="image" src="https://user-images.githubusercontent.com/36766602/165417482-2fdda8b3-9920-42f3-bf52-ab7eb29ee2fb.png">
<img width="698" alt="image" src="https://user-images.githubusercontent.com/36766602/165417549-ed9d0670-9527-4680-b2d8-967065b8852a.png">

### Summary:

The above output shows that:

The vehicle length and vehicle ground clearance have a significant impact on miles per gallon on the MechaCar prototype. Conversely, the vehicle weight, spoiler angle, and All Wheel Drive have p-Values that indicate a random amount of variance with the dataset.

The p-Value for this model is 5.35e-11, which is much smaller than the assumed significance level of 0.05%. This shows that there is sufficient evidence to reject our null hypothesis.

The model has an r-squared value of 0.7149, which means that approximately 71% of all mpg predictions will be determined by this model. This shows mpg of MechaCar prototypes can be predicted effectively.

Removing some variables that show less impact (vehicle weight, spoiler angle, and All Wheel Drive), the predictability does decrease, a bit in that the r-squared value falls from 0.7149 to 0.674.
<img width="859" alt="image" src="https://user-images.githubusercontent.com/36766602/165418148-067275ce-4462-405a-8615-64a0ecb0044a.png">
<img width="861" alt="image" src="https://user-images.githubusercontent.com/36766602/165418310-7dd2edad-b8e3-469c-ab03-ef37524b3caf.png">
<img width="852" alt="image" src="https://user-images.githubusercontent.com/36766602/165418341-49ab054b-3564-4b60-a2b8-251c4e7b723e.png">

# Deliverable 2
## Summary Statistics on Suspension Coils
The MechaCar Suspension_Coil.csv dataset contains the results from multiple production lots. In this dataset, the weight capacities of multiple suspension coils were tested to determine if the manufacturing process is consistent across production lots. Using your knowledge of R, you’ll create a summary statistics table to show:

- The suspension coil’s PSI continuous variable across all manufacturing lots
- The following PSI metrics for each lot: mean, median, variance, and standard deviation.

### total_summary dataframe looks like this:

### RScript
- RScript that creates a lot_summary dataframe using the group_by() and the summarize() functions to group each manufacturing lot by the mean, median, variance, and standard deviation of the suspension coil’s PSI column.
- Summary Stats:
<img width="488" alt="image" src="https://user-images.githubusercontent.com/36766602/165419871-a6f10394-e3af-4ffa-b978-63233832e615.png">

- lot summary:
<img width="669" alt="image" src="https://user-images.githubusercontent.com/36766602/165419936-049103cc-27b7-4579-af82-f0aad500f061.png">

With the understanding that the design specifications for the MechaCar suspension coils mandate that the variance of the suspension coils cannot exceed 100 pounds per square inch (PSI) .

### Does the current manufacturing data meet this design specification for all manufacturing lots in total and each lot individually? Why or why not?

- When looking at the entire population of the production lot, the variance of the coils is 62.29 PSI, which is well within the 100 PSI variance requirement.

Also:
- Lot 1 and Lot 2 are well within the 100 PSI variance requirement; with variances of 0.98 and 7.47 respectively. However, it is Lot 3 that is showing much larger variance in performance and consistency, with a variance of 170.29. It is Lot 3 that is disproportionately causing the variance at the full lot level.

<img width="596" alt="image" src="https://user-images.githubusercontent.com/36766602/165420417-9c71d2ab-59e4-4212-86a3-72004e2c654d.png">

# Deliverable 3
### t-Tests on Suspension Coils
### All t-tests
Summary of the t-test results across all manufacturing lots:
<img width="479" alt="image" src="https://user-images.githubusercontent.com/36766602/165422118-11a479f6-96ae-4f92-8d37-7caa1e8096ce.png">

Here we can see the true mean of the sample is 1498.78, which we also saw in the summary statistics above. With a p-Value of 0.06, which is higher than the common significance level of 0.05, there is NOT enough evidence to support rejecting the null hypothesis. 

### Individual lots:

- Lot 1 sample actually has the true sample mean of 1500, again as we saw in the summary statistics above. With a p-Value of 1, clearly we cannot reject (i.e. accept) the null hypothesis that there is no statistical difference between the observed sample mean and the presumed population mean (1500).

<img width="470" alt="image" src="https://user-images.githubusercontent.com/36766602/165423029-9cbb828a-0520-47e6-bff3-f00f4604e37d.png">

- Lot 2 has essentially the same outcome with a sample mean of 1500.02, a p-Value of 0.61; the null hypothesis cannot be rejected, and the sample mean and the population mean of 1500 are statistically similar.

<img width="459" alt="image" src="https://user-images.githubusercontent.com/36766602/165422957-3d264bf8-47ae-4285-a9ff-5e18b49cace0.png">

- Lot 3, not surprisingly is a different scenario. Here the sample mean is 1496.14 and the p-Value is 0.04, which is lower than the common significance level of 0.05. All indicating to reject the null hypothesis that this sample mean and the presumed population mean are not statistically different.

<img width="456" alt="image" src="https://user-images.githubusercontent.com/36766602/165422830-f202f4c6-ac65-4537-a7fc-1e5e8ca0d92b.png">


### How does this information help? 
- Clearly, something went wrong in Lot 3's production cycle. 
- The process needs to be checked for system fails and the suspension coils from this lot need to be inspected to remove those not meeting quality criteria.

# Deliverable 4
### MechaCar vs Competition

### Metrics
Data for comparable models across all major manufacturers for past 3 years for the following metrics:
### Variables
Independent Variable - Safety Feature Rating
Dependent Variable - Current Price (Selling)
Independent Variable - Drive Package 

### Other vairiables:
Independent Variable - Engine (Electric, Hybrid, Gasoline)
Independent Variable - Resale Value

Independent Variable - Average Annual Cost of ownership 
Independent Variable - MPG (Gasoline Efficiency)

### Hypothesis: Null and Alternative

Null Hypothesis (Ho): MechaCar is priced right according to its performance of key factors for its genre.

Alternative Hypothesis (Ha): MechaCar is NOT priced right based on performance of same key factors for its genre.

### Statistical Tests
A multiple linear regression would be used to determine the factors that have the highest correlation/predictability with the list selling price (dependent variable); which combination has the greatest impact on price.
