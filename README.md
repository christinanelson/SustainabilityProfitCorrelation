# SustainabilityProfitCorrelation

Thesis: Our country's gross domestic product (GDP) is a comprehensive account of our nation's economic status. Business' economic health is interwoven into this measure of GDP, thus accurate predictions of changes in GDP will help in strengthening business decisions and strategies. The increase in usage of renewable energy resources may be a way for a country to stabilize GDP growth to a desirable rate. This analysis explores correlations between GDP growth and renewable energy consumption. A simple univariate multilayer perceptron is built to forecast GDP growth. This provides the basis for building a new multivariate model that uses renewable energy consumption and GDP information to predict GDP growth. The Granger causality test will be applied.  

Businesses are the end user for this project. It is very advantageous for a business to have a highly probable and accurate prediction of future GDP growth;  this information may greatly help to mitigate risk and improve profit. The problem of knowing correlations in GDP growth and having accurate predictions is an urgent and pervasive problem because it has direct association with business profits. Prove accurate predictions, and businesses would pay for this information.

The minimum requirement for this project is to extend the current univariate forecast model using MLP to a multivariate model using MLP, and apply the Granger causality test. This can surely be accomplished in 8 weeks. Additional models could be explored for comparison, such as  k-nearest neighbors, or CNN/DNNs.  I already have shown that a simple univariate MLP model improves GDP forecast when compared to a naive model. Value is shown in accurate and precise forecasts. Additional analysis could be done to search for variables that strengthen GDP growth predictions.

Ideally I want quarterly GDP growth data from around 1950 to present. So far, I've found quarterly GDP data for the last twenty years on the government site bea.gov. There is also more data from statista.com, which goes back annually as far as 1930. If I am not able to find quarterly GDP data far back in history, I will use a hybrid model to incorporate annual data and quarterly data combined.

I have not found any models that use renewable energy consumption as an additional variable to predict GDP using machine learning. There has been articles about positive correlations between renewable energy consumption and GDP growth. And there is an article about improvements found with GDP forecasting using k-nearest neighbors. But again, using the information from renewable energy consumption in a multivariate analysis to forecast GDP growth is a completely novel approach.

I would do this analysis with the additional scope of the considered business, ie. do a multivariate ML time series analysis to predict the business' growth, using renewable energy and our country's GDP as additional variables. The success of this project would be shown in validated predictions and comparison to the business' existing method of projecting growth values. Then do my analysis to forecast business growth in the unknown future. I would then tell the 'nontechnical' stakeholder the forecast, and inform them that they can use this information to decide where to increase business resources , eg. small company growth predicted --> increase marketing, large company growth predicted--> increase production.

tinaphysics@gmailcom

https://github.com/christinanelson/SustainabilityProfitCorrelation

data used: ESGData.csv
From: The World Bank's Data of sustainability themes
https://www.kaggle.com/tunguz/environment-social-and-governance-data

The following plots show exploratory results of a first look at the data.

https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/CorrelationExploration_GDP_RenEnCons.pdf

https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/USA_GDP_timeseries%2Bforecast.pdf

First, I explored if there were correlations between annual % GDP growth and renewable energy consumption (% of total final energy consumption) for every country that data was available for.

![alt text](https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/Plots/environSustainProfit.png?raw=true)

There are no clear trends in the above plot. Perhaps there are categories of countries that have specific trends while others do not. To investigate this, I broke up the data for the country into income categories provided by the United Nations. The following four plots show the correlations between GDP and renewable energy consumption for the categories: high income, low income, lower middle income, and upper middle income.

![alt text](https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/Plots/environSustainProfit_highIncome.png?raw=true)
![alt text](https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/Plots/environSustainProfit_lowIncome.png?raw=true)
![alt text](https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/Plots/environSustainProfit_lowMidIncome.png?raw=true)
![alt text](https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/Plots/environSustainProfit_uppMidIncome.png?raw=true)

