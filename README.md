# Project Introduction: Predicting Google Stock Prices

The stock market is a dynamic and complex system that has captivated investors for centuries. Understanding the factors that drive stock prices is essential for making informed investment decisions. In this project, we will explore the use of machine learning techniques to predict future prices of Google (GOOG) stocks.

To train and evaluate our prediction models, will utilize historical stock data from Yahoo Finance. Yahoo Finance is a financial website that provides a comprehensive range of financial data, including stock prices, new, and market analysis. We will access the data using `yfinance` library in Python, which provides a convenient interface for retrieving and manipulating financial data from Yahoo Finance.

# Retrieving Google Stock Data

This code snippet retrieves historical data for Google (GOOG) stock from Yahoo Finance using the `yfinance` library. Thie first line creates a `Ticker` object for Google stock using the `yf.Ticker()` function. The second line retrieves historical data for the past five years using the `history()` method. The retrieved data is stored in a `Pandas` dataframe object named `google_df`.

The `5Y` argument passed to the `history()` method indicates that you want to retrieve historical data for the past five years. The retrieved data will include information such as the opening price, closing price, high price, low price, and volume for each trading day within the specified time range.

The `google_df` dataframe can be used for further analysis and prediction tasks. For example, you can use the data to visualize historical stock prices, calculate technical indicators, or train machine learning models to predict future stock prices.




# Visualizing Google Stock Closing Prices

This code snippet visualizes the closing prices Google (GOOG) stock using the `Matplotlib` library. The first line sets the visual style to the `darkgrid` using the `sns.set_style()` function. This style provides a dark background and grid lines for a clearer presentation.

The second line creates a new figure using the `plt.figure()` function. The figure size is set to (12, 5) using the figsize parameter, resulting in a wider and taller plot.

The third line adds a title to the plot using the `plt.title()` function. The title is set to `Overview of Closing Price`, which clearly indicates the purpose of the plot.

The fourth line plots the closing prices of Google stock using the `plt.plot()` function. The `google_df.Close` parameter specified that the closing prices from the `google_df` dataframe should be plotted.

