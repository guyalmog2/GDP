# GDP project - analyzing and predicting countrys' GDP based on socio-economic factors
## goals:
the goal of this project, as a student of economics and psychology, was to integrate my passion and knowledge in the field of ecomonics and with my developing programming skills. 
in order to do that, i've chosen to gather some data regarding countrys' GDP and it's related factors, analyze it, and try to fit it into a regression model which will help to predict it correctly.

## data sources:
the data we're about to analyze is taken from https://www.kaggle.com/fernandol/countries-of-the-world and contains socioeconomic indicators as well as their Gross Domestic Product.
To add some more variables which i think can help our model to be fully capble of predicting the GDP, i added a few more indicators taken from the World Bank(https://www.worldbank.org/) such as Imports and Exports, the CIA factbook website(https://www.cia.gov/library/publications/the-world-factbook/) and https://www.heritage.org/index/ranking for some indicators on market freedom.
The data contained 31 variables with 149 countries after cleaning was done.

## Coding resources:
python version - 3

packages: pandas, numpy, sklearn, scipy, matplotlib, seaborn, XGBoost, LightGBM

# Process

## data cleaning:
* Renamed some columns in order to work with them easily
* Renamed some religion indexes to fit the other main religions
* converted some columns to categorial types
* converted numerical null values based on the mean after checking their distribution
* converted string-type null values based on what fitted these variables based on the data

## Exploratory Data Analysis:
GDP basic statistics:

* count      149.000000
* mean      8914.093960
* std      10031.491092
* min        500.000000
* 25%       1800.000000
* 50%       4800.000000
* 75%      11400.000000
* max      55100.000000



top 10 correlators with GDP:

![alt text](https://github.com/guyalmog2/GDP/blob/master/top_corr.png?raw=true)


Relgion data variables:

![alt text](https://github.com/guyalmog2/GDP/blob/master/Region.png?raw=true)


The GDP distribution after perfoming log transformation to make it Normal Distributed:

![alt text](https://github.com/guyalmog2/GDP/blob/master/GDP_Dist.png?raw=true)


## Modeling:

7 models were compared to each other on 4 conditions:
1) All features selected and modelling done without scaling
2) Specific features selected and modelling done without scaling
3) All features selected and modelling done with scaling
4) Specific features selected and modelling done with scaling

the models that were compared are:
* Lasso
* Linear regression
* XGBooster regression
* SVM 
* Random forest
* Elastic net
* Light GBM

out of the seven, XGB and Random forest have shown the best results, further Grid search performed on both, with XGB providing the best final model:
* R2 Score - 0.9428042942023181
* Mean squared error score - 0.07782077858256242

![alt text](https://github.com/guyalmog2/GDP/blob/master/Regression_plot.png?raw=true)


The coefficient results provided from the model were:

* Phones	0.381336
* Infant mortality	0.202153
* Business Freedom	0.094156
* Birthrate	0.051947
* Exports	0.047083
* Industry	0.038557
* Financial Freedom	0.032130
* Investment Freedom	0.027141
* Pop. Density	0.025503
* Population	0.023937
* ATMs per 100,000 adults 2013	0.022876
* Net foreign invest	0.020571
* Service	0.017615
Literacy	0.014994
