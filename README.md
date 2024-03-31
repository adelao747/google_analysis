# Project Introduction: Predicting Google Stock Prices

The stock market is a dynamic and complex system that has captivated investors for centuries. Understanding the factors that drive stock prices is essential for making informed investment decisions. In this project, we will explore the use of machine learning techniques to predict the future prices of Google (GOOG) stocks.

To train and evaluate our prediction models, we will utilize historical stock data from Yahoo Finance. Yahoo Finance is a financial website that provides a comprehensive range of financial data, including stock prices, new, and market analysis. We will access this data using the yfinance library in Python, which provides a convenient interface for retreiving and manipulating financial data from Yahoo Finance.

# Retrieving Google Stock Data

This code snippet retreives historical data for Google (GOOG) stock from Yahoo Finance using the yfinance library. The first line creates a `Ticker` object for Google stock using the `yf.Ticker()` function. The second line retreives historical data for the past five years using the `history()` method. The retrieved data is stored in a Pandas dataframe object named `google_df`.

The `5Y` argument passed to the `history()` method indicates that you want to retrieve historical data for the past five years. The retrieved data will include information such as the opening price, closing price, high price, low price, and volume for each trading day within the specified time range.

The `google_df` dataframe can be used for further analysis and prediction tasks. For example, you can use the data to visualize historical stock prices, calculate technical indicators, or train machine learning models to predict future stock prices.




# Visualizing Google Stock Closing Prices

This code snippet visualizes the closing prices of Google (GOOG) stock using the Matplotlib library. The first line sets the visual style to `darkgrid` using the `sns.set_style()` function. This style provides a dark background and grid lines for a clearer presentation.

The second line creates a new figure using the `plt.figure()` function. The figure size is set to (12, 5) using the figsize parameter, resulting in a wider and taller plot.

The third line adds a title to the plot using the `plt.title()` function. The title is set to `Overview of Closing Price`, which cleary indicates the purpose of the plot.

The fourth line plots the closing prices of Google stock using the `plt.plot()` function. The `google_df.Close` parameter specified that the closing prices from the `google_df` dataframe should be plotted.

The resulting plot displays a line graph that depicts the historical closing prices of Google stock over time. The dark background and grid lines provided by the `darkgrid` style enhance the readability of the plot.


