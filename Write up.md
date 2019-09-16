## The formula we took to calculate driver's Lifetime Value.

We define:

T := The lifetime driver has value to lyft (in month)

V := Driver's value (in dollar per month)

DV := Driver's lifetime value to Lyft (in dollars)

such that

$ DV = T \times V $

This formula is very intuitive. We can associate each driver's life time value with their average month value and their working time respectively. For example, driver A uses Lyft to make money for 18 months total. Each month A can earn an average of 2000 dollars. Then A's lifetime value is $2000 \times 18$ which is $36000. 

## Our Methodology
The reasoning of our formula is based on a simple assumption that Lyft will subtract a fixed percent of money from each driver's Gross Profit (GP). Since the percentage is fixed (and same) for all drivers, we can ignore this percent and only consider the GP for each driver. Thus the question to find driver's lifetime value can be reduced to two simpler questions: 

* How to calculate driver's Average Monthly Gross Profit (AMGP)
* How to calculate driver's average lifetime to Lyft

We have calculated the Gross Profit per Day (GPD) for driver k at day i in a seperated dataframe *xxx.csv*. To find AMGP we can find the average GPD and then multiple this number to 30 to get AMGP. In short

$ AMGP^{(k)} = 30 \times \frac{1}{n^{(k)}}\sum_{i=1}^{n^{(k)}} GPD_{i}^{(k)} $  

Where $ n^{(k)} $ is the number of day we have driver k's GPD data, and $ GPD_{i}^{(k)} $ is the GPD for driver k at day i.

Further, we can take the average of all $ AMGP^{(k)} $ to calculate AMGP, and this solved the first part of our problems.

Finding the driver's lifetime to Lyft is the most challenging one for us, since the data is limited in telling us when drivers actually start not using Lyft anymore. Therefore, we can only predict the end date for the driver. 

Linear Least Square Regression (LLSR) is the method we leverages to predict driver's quit time. This prediction is fast yet accurate. The procedure to do a Least Square is as follows:

1. Plot driver's k GPD respect to k's starting working day (Violet add more details)
2. Find the best fit line of these data using least square technique 
3. Find the intersection of the line and x-axis to predict the quit time (Q) for driver k
4. Average Q to get driver's average lifetime to Lyft

(Why this idea is correct?)

In such manner, we are alble to calculate driver's lifetime value to Lyft given a limited datasets.