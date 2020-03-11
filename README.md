## Project Overview

This project is related to my submission for the data challenge held by XTX Markets and Correlation One in September 2019. Data provided in the competition is NOT shared in this depository out of respect for organisers.

Correlation One's repository for this challenge: https://github.com/correlation-one/XTXStarterKit.

### Files Overview

1. [python] Market Depth and Order Messages.ipynb

&emsp;&emsp;Transform the data into market depth view, and estimate the sizes of market, limit and cancelled orders.

2. [q/kdb+] Data Preparation in Q.ipynb

&emsp;&emsp;Data preprocessing and part of feature engineering.


### Goal, Data and Metrics
The goal is to use limit order book data to predict midprice change in ticks ahead

3 million ticks of data are provided for training. Each line of training data includes
- first 14 levels of bid and ask prices and order sizes
- prediction target y, which is the midprice change in 87 ticks

**Note**: past y can't be used as input of next tick prediction

The final submission must include feature construction code and the trained model. It will be tested real-time on private data and ranked by R-squared. 
$R^2 = \frac{\sum_{i}(\hat{y}_i-\bar{y}_i)^2}{\sum_{i}(y_i-\bar{y}_i)^2}$

### High-frequency Trading Environment Constraints
The competition preserved important features of high-frequency trading environment, i.e. real-time prediction and low latency. It's unlike kaggle, in which participants only compete on the prediction results without limits on model complexity and prediciton time. This one sets **limit on model size** (smaller than 256mb) and **real-time prediciotn speed** (60000 lines in 60min on their cloud computer, specs unkown). So it requires considerations for
1. **tradeoff between model complexity and performance** under time constrains
2. **algorithm** of machine learning model and feature construction process
