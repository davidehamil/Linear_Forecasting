# Linear_Forecasting
## Dave Hamilton, Yuan Ni, Kaili Li
A Project Verifying Hull and Qiao’s Paper On Market Timing


## A. Data Description
1. Dividend-Price Ratio (DP)
- log of a twelve-month moving sum of dividends paid on the S&P 500 index minus the log of S&P 500 prices
- source: http://www.multpl.com/
2. Price-to-Earnings Ratio (PE)
- the price divided by earnings over the last 12 months
- source: http://www.multpl.com/
3. Book-to-Market Ratio (BM)
- book value of the S&P 500 divided by the S&P 500 index
- source: Bloomberg
4. Cyclically Adjusted Price to Earnings Ratio (CAPE)
- price divided by the average inflation adjusted earnings over the last ten years    
- source: http://www.multpl.com/
5. Principal Component of Price Ratios (PCAprice)
- the largest principal component of these variables  
- source: calculated in calculateFirstPC.ipynb
6. Bond Yield (BY)
- the 10-year Treasury bond yield divided by the bond yield EMA    
- source:Quandl
7. Default Spread (DEF)
- the difference between Baa yield and Aaa yield    
- source:Quandl
8. Term Spread (TERM)
- the yield difference between the 10-year Treasury Note and the three-month Treasury Bill    
- source:Quandl
9. Cointegrating Residual of Consumption, Assets, and Wealth (CAY)
- cointegrating residual of log consumption, assets, and wealth
- source: http://faculty.haas.berkeley.edu/lettau/data_cay.html
10. Sell in May and Go Away (SIM)
- SIM = d/130, in which d is the number of days in the next 130 business days that lie between the second business day in May and the 15th business day of October  
- source:calculated in calculateSIM.ipynb
11. Variance Risk Premium (VRP)
- VIX minus the volatility forecast from a GARCH-style model incorporating the Yang and Zhang (2000) estimator using the open, high, low, and close data
- source: VIX from Quandl, calculated in VRP.ipynb
12. Implied Correlation (IC)
- the average equity options-implied correlation, CBOE S&P 500 Implied Correlation Index
- source: Quandl
13. Baltic Dry Index (BDI)
- three month change in the BDI
- source: Bloomberg
14. New Orders/Shipments (NOS)
- log of the originally reported new orders divided by the original shipments
- source: http://www-bcf.usc.edu/~tuzel/
15. Consumer Price Index (CPI)
- the change in CPI over the last twelve months  
- source: Quandl
16. Ratio of Stock Price to Commodity Price (PCR)
- log of the ratio between SPY and GSCI  
- source: Bloomberg
17. Moving Average (MA)
- 0/1 signal based on SMA(20)-SMA(200)
- source: alculated in SPX_tech.xlsx
18. Principal Component of Technical Indicators (PCAtech)
- the first principal component of a set of technical indicators(Neely et al,2014)  
- source: calculated in SPX_tech.xlsx and calculateFirstPC.ipynb
19. Oil Price Shocks (OIL)
- the log of the current front oil futures price (CL1) minus the log of the fourth futures price (CL4) with a three month lag    
- source: Bloomberg
20. Short Interest (SI)
- the sum of all shares short on the NYSE divided by the average daily trading volume over the past 30 days    
- source: Quandl

**Basic Data Description**

