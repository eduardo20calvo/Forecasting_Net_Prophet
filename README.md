# Mercado Libre Google Trends Analysis

The purpose of this analysis is to analyze the google trends for company Mercado Libre, whether it correlates to the price of the stock, and to forecast its revenue in a timeframe of 3 months using Prophet. The tools/libraries used in this analysis include Pandas, Datetime, Matplotlib, all within Python. Google Collab was used as the IDE since Holoviews and Prophet were also included in the notebook. 

The first part of this analysis included finding unusual patterns in the hourly google search traffic dataset. The dataset was read into a DataFrame and it was sliced into the month of May 2020 since during this month, MercadoLibre released it quarterly financial results. Below is a graph of the MercadoLibre Hourly Google Trends for May 2020:

![bokeh_plot](https://user-images.githubusercontent.com/104874384/206546937-62878e96-1cc1-49f5-973a-bbc48a85a81a.png)

The total search traffic for the month of May 2020 was compared against the monthly median search traffic for the year of 2020. What was found using some basic calculations, the total search traffic for May was greater than the monthly median serach traffic for 2020 by an average of 3,008.50 search requests.

The next part of the analysis included mining the search traffic dataset for seasonality. In other words, finding the day of the week and the week of the year with the most search traffic. The dataset was first grouped by the day of the week and plotting to give the following result:

![bokeh_plot (5)](https://user-images.githubusercontent.com/104874384/206549758-98ce2add-035d-4b43-9cf7-a4c54eacf90e.png)

In addition that same data was graphed into a heatmap to show the correlation between the day of the week and hourly data. This was the result:

![bokeh_plot (8)](https://user-images.githubusercontent.com/104874384/206550136-a8239009-2fcd-406e-a815-345ed17cd710.png)

Based on the heatmap, 10pm to 2am look to be the busiest hours receiving the highest number of search traffic ranging from 70s-90s per search hour.

Last but not least, the dataset was grouped by the week of the year and plotting into a graph. This was the result:

![bokeh_plot (9)](https://user-images.githubusercontent.com/104874384/206550405-cb59a004-afaa-4cb4-a254-5b8a700a676b.png)

What was found is that search traffic tends to increase during the winter holiday period. Initially from weeks 40-42 its trending down, however there seems to be an upward trend afterwards until week 51, before going back down at week 52. The peak seems to be almost similar to the peak witnessed in week 4.

The next part of the analysis is relating the search traffic to the company's stock price patterns. The dataset containing the historical stock prices were read into a DataFrame and plotted into a graph. See below:

![bokeh_plot (10)](https://user-images.githubusercontent.com/104874384/206554944-5f9c120d-f0ba-4e5b-884f-33277e11956f.png)

That data was then concatenated with the google search trends data and the concatenated dataset was sliced into the first half of the year 2020. Both columns were plotted into the graph to visualize their relationship:

![bokeh_plot (11)](https://user-images.githubusercontent.com/104874384/206555708-419c052a-2fa2-4a49-9ec6-6020acddfaee.png)
![bokeh_plot (12)](https://user-images.githubusercontent.com/104874384/206555712-40aa4923-0eca-4fbd-aad6-becb8a34797b.png)

Based on these graphs, there seems to be a positive relationship between the search tredns and the closing prices of Mercado Libre stock. This can be seen clearly between Feb. 25th through March 11th 2020. Between Feb. 25th and March 11th, the stock price fell from about 658 to 553. At the same time, the search trends fell from about 59 to 11.

Then the stock's volatility was found by calculating the standard deviation of the closing stock price return data over a 4 period rolling window. Below is the result in a graph:

![bokeh_plot (13)](https://user-images.githubusercontent.com/104874384/206556371-86b1a1b8-0612-4a2c-931a-b783e6a29b58.png)

A correlation table was then created using "Lagged Search Trends", "Stock Volatility", and "Hourly Stock Return". Based on the results, there is a slight negative relationship between the lagged search traffic and the stock volatility, however there is a slight positive relationship between the lagged search traffic and the stock price returns. It is hard to tell that there is a predictable relationship among them since the correlation is so small.

The Prophet Model was then used to forecast the google serach trends of the company in 80 days and the total revenue in 3 months. With calling the model, fitting the data and predicting the results, the following graph was generated for the google search trends:

![Screenshot 2022-12-08 150855](https://user-images.githubusercontent.com/104874384/206557536-755687d3-cfd8-4c3b-9af2-dd9e57b74b7e.png)

Based on the visualization created, there seems to be a downward trend in the near future for google search trends.

The Prophet Model also generated the following graph for future revenue within the company. 

![Screenshot 2022-12-08 151216](https://user-images.githubusercontent.com/104874384/206558128-b4dcc6ad-2391-482c-9b55-c5c40adf2896.png)

Based on the graph, there will be an increase in revenue in the near future, with 3 possibilities that can be considered:

Worst Case: 65,178
Most Likely case: Achieve modest 71,843.
Best Case: 78,520. This would be the best forecasted figure to consider.
