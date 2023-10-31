# RecidivismChallenge

Based on [this challenge](https://nij.ojp.gov/funding/recidivism-forecasting-challenge), attempt to predict prisoner recidivism using classification models.

[Here](ModellingAndAnalysis.ipynb) is the in depth analysis and conclusions including source code for all models used and the entire process.

### Data
Data on recidivism from NIJ. [Here](data/vehicles.csv](https://nij.ojp.gov/funding/recidivism-forecasting-challenge.

### Methodology
1. Data - removed all empty values and nonsensical values. Scaled data pre-analysis as necessary.
2. Models - ran 5 models
 - Simple linear regression model with no feature selection
 - A ridge model
 - A lasso model
 - A linear regression model with polynomial features
 - A linear regression model with polynomial features only using numeric values
3. Cross validation - simple cross validation due to size of data
4. Evaluation - evaluated using median absolute error. We used median because the distribution of prices is right-skewed, and it is more important to be accurate the more to the left we are in the distribution


### Goal
Successfully predict price of used cars as well as identify some factors that cause increased price of used cars

# Insights

### Insight 1: Used cars depreciate in value

![PriceByYear](https://github.com/alexanderpspahr/UsedCarsPriceAnalysis/assets/129889030/4fc38bad-a75e-4f8f-b20a-c1705f78e996)

This is common knowledge in the used car industry, but it is a very important factor in determining the price of a used car. Our model considered this the tenth most important feature, but it is important to note that almost all of the features above it pertained to the manufacturer and the fuel type of a car. Indicating that when adjusted for manufacturer and fuel type, the year of the car is one of the absolute best indicators of whether or not a car will sell for a high price.

### Insight 2: Manufacturer is very, very important in determining price

Out of the factors that make up the bottom 5 important features for our model and the top 5 features for our model, the manufacturer comprises 90%  (9/10) of those factors. 

For reference, here is what the distribution of price looks like for top 5 manufacturers vs the rest:

![Top5VsOtherPrice](https://github.com/alexanderpspahr/UsedCarsPriceAnalysis/assets/129889030/721b0bbf-7698-4e14-b459-aebc60486e3d)

There are 5 specific manufacturers that reign above all others statistically. They are (ordered):
1. Ferrari
2. Aston-Martin
3. Tesla
4. Dotsun
5. Porsche


### Insight 3: Fuel type is the next most important factor

Fuel type is one of the most important factors in determing a used cars value. Diesel cars and electric cars are more expensive, while alternative fuel cars are less expensive.

### Insight 4: Our Model is usable for business cases in which we need to find the ballpark price of a used car

Our model had a median absolute error of around 3500, which is good for ballpark estimates. If we need exact price, it is not good enough, but it is certainly better than any trivial solution. This is mostly related to the fact that the model can estimate the price better based on manufacturer, which is one of the most important aspects of price, as we have seen previously.

## Final Notable Findings and Conclusions

1. **Timing:** Used cars mostly depreciate in value over time, and the year of the car is very important
2. **Brands** There is a top 5 "holy grail" brands for used cars which are significantly higher price and includes cars from: Ferrari, Aston-martin, Tesla, Datsun, and Porsche, in that order  
3. **Fuel Type:** Fuel type matters a lot in used cars with diesel and electric having the highest selling point on average, and alternative fuels being the lowest  
4. **Location:** Alaska is the best state for selling used cars at high prices by a significant margin, this is likely because it is hard to find cars there.  
5. **Model Performance:** Our model can predict the price of used cars with an average error of around 3500, which is a good ballpark estimate.  

Next Steps:
1. Stock inventory with newer cars
2. Be on the look at for top 5 brands
3. Stock inventory with as many diesel and electric cars as possible
4. Use model to predict ballpark price
