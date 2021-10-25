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


![alt text](https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/Plots/environSustainProfit.png?raw=true)

![alt text](https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/Plots/environSustainProfit_highIncome.png?raw=true)
![alt text](https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/Plots/environSustainProfit_lowIncome.png?raw=true)
![alt text](https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/Plots/environSustainProfit_lowMidIncome.png?raw=true)
![alt text](https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/Plots/environSustainProfit_uppMidIncome.png?raw=true)


![alt text](https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/Plots/USA_GDP_timeseries_1961-2013.png?raw=true)
![alt text](https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/Plots/boxplot-forecast-2013_USA_GDP.png?raw=true)
![alt text](https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/Plots/USA_GDP_2014-2019_real.png?raw=true)


![alt text](https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/Plots/USA_GDP_timeseries_1961-2009.png?raw=true)
![alt text](https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/Plots/boxplot-forecast-2009_USA_GDP.png?raw=true)
![alt text](https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/Plots/USA_GDP_2010-2019_real.png?raw=true)


![alt text](https://github.com/christinanelson/SustainabilityProfitCorrelation/blob/main/Plots/USA_GDP+RenewableEnergyConsumption_timeseries_1961-2019.png?raw=true)
