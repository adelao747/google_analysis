# Project Introduction: Predicting Google Stock Prices

The stock market is a dynamic and complex system that has captivated investors for centuries. Understanding the factors that drive stock prices is essential for making informed investment decisions. In this project, we will explore the use of machine learning techniques to predict the future prices of Google (GOOG) stocks.

To train and evaluate our prediction models, we will utilize historical stock data from Yahoo Finance. Yahoo Finance is a financial website that provides a comprehensive range of financial data, including stock prices, new and market analysis. We will access this data using the `yfinance` library in Python, which provides a convenient interface retrieving and manipulating financial data from Yahoo Finance.

# Retrieving Google Stock Data

This code snippet retrieves historical data for Google (GOOG) stock from Yahoo Finance using the `yfinance` library. The first line creates a `Ticker` object for Google stock using the `yf.Ticker()` function. The second line retrieves historical data for the past five years using the `history()` method. The retrieved data is stored in a `Pandas` dataframe object named `df`.

The `5Y` argument passed to the `history()` method indicates that you want to retrieve historical data for the past five years. The retrieved data will include information such as the opening price, closing price, high price, low price, and volume for each trading day within the specific time range.

The `df` dataframe can be used for further analysis and prediction tasks. For example, you can use the data to visualize historical stock prices, calculate technical indicators or train machine learning models to predict future stock prices.






# Visualizing Google Stock Closing Prices

This code snippet visualizes the closing prices of Google (GOOG) stock using the `Matplotlib` library. The first line sets the visual style to `darkgrid` using the `sns.set_style()` function. This style provides a dark background and grid lines for a clearer presentation.

The second line creates a new figure using the `plt.figure()` function. The figure size is set to (12, 5) using the `figsize` parameter, resulting in a wider and taller plot.

The third line adds a title to the plot using the `plt.title()` function. The title is set to `Overview of Closing Price`, which clearly indicates the purpose of the plot.

The fourth line plots the closing prices of Google stock using the `plt.plot()` function. The `df.Close` parameter specifies that the closing price from the `df` dataframe should be plotted.