The resulting plot displays a line graph that depicts the historical closing prices of Google stock over time. The dark background and grid lines provided by the `darkgrid` style enhance the readability of the plot. 





    
![overview](https://github.com/adelao747/google_analysis/assets/113153195/434c74f7-c835-4c25-bb27-7630ee374930)

    


# Adding Moving Averages to the Dataframe

This code snippet adds to moving averages; a 50-day moving average (fiftyDMA) and a 200-day moving average (200DMA), to the `google_df` dataframe. Moving averages are technical indicators to help identify trends and smooth out short-term fluctuations in stock prices.

The first line calculates the fiftyDMA by applying the `rolling()` function to the `Close` column with a window size of 50. This means that the average closing price over the past 50 days is calculated for each data point. The result is assigned to a new column named `fiftyDMA`.

The second line calculates the 200DMA ina similar manner, but with a window size of 200. This captures the long-term in Google stock prices. The result is assigned a new column named `200DMA`.

These moving averages provide valuable insights into the underlying price movements of Google stock, potentially aiding in trading decisions.




# Descriptive Statistics of the Dataframe

The provided dataframe contains information about various stock market statistics, including open, high, low and close prices, volume, dividends, stock splits, 50-day moving average (fiftyDMA) and 200-day moving average (200DMA).

The `describe()` function provides a summary of the statistical properties of each column in the dataframe. The output includes the count, mean, standard deviation, minimum, 25th percentile, 50th percentile (median), 75th percentile, and maximum values for each numerical column.

After removing `Dividends` and `Stock Splits` columns, the dataframe is left with the following columns: Open, High, Low, Close, Volume, fiftyDMA and 200DMA. These columns provide a comprehensive overview of the stock's price movements and trading activity.

Here's a summary of the key findings from the descriptive statistics:

- The average open price is 96.74, while the average high price is 97.44. This indicates a slight upward trend in the stock's price.

- The average low price is 49.05, and the average closing price is 96.93. This suggests that the stock price trends to close higher than it opens. The average trading volume is 5.345 billion, indicating trading activity in this stock.

- The fiftyDMA and 200DMA are both around 97.5, suggesting that the stock price has been relatively stable for the past 50 and 200 days.

Overall, the descriptive statistics provide a valuable snapshot of the stock's price movements, trading activity, and overall trends.








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



Note: There are `NaN` values in fiftyDMA and 200DMA columns because the moving averages have not been calculated for the first few rows of the dataframe. This is because the moving average calculation requires a certain number of previous data points in order to be calculated. For example, the 50-day moving average requires 50 previous data points, and the 200-day moving average requires 200 previous data points.

As a result, the fiftyDMA and 200DMA columns will contain `NaN` values for the first few rows of the dataframe, until there are enough data points to calculate the moving averages.



    

# Plotting Closing Price, 50 DMA and 200 DMA

The provided code visualizes the closing price, 50-day moving average (fiftyDMA) and 200-day moving average (200DMA) of a stock over time. The code utilizes the `sns.set_style()` function to set a dark grid style for the plot, enhancing readability.

The `plt.figure()` function creates a figure with a specified size of 10 units in width and 5 units in height, providing ample space for the plot. The title of the plot is set to `Closing Price vs 50 DMA vs 200 DMA` using the `plt.title()` function, clearly indicating the data being displayed.

The `plt.plot()` function is used to plot three lines representing the closing price, 50 DMA and 200 DMA. The closing price is plotted using the `google_df["Close"]` series, the 50 DMA is plotted using the `google_df["fiftyDMA"]` series, and the 200 DMA is plotted using the `google_df["200DMA"]` series. Labels are assigned to each line using the label parameter within the `plt.plot()` function.

Finally, the `plt.legend()` function is used to create a legend that displays the labels for each line, making it clear which line corresponds to which data series.





    
![closing_price_vs_50_vs200](https://github.com/adelao747/google_analysis/assets/113153195/270eaee3-1d53-401e-9033-e4c38c2769e3)

    


# Visualizing Correlation Matrix Using Heatmap

The provided code creates a heatmap to visualize the correlation matrix of the dataframe `google_df`. The correlation matrix represents the pairwise correlations between all numerical columns in the dataframe.

The heatmap is generated using the `sns.heatmap()` function, which takes the correlation matrix as input and displays correlations in a color-coded format. Darker shades of red indicate stronger positive correlations, while darker shades of blue indicate stronger negative correlations.

The `annot` parameter is set to `True`, which causes the correlation coefficients to be displayed within the heatmap cells. This allows for easy identification of the strength and direction of correlation between variables.

The heatmap provides a visual representation of the relationships between the numerical columns in the dataframe, making it easier to identify patterns and insights that might not readily be apparent from the individual correlation coefficients.





    
![correlation_matrix](https://github.com/adelao747/google_analysis/assets/113153195/ebdd38df-2f1e-4acc-8089-e99ea1044cc8)
    


# Plotting Histogram of Closing Price, 50 DMA and 200 DMA

A histogram is graphical representation of the distribution of a dataset. It is commonly used to visualize the frequency or count of the data within certain intervals, also known as bins. The x-axis of a histogram represents the range of values in the dataset, while the y-axis represents the frequency or count of those values.

A histogram plot shows the shape and spread of the data, allowing us to understand its distribution. It helps us identify patterns, outliers, and the central tendency of the dataset. By examining the histogram, we can gain insights into the data's skewness, kurtosis, and other statistical properties.

In summary, a histogram plot is a visual tool that displays the distribution of a dataset by representing the frequency or count of the values within specific intervals.





    
![histogram_closing](https://github.com/adelao747/google_analysis/assets/113153195/61f7f808-b19c-47d4-a4cf-1b11a5a48d88)
    






    
![histogram_50](https://github.com/adelao747/google_analysis/assets/113153195/5d53cb8f-ccbb-4fa9-be5e-7fa7c2855db8)
    






    
![histogram_200](https://github.com/adelao747/google_analysis/assets/113153195/5de784f8-d89f-472c-a741-e8929bc7da4f)
    


# Importing the Formula API from Statsmodels

The provided code import the formula API from the `Statsmodels` library in the current Python environment. The formula API is a convenient way to fit statistical models using the R-style formulas.

The `import statsmodels.formula.api as smf` statement aliases the Statsmodel formula API as smf. This makes it easier to refer to the formula API functions and methods without having to type the full library name each time.

The formula API is a powerful tool for data scientists and statisticians who want to work with R-style formulas in Python. It allows you to specify statistical models concisely and easily, and it provides a number of functions for fitting, evaluating, and visualizing models.







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
  <th>Date:</th>             <td>Sun, 31 Mar 2024</td> <th>  Prob (F-statistic):</th>  <td>  0.00</td>  
</tr>
<tr>
  <th>Time:</th>                 <td>13:31:01</td>     <th>  Log-Likelihood:    </th> <td> -3984.3</td> 
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



# Predicting Stock Prices Using Fitted Linear Regression Model

The provided code utilizes a fitted linear regression model to predict stock prices based on 50-day moving average (fiftyDMA) values. It utilizes the `Pandas` library to manage and manipulate the input data.

The code first creates a dataframe named `new_data` containing 50DMA values. This dataframe serves as the input data for the prediction process.

The `model.predict()` method is then invoked to generate predictions from the fitted linear regression model. The `new_data` dataframe is passed as input, and the model produces predictions for the closing price of the stock.

Finally, the predicted closing prices are printed using the `print()` function.

In summary, the code predicts stock prices based on 50DMA values using fitted linear regression model. It creates input data, generates predictions, and displays the results.



    

# Visualizing Predicted Closing Prices Based on 50DMA Values

The provided code generates a line plot to visualize the predicted closing prices of a stock based on 50-day moving average (50DMA) values. It utilizes the `Matplotlib` library for creating the plot.

The code first creates two separate line plots using the `plt.plot()` function. The first plot represents the 50DMA values from the `new_data`, and it is labeled as `New Data Values`. The second plot represents the predicted closing prices generates from the fitted linear regression model, and it labeled as `New Values Predicted`.

Finally, the `plt.legend()` function is used to create a legend that displays the labels for two line plots, making it clear which line corresponds to which data series. This visualization allows for easy interpretation of the relationship between the 50DMA values and the predicted closing prices.





    
![prediction](https://github.com/adelao747/google_analysis/assets/113153195/f4405474-d647-403a-a232-9d5fa24be511)
    



