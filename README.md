# Linear_Forecasting
A Project Verifying Hull and Qiao’s Paper On Market Timing


Source of Data:
1. DP: Dividend-Price Ratio
Monthly
http://www.multpl.com/s-p-500-dividend-yield/table?f=m
2. PE: Price-to-Earnings Ratio
Monthly
http://www.multpl.com/table?f=m
3. BM: Book-to-Market
Calculated from price-to-book ratio
Quarterly
http://www.multpl.com/s-p-500-price-to-book/table/by-quarter
4.CAPE: Cyclically Adjusted Price to Earnings
Monthly
http://www.multpl.com/shiller-pe/table?f=m
5.BY: Bond Yields
10-year Treasury bond yield divided by the bond yield EMA
Daily
https://www.quandl.com/data/FRED/DGS10-10-Year-Treasury-Constant-Maturity-Rate
6.DEF: Default spread Aaa-Baa
The difference between Baa yield and Aaa yield
Aaa: Daily
https://www.quandl.com/data/FRED/AAA10Y-Moody-s-Seasoned-Aaa-Corporate-Bond-Yield-Relative-to-Yield-on-10-Year-Treasury-Constant-Maturity-DISCONTINUED
Baa: Daily
https://www.quandl.com/data/FRED/BAA10Y-Moody-s-Seasoned-Baa-Corporate-Bond-Yield-Relative-to-Yield-on-10-Year-Treasury-Constant-Maturity-DISCONTINUED
7.TERM: The yield difference between the 10-year Treasury Note and the three-month Treasury Bill.
10-year Treasury: (Same as in 5) Daily
https://www.quandl.com/data/FRED/DGS10-10-Year-Treasury-Constant-Maturity-Rate
3-month Treasury: Daily
https://www.quandl.com/data/FRED/DGS3MO-3-Month-Treasury-Constant-Maturity-Rate