The resulting plot displays a line graph that depicts the historical closing prices of Google stock over time. The dark background and grid lines provides by the `darkgrid` style enhance the readability of the plot.





    
![overview_close](https://github.com/adelao747/google_analysis/assets/113153195/9e77e5e8-c145-4d00-9689-5215d0d88d26)
 


# Adding Moving Averages to the Dataframe

This code snippet adds two moving averages; a 50-day moving average (fiftyDMA) and a 200-day moving average (200DMA), to the `df` dataframe. Moving averages are technical indicators that help identify trends and smooth out short-term price fluctuations in stock prices.

The first line calculates the fiftyDMA by applying the `rolling()` function to the `Close` column with a window size of 50. This means that the average closing price over the past 50 days is calculated for each data point. The result is assigned to a new column named `fiftyDMA`.

The second line calculates the 200DMA in a similar manner, but with a window size of 200. This captures the long-term trend in Google stock prices. The result is assigned to a new column named `200DMA`.

These moving averages provide valuable insights into the underlying price movements of Google stock, potentially aiding in trading decisions.




# Descriptive Statistics of the Dataframe

The provided dataframe contains information about various stock market statistics, including open, high, low, close, volume, dividends, stock splits, 50-day moving average (fiftyDMA) and 200-day moving average (200DMA).

The `describe()` method provides a summary of the statistical properties of each column in the dataframe. The output inclues the count, mean, standard deviation, minimum, 25th percentile, 50th percentile (median), 75th percentile and maximum values for each numerical column.

After removing the `Dividends` and `Stock Splits` columns, the dataframe is left with the following columns: Open, High, Low, Close, Volume, fiftyDMA and 200DMA. These columns provide a comprehensive overview of the stock's price movements and trading activity.

Here is a summary of the key findings from the descriptive statistics:

- The average open price is 96.74, while the average high price is 97.44. This indicates a slight upward trend in the stock's price.

- The average low price is 49.05, and the average closing price is 96.93. This suggests that the stock price tends to close higher than it opens. The average trading volume is 5.345 billion, indicating significant trading activity to this stock.

- The fiftyDMA and 200DMA are both around 97.5, suggesting that the stock price has been relatively stable over the past 50 and 200 days.

Overall, the descriptive statistics provide a valuable snapshot of the stock's price movements, trading activity and overall trends.



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
      <td>1258.00</td>
      <td>1258.00</td>
      <td>1258.00</td>
      <td>1258.00</td>
      <td>1.258000e+03</td>
      <td>1258.0</td>
      <td>1258.00</td>
      <td>1209.00</td>
      <td>1059.00</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>103.26</td>
      <td>104.46</td>
      <td>102.20</td>
      <td>103.35</td>
      <td>2.880056e+07</td>
      <td>0.0</td>
      <td>0.02</td>
      <td>103.37</td>
      <td>104.02</td>
    </tr>
    <tr>
      <th>std</th>
      <td>30.12</td>
      <td>30.38</td>
      <td>29.85</td>
      <td>30.11</td>
      <td>1.283803e+07</td>
      <td>0.0</td>
      <td>0.56</td>
      <td>29.00</td>
      <td>24.94</td>
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
      <td>61.25</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>73.73</td>
      <td>74.51</td>
      <td>73.22</td>
      <td>74.02</td>
      <td>2.067548e+07</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>75.31</td>
      <td>79.53</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>104.94</td>
      <td>106.19</td>
      <td>103.71</td>
      <td>105.04</td>
      <td>2.565400e+07</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>105.97</td>
      <td>106.54</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>131.63</td>
      <td>133.15</td>
      <td>130.30</td>
      <td>131.82</td>
      <td>3.290050e+07</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>132.22</td>
      <td>126.48</td>
    </tr>
    <tr>
      <th>max</th>
      <td>155.08</td>
      <td>157.00</td>
      <td>154.13</td>
      <td>156.50</td>
      <td>1.241400e+08</td>
      <td>0.0</td>
      <td>20.00</td>
      <td>146.18</td>
      <td>139.27</td>
    </tr>
  </tbody>
</table>
</div>



Note: There are `NaN` values in `fiftyDMA` and `200DMA` columns because the moving averages have not been calculated for the first few rows of the dataframe. This is because the moving average calculation requires a certain number of previous data points in-order to be calculated. For example, the 50-day moving average requires 50 previous data points, and the 200-day moving average requires 200 previous data points.



    

# Plotting Closing Price, fiftyDMA and 200DMA

The provided code visualizes the closing price, 50-day moving average (fiftyDMA) and 200-day moving average (200DMA) of a stock over time. The code utilizes the `sns.set_style()` function to set a dark grid style for the plot, enhancing readability.

The `plt.figure()` function creates a figure with a specified size of 10 units in width and 5 units in height, providing ample space for the plot. The title of the plot is set to `Closing Price vs 50 DMA vs 200 DMA` using the `plt.title()` function, clearly indicating the data being displayed.

The `plt.plot()` function is used to plot three lines representing the closing price, fiftyDMA and 200DMA. The closing price is plotted using the `df["Close"]`  series, the fiftyDMA is plotted using the `df["fiftyDMA"]` series and the 200DMA is plotted using the `df["200DMA"]` series. Labels are assigned to each line using the label parameter within the `plt.plot()` function.

Finally, the `plt.legend()` function is used to create a legend that displays the labels for each line, making it clear which line corresponds to which data series.





    
![close_50_200](https://github.com/adelao747/google_analysis/assets/113153195/73996f49-a2c8-4a95-884b-478578599293)
  


# Visualizing Correlation Matrix Using Heatmap

The provided code creates a heatmap to visualize the correlation matrix of the dataframe `df`. The correlation matrix represents the pairwise correlations between all numerical columns in the dataframe.

The heatmap is generated using the `sns.heatmap()` function, which takes the correlation matrix as input and displays the correlations in a color-coded format. Darker shades of red indicate stronger positive correlations, while darker shades of blue indicate stronger negative correlations.

The `annot` parameter is set to `True`, which causes the correlation coefficients to be displayed within the heatmap cells. This allows for easy identification of the strength and direction of correlations between variables.

The heatmap provides a visual representation of the relationships between the numerical columns in the dataframe, making it easier to identify patterns and insights that might not be readily apparent from the individual correlation coefficients.






![correlation_matrix](https://github.com/adelao747/google_analysis/assets/113153195/835e09ca-87f8-4227-9679-e3e1761a5a90)




# Plotting Histogram of Closing Price, fiftyDMA and 200DMA

A histogram is a graphical representation of the distribution of a dataset. It is commonly used to visualize the frequency or count of data within certain intervals, also known as bins. The x-axis of a histogram represents the range of values in the dataset, while the y-axis represents the frequency or count of those values.

A histogram plot shows the shape and spread of the data, allowing us to understand its distribution. It helps us identify patterns, outliers and central tendency of the dataset. By examining the histogram, we can gain insights into the data's skewness, kurtosis, and other statistical properties.

In summary, a histogram plot is a visual tool that displays the distribution of a dataset by representing the frequency or count of values within specific intervals.





    
![histogram_close](https://github.com/adelao747/google_analysis/assets/113153195/70a1599a-75fb-42bb-8d1b-4a23131cf101)
  






    
![histogram_50](https://github.com/adelao747/google_analysis/assets/113153195/c1a21366-a51f-41d1-ae3c-8f948d352d9c)

    






    
![histogram_200](https://github.com/adelao747/google_analysis/assets/113153195/29ee9af7-3235-4ba2-949a-5bc7136f4f81)

    


# Importing the Formuala API from Statsmodels

The provided code imports the formula API from the `Statsmodels` library in the current Python environment. The formula API is a convenient way to fit statistical models using R-style formulas.

The `import statsmodels.formula.api as smf` statement aliases the `Statsmodels` formula API as `smf`. This makes it easier to refer to the formula API functions and methods without having to type the full library name each time.

The formula API is a powerful tool for data scientists and statisticians who want to work with R-style formulas in Python. It allows you to specify statistical models concisely and easily, and it provides a number of functions for fitting, evaluating and visualizing models.

# Fitting a Linear Regression Model Using the Formula API

The provided code fits a linear regression model using the formula API from the `Statsmodels` library. The model predicts the `Close` price of a stock based on its `fiftyDMA`.

The model is fitted using the `smf.ols()` function, which takes the formula `Close ~ fiftyDMA` and the dataframe `df` as the independent variable.

The model is then summarized using the `model.summary()` method. The summary provides information about the model's fit, including R-squared, p-values, coefficients and standard errors.







<table class="simpletable">
<caption>OLS Regression Results</caption>
<tr>
  <th>Dep. Variable:</th>          <td>Close</td>      <th>  R-squared:         </th> <td>   0.950</td> 
</tr>
<tr>
  <th>Model:</th>                   <td>OLS</td>       <th>  Adj. R-squared:    </th> <td>   0.950</td> 
</tr>
<tr>
  <th>Method:</th>             <td>Least Squares</td>  <th>  F-statistic:       </th> <td>2.306e+04</td>
</tr>
<tr>
  <th>Date:</th>             <td>Sat, 06 Apr 2024</td> <th>  Prob (F-statistic):</th>  <td>  0.00</td>  
</tr>
<tr>
  <th>Time:</th>                 <td>22:22:14</td>     <th>  Log-Likelihood:    </th> <td> -3982.7</td> 
</tr>
<tr>
  <th>No. Observations:</th>      <td>  1209</td>      <th>  AIC:               </th> <td>   7969.</td> 
</tr>
<tr>
  <th>Df Residuals:</th>          <td>  1207</td>      <th>  BIC:               </th> <td>   7980.</td> 
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
  <th>Intercept</th> <td>    3.5218</td> <td>    0.695</td> <td>    5.064</td> <td> 0.000</td> <td>    2.157</td> <td>    4.886</td>
</tr>
<tr>
  <th>fiftyDMA</th>  <td>    0.9836</td> <td>    0.006</td> <td>  151.843</td> <td> 0.000</td> <td>    0.971</td> <td>    0.996</td>
</tr>
</table>
<table class="simpletable">
<tr>
  <th>Omnibus:</th>       <td>79.093</td> <th>  Durbin-Watson:     </th> <td>   0.100</td>
</tr>
<tr>
  <th>Prob(Omnibus):</th> <td> 0.000</td> <th>  Jarque-Bera (JB):  </th> <td>  93.355</td>
</tr>
<tr>
  <th>Skew:</th>          <td>-0.655</td> <th>  Prob(JB):          </th> <td>5.35e-21</td>
</tr>
<tr>
  <th>Kurtosis:</th>      <td> 3.369</td> <th>  Cond. No.          </th> <td>    398.</td>
</tr>
</table><br/><br/>Notes:<br/>[1] Standard Errors assume that the covariance matrix of the errors is correctly specified.



# Predicting Stock Prices Using Fitted Linear Regression Model

The provided code utilizes a fitted linear regression model to predict stock prices based on 50-day moving average (fiftyDMA) values. It utilizes the `Pandas` library to manage and manipulate the input data.

The code first creates a dataframe named `new_data` containing fiftyDMA values. This dataframe serves as the input data for the prediction process.

The `model.predict()` method is then invoked to generate predictions from the fitted linear regression model. The `new_data` dataframe is passed as input, and the model produces predictions for the closing price of the stock.

Finally, the predicted closing stock prices based on `fiftyDMA` values using fitted linear regression model. It creates input data, generates predictions, and displays the results.



    

# Visualizing Predicted Closing Prices Based on fiftyDMA Values

The provided code generates a line plot to visualize the predicted closing prices of a stock based on 50-day moving average (fiftyDMA) values. It utilizes the `Matplotlib` library for creating the plot.

The code first creates two separate line plots using the `plt.plot()` function. The first plot represents the `fiftyDMA` values from the `new_data`, and it is labeled as `New Data Values`. The second plot represents the predicted closing prices generated from the fitted linear regression mode, and it is labeled as `New Values Predicted`.

Finally, the `plt.legend()` function is used to create a legend that displays the labels for the two line plots, making it clear which line corresponds to which data series. This visualization allows for easy interpretation of the relationship between the `fiftyDMA` values and the predicted closing prices.





![prediction_model](https://github.com/adelao747/google_analysis/assets/113153195/d04691ee-782a-4356-8f33-2bdda2f4bfe7)

    




