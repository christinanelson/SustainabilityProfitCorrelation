# SustainabilityProfitCorrelation

Thesis: Our country's gross domesetic product (GDP) is a comprehensive account of our nation's economic status. Business' economic health is interwoven into this measure of GDP, thus accurate predictions of changes in GDP will help in strengthening business decisions and strategies. The increase in usage of renweable energy resources may be a way for a country to stabilize GDP growth to a desirable rate. This analysis explores correlations between GDP growth and renewable energy consumption. A simple univariate multilayer perceptron is built to forecast GDP growth. This provides the basis for building a new multivariate model that uses renewable energy consumption and GDP information to predict GDP growth. The Granger causality test will be applied.  

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

You can see that there are denser clusters of data points in higher region of renewable energy consumption, for low and lower middle income countries. Meaning these countries are able to perform relatively similar in GDP growth and renewable energy consumption. This insinuates that a more stable (ie. not spread-out) GDP growth could be achieved with larger uses of renewable energy consumption. When looking at the high income contry correlation plot, all values are spread-out and there is no correlation is observed. The upper middle income country correlation plot has the largest spread towards lowest GDP growth. Again, the plots hint at the effect that renewable energy consumption has on GDP growthy, ie. that it keeps the growth more stable in a tigher area.


Next, I looked at the time series of annual % GDP growth for the USA from 1961 to 2013. I have data values for the time range 1961-2019, but I wanted to keep data from 2014-2019 'blinded', so that I could make a prediction using my model, and then compare it to the known result in order to guage accuracy and precision.


![alt text](https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/Plots/USA_GDP_timeseries_1961-2013.png?raw=true)

Then, I built two simple models to train and validate on data from 1961-2013 and predict GDP growth for 2014.

The first model predicts the next year's GDP growth to be 2.446 RMSE (+/- 0.000).

While the MLP's prediction is shown in the folllowing box and whisker plot, which predicts a GDP growth value of 2.192 with a root mean square error (RMSE) of +/- 0.059.

![alt text](https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/Plots/boxplot-forecast-2013_USA_GDP.png?raw=true)

This is the values for GDP growth for the years 2014-2019. We compare our prediction above to GDP growth for 2014. (ie. about 2.5%)

![alt text](https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/Plots/USA_GDP_2014-2019_real.png?raw=true)

The naive model is closer in accuracy to the actual value for GDP growth in 2014, but this could be that the MLP needs more optimization and training.



![alt text](https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/Plots/USA_GDP_timeseries_1961-2009.png?raw=true)
![alt text](https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/Plots/boxplot-forecast-2009_USA_GDP.png?raw=true)

This is the values for GDP growth for the years 2010-2019. We compare our prediction above to GDP growth for 2010. (ie. about 2.5%)

![alt text](https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/Plots/USA_GDP_2010-2019_real.png?raw=true)


![alt text](https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/Plots/USA_GDP+RenewableEnergyConsumption_timeseries_1961-2019.png?raw=true)