|          | count | mean   | std    | min     | max    | q1     | q2     | q3     | skew   | kurt   |
|----------|-------|--------|--------|---------|--------|--------|--------|--------|--------|--------|
| CAY      | 6909  | -0.001 | 0.021  | -0.047  | 0.033  | -0.012 | -0.002 | 0.015  | -0.493 | -0.371 |
| NOS      | 6909  | 0.005  | 0.045  | -0.193  | 0.254  | -0.02  | 0.008  | 0.03   | 0.125  | 4.301  |
| BM       | 6909  | 0.374  | 0.085  | 0.201   | 0.609  | 0.331  | 0.366  | 0.438  | 0.004  | -0.259 |
| PE       | 6909  | 24.471 | 14.765 | 13.5    | 123.73 | 17.8   | 21.22  | 26.11  | 4.572  | 24.092 |
| CAPE     | 6909  | 25.437 | 6.538  | 13.32   | 44.19  | 20.83  | 24.86  | 27.21  | 1.081  | 0.98   |
| DP       | 6909  | 0.021  | 0.006  | 0.011   | 0.039  | 0.017  | 0.02   | 0.023  | 0.758  | 0.012  |
| PCAprice | 6909  | -0.004 | 1.632  | -4.229  | 3.67   | -1.071 | 0.131  | 0.72   | 0.155  | 0.055  |
| CPI      | 6909  | 0.025  | 0.013  | -0.02   | 0.064  | 0.017  | 0.026  | 0.032  | -0.053 | 1.107  |
| BY       | 6909  | 1      | 0.001  | 0.988   | 1.006  | 1      | 1      | 1      | -0.223 | 6.514  |
| DEF      | 6909  | 0.959  | 0.401  | 0.5     | 3.5    | 0.7    | 0.88   | 1.07   | 3.13   | 13.502 |
| TERM     | 6909  | 1.839  | 1.122  | -0.95   | 3.87   | 0.96   | 1.93   | 2.73   | -0.245 | -0.893 |
| VRP      | 6820  | -2.95  | 7.907  | -13.145 | 58.405 | -8.665 | -4.905 | 0.455  | 2.103  | 7.611  |
| IC       | 2643  | 57.98  | 9.593  | 19.92   | 83.94  | 51.79  | 58.05  | 63.83  | -0.001 | -0.155 |
| BDI      | 6909  | 0.052  | 0.332  | -0.899  | 2.379  | -0.135 | 0.017  | 0.207  | 0.931  | 3.6    |
| PCR      | 6151  | -1.52  | 0.205  | -1.94   | -0.927 | -1.663 | -1.591 | -1.422 | 1.076  | 0.455  |
| MA       | 6909  | 0.732  | 0.443  | 0       | 1      | 0      | 1      | 1      | -1.046 | -0.907 |
| PCAtech  | 6909  | -0.001 | 2.9    | -4.255  | 3.042  | -3.174 | 0.788  | 3.042  | -0.325 | -1.534 |
| OIL      | 6909  | 0.003  | 0.08   | -0.473  | 0.344  | -0.04  | 0.011  | 0.051  | -0.884 | 3.643  |
| SI       | 1044  | 0.437  | 0.51   | 0.003   | 8.411  | 0.151  | 0.299  | 0.554  | 5.939  | 68.426 |
| SIM      | 6909  | 0.477  | 0.279  | 0       | 0.931  | 0.238  | 0.485  | 0.723  | -0.032 | -1.219 |
| R_1M     | 6887  | 0.007  | 0.045  | -0.298  | 0.224  | -0.015 | 0.011  | 0.033  | -0.671 | 3.566  |
| R_3M     | 6844  | 0.022  | 0.075  | -0.41   | 0.388  | -0.013 | 0.028  | 0.066  | -0.71  | 2.938  |
| R_6M     | 6783  | 0.043  | 0.109  | -0.465  | 0.502  | -0.008 | 0.052  | 0.105  | -0.788 | 2.561  |
| R_12M    | 6657  | 0.089  | 0.163  | -0.488  | 0.686  | 0.025  | 0.105  | 0.193  | -0.724 | 1.066  |

**Correlation of Predictors**
![Alt text](/data_description/correlation_of_predictors.jpg)
**Correlation with future return**
![Alt text](/data_description/correlation_with_future_return.jpg)


## B. Regression Models
### Basic idea

Use the predictors to predict future return, with multiple regression models.

### Data Definition

Our "Y" is the n-day future return of SPX, where n = 130 (as the paper suggested) or 60. For each predictor, calculate the correlation between Y and (1) the predictor's raw value, (2) ewma of this predictor, (3) log of this predictor (we abandoned this one). Then we use the one with maximum correlation as our "transformed predictor". In some models we use raw values of predictors, while in others we use transformed value.

### Our Methods 

From 2001.1.1 to 2017.1.1, on the first day of month, we used past m-year (m=10 or 5, where 10 is suggested in the paper) daily data, excluding most recent n days (n=130, for example), as our training set to fit regression parameters. The parameters are used to predict future returns on each day of that month. The predicted future return is then used to calculate position in PnL backtesting.

