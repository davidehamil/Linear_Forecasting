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


|                          | 130_10  |         | 130_5   |         | 60_10   |         | 60_5    |         |
|--------------------------|---------|---------|---------|---------|---------|---------|---------|---------|
|                          | mean    | sharpe  | mean    | sharpe  | mean    | sharpe  | mean    | sharpe  |
| LR_Trans                 | 0.0031  | 0.0171  | 0.0255  | 0.1561  | 0.0374  | 0.2041  | 0.0446  | 0.2672  |
| corrLR_corr_0.05         | 0.0238  | 0.1617  | -0.0043 | -0.0253 | 0.0445  | 0.2746  | 0.0271  | 0.1625  |
| corrLR_corr_0.1          | 0.0290  | 0.2059  | 0.0132  | 0.0809  | 0.0466  | 0.3135  | 0.0496  | 0.3284  |
| corrLR_corr_0.15         | 0.0083  | 0.0504  | 0.0145  | 0.0931  | 0.0282  | 0.2788  | 0.0540  | 0.3624  |
| corrLR_corr_0.2          | -0.0080 | -0.0459 | 0.0379  | 0.2391  | 0.0269  | 0.3785  | 0.0584  | 0.4974  |
| corrLR_corr_0.25         | 0.0169  | 0.1158  | 0.0282  | 0.1761  | NaN     | NaN     | 0.0537  | 0.4812  |
| corrLR_corr_0.3          | 0.0393  | 0.2921  | 0.0198  | 0.1235  | NaN     | NaN     | NaN     | NaN     |
| corrLR_corr_0.35         | NaN     | NaN     | 0.0286  | 0.1767  | NaN     | NaN     | NaN     | NaN     |
| elasticNet_en_a0.1_r0.0  | 0.0238  | 0.1368  | -0.0024 | -0.0160 | 0.0201  | 0.1354  | 0.0097  | 0.0918  |
| elasticNet_en_a0.1_r0.1  | 0.0234  | 0.1504  | -0.0027 | -0.0194 | 0.0202  | 0.1559  | 0.0116  | 0.1181  |
| elasticNet_en_a0.1_r0.2  | 0.0314  | 0.2136  | 0.0104  | 0.0795  | 0.0193  | 0.1658  | 0.0083  | 0.0891  |
| elasticNet_en_a0.1_r0.3  | 0.0366  | 0.2720  | 0.0152  | 0.1205  | 0.0187  | 0.1859  | 0.0098  | 0.1107  |
| elasticNet_en_a0.1_r0.4  | 0.0348  | 0.2928  | 0.0151  | 0.1213  | 0.0172  | 0.2017  | 0.0079  | 0.0912  |
| elasticNet_en_a0.1_r0.5  | 0.0370  | 0.3493  | 0.0146  | 0.1196  | 0.0141  | 0.1987  | 0.0054  | 0.0637  |
| elasticNet_en_a0.1_r0.6  | 0.0343  | 0.3654  | 0.0132  | 0.1093  | 0.0106  | 0.1764  | 0.0059  | 0.0714  |
| elasticNet_en_a0.1_r0.7  | 0.0323  | 0.3761  | 0.0113  | 0.0955  | 0.0105  | 0.2111  | 0.0031  | 0.0406  |
| elasticNet_en_a0.1_r0.8  | 0.0276  | 0.3529  | 0.0120  | 0.1028  | 0.0056  | 0.1281  | -0.0022 | -0.0316 |
| elasticNet_en_a0.1_r0.9  | 0.0264  | 0.3604  | 0.0084  | 0.0734  | 0.0032  | 0.0792  | -0.0046 | -0.0679 |
| elasticNet_en_a0.1_r1.0  | 0.0217  | 0.3083  | 0.0044  | 0.0392  | 0.0016  | 0.0411  | -0.0061 | -0.0935 |
| elasticNet_en_a0.2_r0.0  | 0.0215  | 0.1263  | -0.0032 | -0.0220 | 0.0212  | 0.1463  | 0.0124  | 0.1201  |
| elasticNet_en_a0.2_r0.1  | 0.0316  | 0.2155  | 0.0094  | 0.0727  | 0.0189  | 0.1629  | 0.0089  | 0.0960  |
| elasticNet_en_a0.2_r0.2  | 0.0352  | 0.2973  | 0.0161  | 0.1296  | 0.0175  | 0.2053  | 0.0079  | 0.0919  |
| elasticNet_en_a0.2_r0.3  | 0.0341  | 0.3639  | 0.0135  | 0.1122  | 0.0104  | 0.1730  | 0.0065  | 0.0800  |
| elasticNet_en_a0.2_r0.4  | 0.0272  | 0.3483  | 0.0114  | 0.0978  | 0.0052  | 0.1194  | -0.0024 | -0.0336 |
| elasticNet_en_a0.2_r0.5  | 0.0213  | 0.3028  | 0.0042  | 0.0379  | 0.0015  | 0.0398  | -0.0058 | -0.0892 |
| elasticNet_en_a0.2_r0.6  | 0.0141  | 0.2168  | -0.0042 | -0.0407 | -0.0023 | -0.0654 | -0.0049 | -0.0847 |
| elasticNet_en_a0.2_r0.7  | 0.0096  | 0.1505  | -0.0061 | -0.0621 | -0.0036 | -0.1205 | -0.0014 | -0.0261 |
| elasticNet_en_a0.2_r0.8  | 0.0037  | 0.0580  | -0.0115 | -0.1274 | -0.0033 | -0.1198 | -0.0031 | -0.0699 |
| elasticNet_en_a0.2_r0.9  | 0.0039  | 0.0621  | -0.0112 | -0.1342 | -0.0013 | -0.0529 | -0.0069 | -0.1792 |
| elasticNet_en_a0.2_r1.0  | 0.0034  | 0.0541  | -0.0067 | -0.0845 | 0.0005  | 0.0249  | -0.0092 | -0.2634 |
| elasticNet_en_a0.3_r0.0  | 0.0200  | 0.1192  | -0.0029 | -0.0200 | 0.0179  | 0.1253  | 0.0132  | 0.1277  |
| elasticNet_en_a0.3_r0.1  | 0.0359  | 0.2705  | 0.0157  | 0.1250  | 0.0182  | 0.1828  | 0.0110  | 0.1248  |
| elasticNet_en_a0.3_r0.2  | 0.0337  | 0.3603  | 0.0134  | 0.1110  | 0.0108  | 0.1790  | 0.0068  | 0.0837  |
| elasticNet_en_a0.3_r0.3  | 0.0257  | 0.3517  | 0.0083  | 0.0731  | 0.0031  | 0.0755  | -0.0042 | -0.0623 |
| elasticNet_en_a0.3_r0.4  | 0.0141  | 0.2173  | -0.0043 | -0.0416 | -0.0024 | -0.0683 | -0.0047 | -0.0802 |
| elasticNet_en_a0.3_r0.5  | 0.0064  | 0.1004  | -0.0090 | -0.0952 | -0.0033 | -0.1185 | -0.0024 | -0.0493 |
| elasticNet_en_a0.3_r0.6  | 0.0038  | 0.0608  | -0.0110 | -0.1323 | -0.0013 | -0.0529 | -0.0072 | -0.1856 |
| elasticNet_en_a0.3_r0.7  | 0.0012  | 0.0193  | -0.0061 | -0.0803 | 0.0001  | 0.0053  | -0.0085 | -0.2570 |
| elasticNet_en_a0.3_r0.8  | -0.0017 | -0.0284 | -0.0105 | -0.1479 | 0.0001  | 0.0047  | -0.0081 | -0.2870 |
| elasticNet_en_a0.3_r0.9  | 0.0004  | 0.0069  | -0.0179 | -0.2675 | 0.0013  | 0.0530  | -0.0063 | -0.2391 |
| elasticNet_en_a0.3_r1.0  | 0.0039  | 0.0728  | -0.0187 | -0.2994 | 0.0008  | 0.0343  | -0.0065 | -0.2497 |
| elasticNet_en_a0.4_r0.0  | 0.0179  | 0.1072  | -0.0040 | -0.0282 | 0.0184  | 0.1300  | 0.0101  | 0.0984  |
| elasticNet_en_a0.4_r0.1  | 0.0371  | 0.3158  | 0.0153  | 0.1237  | 0.0176  | 0.2072  | 0.0069  | 0.0807  |
| elasticNet_en_a0.4_r0.2  | 0.0272  | 0.3508  | 0.0107  | 0.0919  | 0.0050  | 0.1136  | -0.0025 | -0.0354 |
| elasticNet_en_a0.4_r0.3  | 0.0141  | 0.2176  | -0.0048 | -0.0469 | -0.0024 | -0.0688 | -0.0050 | -0.0853 |
| elasticNet_en_a0.4_r0.4  | 0.0040  | 0.0632  | -0.0120 | -0.1331 | -0.0033 | -0.1198 | -0.0030 | -0.0678 |
| elasticNet_en_a0.4_r0.5  | 0.0034  | 0.0541  | -0.0066 | -0.0836 | 0.0005  | 0.0249  | -0.0092 | -0.2617 |
| elasticNet_en_a0.4_r0.6  | -0.0017 | -0.0284 | -0.0108 | -0.1513 | 0.0001  | 0.0047  | -0.0081 | -0.2856 |
| elasticNet_en_a0.4_r0.7  | 0.0028  | 0.0514  | -0.0193 | -0.2918 | 0.0010  | 0.0418  | -0.0063 | -0.2393 |
| elasticNet_en_a0.4_r0.8  | 0.0029  | 0.0544  | -0.0143 | -0.2364 | 0.0009  | 0.0373  | -0.0048 | -0.1909 |
| elasticNet_en_a0.4_r0.9  | 0.0033  | 0.0644  | -0.0142 | -0.2445 | 0.0012  | 0.0527  | -0.0053 | -0.2152 |
| elasticNet_en_a0.4_r1.0  | 0.0026  | 0.0509  | -0.0121 | -0.2149 | 0.0010  | 0.0414  | -0.0055 | -0.2259 |
| realCorrLR_realCorr_0.05 | 0.0252  | 0.1918  | 0.0305  | 0.2012  | 0.0586  | 0.3882  | 0.0409  | 0.2541  |
| realCorrLR_realCorr_0.1  | 0.0225  | 0.1645  | 0.0494  | 0.3278  | 0.0526  | 0.3639  | 0.0574  | 0.4554  |
| realCorrLR_realCorr_0.15 | 0.0070  | 0.0418  | 0.0476  | 0.3251  | 0.0341  | 0.3611  | 0.0584  | 0.4743  |
| realCorrLR_realCorr_0.2  | -0.0058 | -0.0340 | 0.0442  | 0.3008  | 0.0329  | 0.4793  | 0.0603  | 0.5371  |
| realCorrLR_realCorr_0.25 | 0.0206  | 0.1494  | 0.0289  | 0.1861  | NaN     | NaN     | NaN     | NaN     |
| realCorrLR_realCorr_0.3  | 0.0352  | 0.2756  | 0.0202  | 0.1279  | NaN     | NaN     | NaN     | NaN     |
| realCorrLR_realCorr_0.35 | NaN     | NaN     | 0.0355  | 0.2243  | NaN     | NaN     | NaN     | NaN     |
| simpLR                   | 0.0040  | 0.0224  | 0.0260  | 0.1590  | 0.0380  | 0.2073  | 0.0449  | 0.2689  |		

		
This underperformance is also borne out when visualizing our model's cumulative returns:

![Alt text](/data_description/realCorrLR_2001-2015.png)

Extending the testing period past the end of the Hull study to include our most recent data fails to add 
significant improvement:

![Alt text](/data_description/realCorrLR_2001-2017.png)

Determining the exact cause of this gap in projected performance will most likely require further review and examination of our predictor classes to identify the largest discrepancies with equivalent Hull data.         