You can see that there are denser clusters of data points in higher region of renewable energy consumption, for low and lower middle income countries. Meaning these countries are able to perform relatively similar in GDP growth and renewable energy consumption. This insinuates that a more stable (ie. not spread-out) GDP growth could be achieved with larger uses of renewable energy consumption. When looking at the high income country correlation plot, all values are spread-out and there is no correlation is observed. The upper middle income country correlation plot has the largest spread towards lowest GDP growth. Again, the plots hint at the effect that renewable energy consumption has on GDP growth, ie. that it keeps the growth more stable in a tighter area.


Next, I looked at the time series of annual % GDP growth for the USA from 1961 to 2013. I have data values for the time range 1961-2019, but I wanted to keep data from 2014-2019 'blinded', so that I could make a prediction using my model, and then compare it to the known result in order to gauge accuracy and precision.


![alt text](https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/Plots/USA_GDP_timeseries_1961-2013.png?raw=true)

Then, I built two simple models to train and validate on data from 1961-2013 and predict GDP growth for 2014.

The first model I call the naive or dummy model, because it just does supervised learning via walk-forward-validtion with no stochastic element.

I use 47 years of data (1961-2008) for training, and the last 5 years (2009-2013) for the test set. The models shift the data set in 1 year increments back and forward in time for up to 10 years. 

The naive model calculates the median RMS of subset prior observations relative to the next one year GDP growth.

From this model, there is a median of **2.446 RMSE (+/- 0.000)**. Note there is no error because there is no stochastic element. So, any model that gives a lower error than 2.446 shows an improvement in predictive performance.


The next model I built is a multilayer perceptron (MLP). MLPs are a good starting point because it is a relatively simple feed forward neural network. Again, we use time steps of one years here, but MLPs are additionally able to do time series forecasting by taking multiple lag observations and use them as features to make predictions. Here we will actually make a prediction of the unknown next year's annual GDP growth.

A MLP from Keras library is used. We use 10 (increments of 1 year) lag observations, 500 nodes in the hidden layer, 100 epochs (times exposed to the whole training set), and 100 batches (amount of samples within an epoch having updated weights applied). The hidden layer uses a rectified linear activation function, and the output layer uses a linear activation function. Also, the standard mean squared error is used as a loss function and the 'Adam' flavour is used for training the network using stochastic gradient descent.


The MLP's RMSE scores are shown in the following box and whisker plot, which has a RMSE of **2.204 +/- 0.068**, which is an improvement compared to the naive model. The spread with a standard deviation of 0.068 could be reduced further by optimizing hyperparameters.

![alt text](https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/Plots/boxplot-forecast-2013_USA_GDP.png?raw=true)

This is the values for GDP growth for the years 2014-2019. I plan to compare prediction above to GDP growth for 2014.

![alt text](https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/Plots/USA_GDP_2014-2019_real.png?raw=true)


The same analysis was repeated closer to the large delta in GDP growth from from 2009 to 2010.


![alt text](https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/Plots/USA_GDP_timeseries_1961-2009.png?raw=true)

For our naive model we obtain a RMSE of about **2.975**. And when using MLP, we get a median RMSE of **2.071 +/- 0.060**. Again, there is improvement in model's predictive performance when using MLP.

![alt text](https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/Plots/boxplot-forecast-2009_USA_GDP.png?raw=true)

This is the values for GDP growth for the years 2010-2019. I plan to compare our prediction above to GDP growth for 2010.

![alt text](https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/Plots/USA_GDP_2010-2019_real.png?raw=true)


The next step is to obtain prediction values for have kept 'blind'. I expect the performance to be consistent within the MLP's RMS error.

The minimum final step for this project is to combine renewable energy consumption data with annual GDP data to perform a multivariate time series forecast using MLP. The goal is to determine whether renewable energy consumption of a country is an informative variable in GDP forecasts. The Granger causality test will be applied, which states if X (read: renewable energy consumption) causes Y (read: GDP growth), then the forecast of Y based on previous values of Y *and* the previous values of X should outperform the forecast of Y based on previous values of Y alone. The below figure is an overlay of annual GDP growth and renewable energy consumption data.

![alt text](https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/Plots/USA_GDP+RenewableEnergyConsumption_timeseries_1961-2019.png?raw=true)