**(1) simpLR and LR_Trans("Kitchen sink" model)**

This is the basic, simplest regression model where we use every predictor as long as it exists. 

We have two models here. simpLR uses raw values, and LR_Trans uses transfromed values to fit the model, and find that they generates almost identical results. So for simplicity we only use raw values in the following values.

**(2) corrLR (Correlation screening model)**

Unlike the first model, here we only use those predictors with a correlation to Y that's higher than a threshold. The papre proposed threshold=0.1, and we also tried other values.

**(3) realCorrLR ("Real-time" correlation screening model)**

This one is similar to (2), except that we exclude those predictors in our model before they were first proposed (or "invented") in history.

For example, a certain indicator might be first noticed in 2006, and later people fill the values of this indicator before 2006. In this case we only include it after 2006.

This is the model with the best performance in the paper

**(4) elasticNet (Elastic net model)**

This model was not mentioned in the paper.

We test different combination of parameters (alpha, which controls the size of penalty term; and l1_ratio, which controls the ratio of l1_norm penalty and l2_norm penalty.)



## C. Model Backtesting

### Baseline Metrics

Before running backtests for all of our indiviudal models, we calculate annualized and cumulative returns, as well as an annualized sharpe ratio, for an SPY "Buy & Hold" strategy to establish a passive investment baseline.

We also generate the cumulative returns of the 3 Month T-Bill rate, less 30bps, to follow the Hull & Qiao study and demonstrate the performance of cash earning a conventional risk-free rate of deposit.


### Backtest Design

We structure a dedicated backtest for each individual model, based on 3 speciifc criteria:

	Timeframe:
		- Predicted Forward Market Return (130 or 60 day)
		- Training Lookback Period (10 or 5 year)

	Model:
		- LR_Trans
		- corrLR
		- elasticNet
		- realCorrLR
		- simpLR

	Model Version:  
		- Regression screening models (corrLR, realCorrLR, elasticNet) are 
			implemented using multiple screening thresholds   

The time series of projected equity premiums for each Timeframe/Model/Model Version are then scaled using a multiplier of 8, per Hull, to generate a daily position weight with the following floor/cap thresholds:

	-Min Weight (Short): -0.50
	-Max Weight (Long): 1.50

As in the Hull study, trading costs are effectively negated due to the ample liquidity of SPY. This ensures that any daily position re-weighting can be resloved by submitting the necessary buy/sell orders to the closing auction, resulting in trade execution at SPY's Close price.


### Backtest Results

Overall, projected model performance appears to underperform the results shown in the Hull & Qiao research. From June 2001 to May 2015, their two top-performing correlation screening models boast annualized returns over twice that of the SPY Buy & Hold strategy (approximately 12%) and sharpe ratios over 4x greater (around 0.85). By comparison, our best model (also using correlation screening) can only project annualized returns of 6% and a sharpe of 0.54:

	Correlation Screening (Hull & Qiao):
		- Annualized Return: 12.11%
		- Sharpe Ratio: 0.85

	Real-Time Correlation Screening (Hull & Qiao):
		- Annualized Return: 11.66%
		- Sharpe Ratio: 0.88

	Real-Time Correlation Screening (Linear Forecasting Replication):
		- Annualized Return: 6.03%
		- Sharpe Ratio: 0.54


This underperformance is also borne out when visualizing our model's cumulative returns:


Extending the testing period past the end of the Hull study to include our most recent data fails to add 
significant improvement:


Determining the exact cause of this gap in projected performance will most likely require further review and examination of our predictor classes to identify the largest discrepancies with equivalent Hull data.         






Normal text **bold** then *italic*.
Escape \* \` \< \_ \# \\ & more.

1. Order list
- Unorder list ( - or + )

code: `a === a`

> blockquote

URL: [Edditoria][1] | image: ![2][]

[1]: https://edditoria.blogspot.com
[2]: https://avatars0.githubusercontent.com/u/2234073?v=3&s=40

<!-- please comment -->

# Enjoy! :)

[[https://github.com/niyuan17/Linear_Forecasting/blob/master/correlation_of_predictors.jpg|alt=octocat]]