![google_analysis_7_0](https://github.com/adelao747/google_analysis/assets/113153195/de4a3733-2e5a-47b2-a1af-a6480680e3a3)


    


# Adding Moving Averages to the Dataframe

This code snippet adds two miving averages; a 50-day moving average (50DMA) and a 200-day moving average (200DMA), to the `google_df` dataframe. Moving averages are technical indicators that help identify trends and smooth out short-term prices fluctuations in stock prices.

The first line calculates the 50DMA by applying the `rolling()` function fo the `Close` column with a window size of 50. This means that the average closing price over the past 50 days is calculated for each data point. The result is assigned to a new column named `fiftyDMA`.

The second line calculates the 200DMA in a similar manner, but with a window size of 200. This captures the long-term trend in Google stock prices. The result is assigned to a new column named `200DMA`.

These moving averages provide valuable insights into the underlying price movements of Google stock, potentially aiding in trading decisions.




# Descriptive Statistics of the Dataframe

The provided dataframe contains information about various stock market statistics, including open, high, low, and close prices, volume, dividends, stock splits, 50-day moving average (fiftyDMA), and 200-day moving average (200DMA).

The `describe()` function provides a summary of the statistical properties of each column in the dataframe. The output includes the count, mean, standard deviation, minimum, 25th percentile, 50th percentile (median), 75th percentile, and maximum values for each numerical column.

After removing the `Dividends` and `Stock Splits` columns, the dataframe is left with the following columns: Open, High, Low, Close, Volume, fiftyDMA and 200DMA. These columns provide a comprehensive overview of the stock's price movements and trading activity.

Here's a summary of the key findings from the descriptive statistics:

- The average open price is 96.74, while the average high price is 97.44. This indicates a slight upward trend in the stock's price.

- The average low price is 49.05, and the average closing price is 96.93. This suggest that the stock price tends to close higher than it opens. The average trading volume is 5.345 billion, indicating trading activity in this stock.

- The 50DMA and 200DMA are both around 97.5, suggesting that the stock price has been relativley stable for the past 50 and 200 days.

Overall, the descriptive statistics provide a valuable snapshop of the stock's price movements, trading activity, and overall trends.

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Volume</th>
      <th>Dividends</th>
      <th>Stock Splits</th>
      <th>fiftyDMA</th>
      <th>200DMA</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>1259.00</td>
      <td>1259.00</td>
      <td>1259.00</td>
      <td>1259.00</td>
      <td>1.259000e+03</td>
      <td>1259.0</td>
      <td>1259.00</td>
      <td>1210.00</td>
      <td>1060.00</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>102.86</td>
      <td>104.04</td>
      <td>101.80</td>
      <td>102.94</td>
      <td>2.879725e+07</td>
      <td>0.0</td>
      <td>0.02</td>
      <td>102.97</td>
      <td>103.62</td>
    </tr>
    <tr>
      <th>std</th>
      <td>30.09</td>
      <td>30.35</td>
      <td>29.81</td>
      <td>30.07</td>
      <td>1.283300e+07</td>
      <td>0.0</td>
      <td>0.56</td>
      <td>29.03</td>
      <td>25.04</td>
    </tr>
    <tr>
      <th>min</th>
      <td>52.15</td>
      <td>52.37</td>
      <td>50.68</td>
      <td>51.81</td>
      <td>6.936000e+06</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>55.71</td>
      <td>60.85</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>73.40</td>
      <td>74.28</td>
      <td>72.92</td>
      <td>73.47</td>
      <td>2.066815e+07</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>74.29</td>
      <td>78.41</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>104.25</td>
      <td>105.96</td>
      <td>103.31</td>
      <td>104.79</td>
      <td>2.565400e+07</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>105.19</td>
      <td>106.18</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>131.33</td>
      <td>132.86</td>
      <td>130.02</td>
      <td>131.39</td>
      <td>3.289900e+07</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>131.82</td>
      <td>126.14</td>
    </tr>
    <tr>
      <th>max</th>
      <td>154.01</td>
      <td>155.20</td>
      <td>152.92</td>
      <td>154.84</td>
      <td>1.241400e+08</td>
      <td>0.0</td>
      <td>20.00</td>
      <td>146.18</td>
      <td>139.27</td>
    </tr>
  </tbody>
</table>
</div>



Note: There are `NaN` values in `fiftyDMA` and `200DMA` columns because the moving averages have not been calculated for the first few rows of the dataframe. This is because the moving average calculation requires a certain number of previous data points in order to be calculated. For example, the 50-day moving average requires 50 previous data points, and the 200-day moving average requires 200 previous data points.

As a result, the fiftyDMA and 200DMA columns will contain `NaN` valkues for the first few rows of the dataframe, until there are enough data points to calculate the moving averages.



# Plotting Closing Price, 50 DMA and 200 DMA

The provided code visualizes the closing price, 50-day moving average (50 DMA), and 200-day moving average (200 DMA) of a stock over time. The code utilizes the `sns.set_style()` function to set a dark grid style for the plot, enhancing readability.

The `plt.figure()` function creates a figure with a specified size of 10 units in width and 5 units in height, providing ample space for the plot. The title of the plot is set to `Closing Price vs 50 DMA vs 200 DMA` using the `plot.title()` function, clearly indicating the data being displayed.

The `plt.plot()` function is used to plot three lines representing the closing price, 50 DMA and 200 DMA. The closing price is plotted using the `google_df["Close"]` series, the 50 DMA is plotted using the `google_df["fiftyDMA"]` series, and the 200 DMA is plotted using the `google_df["200DMA"]` series. Labels are assigned to each line using the label parameter within the `plt.plot()` function.

Finally, the `plt.legend()` function is used to create a legend that displays the labels for each line, making it clear which line corresponds to which data series.


![google_analysis_17_0](https://github.com/adelao747/google_analysis/assets/113153195/c951deae-dbf9-4716-a421-616082032700)


    


# Visualizing Correlation Matrix Using Heatmap

The provided code creates a heatmap to visualize the correlation matrix of the dataframe `google_df`. The correlation matrix represents the pairwise correlations between all numerical columns in the dataframe.

The heatmap is generates using the `sns.heatmap()` function, which takes the correlation matrix as input and displays the correlations in a color-coded format. Darker shades of red indicate stronger positive correlations, while darker shades of blue indicatge stronger negative correlations.

The `annot` parameter is set to `True`, which causes the correlation coefficients to be displayed within the heatmap cells. This allows for easy indentification of the strength and direction of correlation between variables.

The heatmap provides a visual representation of the relationships between the numerical columns in the dataframe, making it easier to identify patterns and insights that might not readily apparent from the individual correlation coefficients.


![google_analysis_19_0](https://github.com/adelao747/google_analysis/assets/113153195/cae533c4-67d8-4baa-9ea7-13b73ff6bd77)


    


# Plotting Histogram of Closing Price, 50 DMA and 200 DMA

A histogram is a graphical representation of the distribution of a dataset. It is commonly used to visualize the frequency or count of the data within certain invervals, also know as bins. The x-axis of a histogram represents the range of values in the dataset, while the y-axis represents the frequency or count of those values.

A histogram plot shows the shape and spread of the data, allowing us to understand its distribution. It helps us identify patterns, outliers, and the central tendendy of the dataset. By examining the histogram, we can gain insights into the data's skewness, kurtosis, and other statistical properties.

In summary, a histogram plot is a visual tool that displays the distribution of a dataset by representing the frequency or count of the values within specific intervals.


![google_analysis_21_0](https://github.com/adelao747/google_analysis/assets/113153195/b30fa0d3-b9a9-4742-870c-008dbcf3b46f)


    



![google_analysis_22_0](https://github.com/adelao747/google_analysis/assets/113153195/a0820c57-2d24-468b-8490-3e785044c655)


    



![google_analysis_23_0](https://github.com/adelao747/google_analysis/assets/113153195/48409efb-7f99-4935-ba77-b59fe3b61a1e)


    


# Importing the Formula API from Statsmodels

The provided code imports the formula API from the `Statsmodels` library into the current Python environment. The formula API is a convenient way to fit statistical models using R-style formulas.

The `import statsmodels.formula.api as smf` statement aliases the Statsmodels formula API as smf. This makes it easier to refer to the formula API functions and methods without having to type the full library name each time.

The formula API is a powerfule tool for data scientists and statisticians who want to work with R-style formulas in Python. It allows you to specify statistical models consicely and easily, and it provides a number of functions for fitting, evaluating, and visualzing models.






<table class="simpletable">
<caption>OLS Regression Results</caption>
<tr>
  <th>Dep. Variable:</th>          <td>Close</td>      <th>  R-squared:         </th> <td>   0.950</td> 
</tr>
<tr>
  <th>Model:</th>                   <td>OLS</td>       <th>  Adj. R-squared:    </th> <td>   0.950</td> 
</tr>
<tr>
  <th>Method:</th>             <td>Least Squares</td>  <th>  F-statistic:       </th> <td>2.319e+04</td>
</tr>
<tr>
  <th>Date:</th>             <td>Sat, 30 Mar 2024</td> <th>  Prob (F-statistic):</th>  <td>  0.00</td>  
</tr>
<tr>
  <th>Time:</th>                 <td>20:06:58</td>     <th>  Log-Likelihood:    </th> <td> -3984.3</td> 
</tr>
<tr>
  <th>No. Observations:</th>      <td>  1210</td>      <th>  AIC:               </th> <td>   7973.</td> 
</tr>
<tr>
  <th>Df Residuals:</th>          <td>  1208</td>      <th>  BIC:               </th> <td>   7983.</td> 
</tr>
<tr>
  <th>Df Model:</th>              <td>     1</td>      <th>                     </th>     <td> </td>    
</tr>
<tr>
  <th>Covariance Type:</th>      <td>nonrobust</td>    <th>                     </th>     <td> </td>    
</tr>
</table>
<table class="simpletable">
<tr>
      <td></td>         <th>coef</th>     <th>std err</th>      <th>t</th>      <th>P>|t|</th>  <th>[0.025</th>    <th>0.975]</th>  
</tr>
<tr>
  <th>Intercept</th> <td>    3.4526</td> <td>    0.691</td> <td>    4.997</td> <td> 0.000</td> <td>    2.097</td> <td>    4.808</td>
</tr>
<tr>
  <th>fiftyDMA</th>  <td>    0.9836</td> <td>    0.006</td> <td>  152.296</td> <td> 0.000</td> <td>    0.971</td> <td>    0.996</td>
</tr>
</table>
<table class="simpletable">
<tr>
  <th>Omnibus:</th>       <td>76.110</td> <th>  Durbin-Watson:     </th> <td>   0.099</td>
</tr>
<tr>
  <th>Prob(Omnibus):</th> <td> 0.000</td> <th>  Jarque-Bera (JB):  </th> <td>  89.197</td>
</tr>
<tr>
  <th>Skew:</th>          <td>-0.642</td> <th>  Prob(JB):          </th> <td>4.28e-20</td>
</tr>
<tr>
  <th>Kurtosis:</th>      <td> 3.350</td> <th>  Cond. No.          </th> <td>    394.</td>
</tr>
</table><br/><br/>Notes:<br/>[1] Standard Errors assume that the covariance matrix of the errors is correctly specified.



# Predicting Stock Prices Using Fitted Lineare Regression Model

The provided code utilizes a fitted linear regression model to predict stock prices based on 50-day moving average (50DMA) values. It utilizes the `Pandas` library to manage and manipulate the input data.

The code first creates a dataframe named `new_data` containing 50DMA values. This dataframe serves as the input data for the prediction process.

The `model.predict()` method is then invoked to generate predictions from the fitted linear regression model. The `new_data` dataframe is passed as input, and the model produces predictions for the closing price of the stock.

Finally, the predicted closing prices are printed using the `print()` function.

In summary, the code predicts stock prices based on 50DMA values using fitted linear regression model. It creates input data, generates predictions, and displays the results.



    0    101.810792
    1    104.761537
    2    106.728701
    3    111.646610
    4    116.564519
    dtype: float64


# Visualizing Predicted Closing Prices Based on 50DMA Values

The provided code generates a line plot to visualize the predicted closing prices of a stock based on 50-day moving average (50DMA) values. It utilizes the `Matplotlib` library for creating the plot.

The code first creates two separate line plots using the `plt.plot()` function. The first plot represents the 50DMA values from the `new_data`, and it is labeled as `New Data Values`. The second plot represents the predicted closing prices generates from the fitted linear regression model, and it is labeled as `New Values Predicted`.

Finally, the `plt.legend()` function is used to create a legend that displays the labels for two line plots, making it clear which line corresponds to which data series. This visualization allows for easy interpretation of the relationship between the 50DMA values and the predicted closing prices.


![google_analysis_29_0](https://github.com/adelao747/google_analysis/assets/113153195/59e4ba9a-d7f7-4c30-98e8-b2b2f6da7998)


    


