<div  align=center><font face="华文行楷" size=180>NNNU</font></div>



<div align=center><h1>Python Data Analysis and Visualisation</h1></div>



  

<div STYLE="page-break-after: always;"></div>

## Project Overview



### 1.1 Project background:

Internet is one of the most important and influential technologies in today's era, and it has profoundly changed people's life, work, study and other aspects. Internet user data is an important indicator reflecting the level and potential of Internet development, which can help us understand the strengths and weaknesses of different countries and regions in the field of Internet, as well as the differences and imbalances that exist. The number of global Internet users has grown rapidly over the past decade, with China being the world's largest Internet market. However, there are some problems and challenges with global and Chinese Internet user data. By analysing and visualising global and Chinese Internet user data, we can better grasp the changing trends and distribution of the Internet sector, as well as predict future directions and challenges.

### 1.2 Data Source:

The data comes from the dataset named Global Internet users on kaggle, the link to the dataset: [Global Internet users | Kaggle](https://www.kaggle.com/datasets/ashishraut64/internet- users), which contains information about global Internet users from 1980-2020. It includes information such as the name of the country or region, the country code, the year, the number of mobile Internet subscriptions per 100 people, the proportion of Internet users to the total population, the number of Internet users, and the number of broadband subscriptions per 100 people.

### 1.3. program function:

Analyse and visualise various data on global users per year, such as total number of Internet users, number of Internet subscriptions on mobile, percentage of Internet users, and number of broadband subscriptions.

   - Plot pie charts and bar charts of the percentage of users in each country-region in 2020 to show the distribution and differences in the percentage of Internet users globally.
   - To draw histograms of the distribution of the share of Internet users in each country-region in 2020, showing the characteristics and bias of the distribution of the share of Internet users globally.
   - To plot a scatterplot of the proportion of Internet users and mobile Internet subscriptions in each country-region in 2020, and analyse the correlation between them using a linear regression model.
   - Plot the word clouds of the names of the three countries and regions with the largest proportion of Internet users in each year to demonstrate the dominance and influence of the global Internet sector.
   - Analyse and visualise the data on Chinese Internet users to demonstrate China's level of development and potential in the Internet sector, and use multiple linear regression models to predict the total number of Internet users in China by 2050.

### 1.4. Introduction to third-party libraries used:

   - numpy library: used for numerical computation, such as the creation, manipulation and operation of arrays, matrices, vectors, and so on.

   - pandas library: used for data processing, such as reading, cleaning, grouping, aggregating, merging, etc.
   - matplotlib library: used to draw graphs, such as line graphs, bar charts, pie charts, etc., as well as set the style of the graphs, titles, labels and so on.
   - seaborn library: used to draw graphs, such as histograms, scatterplots, etc., as well as set the theme, colour, etc. of the graphs.
   - wordcloud library: used to configure and generate word clouds, such as setting the shape, size, font, etc. of the word cloud.
   - sklearn library: for performing linear regression analysis, such as creating linear regression models, fitting data, predicting data, evaluating models, etc.







## Function Implements



### 2.1. Data reading and implementation of tool functions

Use `read_csv` function to read `Final.csv` file to get global internet user information, define two tool functions `set_seaborn_properties`, `get_2020_entities_dataframe`.

```python
# Read out all the data from the dataset
global_users = pd.read_csv('. /data/Final.csv', delimiter=','', usecols=range(1, 8))

# This function is used to configure the theme of each seaborn diagram, which provides some default configurations that need to be modified are provided in the parameters, depending on the aesthetics and usefulness of the diagram need to change the parameters
def set_seaborn_properties(context='talk', font_scale=0.8)

# This function is used to get a DataFrame consisting of 2020 data for all Entities.
def get_2020_entities_dataframe()
```

### 2.2 Analysis and visualisation of global users' annual data

A function called `global_internet_users_analysis` is defined to analyse and visualise global users per year. In this function, the matplotlib and seaborn libraries are used to graph the total number of global internet users per year, the number of global mobile internet subscriptions per 100 people per year, the ratio of internet users, and the average number of broadband subscriptions per 100 people per year.

``````python
plt.subplot(2, 2, 1) # Drawing subgraphs
sns.lineplot(data=internet_users_sum_data, x='Year', y='sum') # line graph
plt.bar(column_mean.index, column_mean.values, color='cornflowerblue', width=0.6) # Combine with line drawings to make a fuller composition

for column in ['Cellular Subscription', 'Internet Users(%)', 'Broadband Subscription']：
    plt.subplot(2, 2, i)
    i += 1
    # Max
    sns.lineplot(data=max_data, x='Year', y='max', label=column + ' max', lw=2, linestyle=(0, (5, 1)))
    # Min
    sns.lineplot(data=mean_data, x='Year', y='mean', label=column + ' mean', lw=3, linestyle=(0, (1, 1)))
``````

![image-20240529104102747](https://fakercodes.oss-cn-hangzhou.aliyuncs.com/sl/OS202405291041811.png?sleflearingnotes)

It can be seen from the figure:

- The total number of Internet users worldwide has shown a trend of rapid growth, especially after 2000. This shows that the development and popularity of Internet technology, as well as people's demand for and reliance on the Internet have been increasing.

- The number of mobile Internet subscriptions per 100 people in the world has also shown a rapid growth trend, especially after 2005, and the growth rate is more obvious. This indicates that the popularity and convenience of mobile devices, as well as people's demand and preference for mobile Internet are both increasing.

- The proportion of people using the Internet globally also shows a fast-growing trend. This indicates that the Internet has become an indispensable part of people's life, work and study, as well as that the coverage and access to the Internet are expanding and improving.

- The number of broadband subscriptions per 100 people globally has shown a slow growth trend, but the growth rate has slowed down after 2010. This suggests that there is scope and potential for the growth and penetration of broadband networks, as well as that the competitiveness and attractiveness of broadband networks may have been affected by mobile networks.



### 2.3. Plotting Pie and Bar Charts of Percentage of Users by Country Region in 2020

A function named `entities_2020_internet_users_percentage_pie_bar` is defined to plot a pie chart and a bar chart of the percentage of users in each country region in 2020. In this function, a DataFrame encapsulating the 10 groups of data with the highest number of users in 2020 for each country and region is obtained first, and the other data is replaced by `other` data, and the pie and bar charts are plotted using matplotlib and seaborn libraries.

```python
# Filter only the 10 sets of data with the highest number of users, and replace the rest with `other`.
entity_2020_df.sort_values(by='No. of Internet Users', axis=0, ascending=False, inplace=True)
processed_data = pd.concat([entity_2020_df.head(10), other_df], axis=0, join='outer')

# Pie charts drawn
plt.pie(processed_data['No. of Internet Users'], labels=processed_data.index, explode=explode_arr,
            labeldistance=1.1, autopct='%2.1f%%', pctdistance=0.9, shadow=True)

# Plotting bar charts
sns.barplot(data=data, x='Entity', y='Percent')
```



![image-20240529104124347](https://fakercodes.oss-cn-hangzhou.aliyuncs.com/sl/OS202405291041377.png?sleflearingnotes)

![image-20240529104138543](https://fakercodes.oss-cn-hangzhou.aliyuncs.com/sl/OS202405291041599.png?sleflearingnotes)

It can be seen from the figure:

- In 2020, the country and region with the highest proportion of Internet users in the world is China, with a proportion of 20.3 per cent, much higher than other countries and regions. This shows that China has a huge market size and potential in the field of Internet, as well as strong competitiveness and influence in Internet technology, applications and services.

- In 2020, the second highest proportion of Internet users in the world will be in India, accounting for 12.1%, but there is still a big gap compared with China. This indicates that India also has a large market size and potential in the Internet sector, but there is still much room for development and challenges compared with China.

- In 2020, the third highest proportion of Internet users in the world is South America, accounting for 9.7%, which is closer to India. This shows that the United States also has a large market size and potential in the Internet field, but there is also a large gap compared with China.

- In 2020, the top ten countries and regions in terms of the proportion of global Internet users also include Brazil, Indonesia, Russia, Japan, Mexico and Egypt. The share of these countries and regions is between 1.5% and 3.6%, which is relatively low. This shows that these countries and regions still have more room and potential for development in the field of Internet, but also face greater challenges and competition.

- In 2020, the proportion of Internet users in countries and regions ranked 11th or later in the world will only be about 37%, much lower than the proportion of China. This shows that these countries and regions still have large imbalances and gaps in the Internet field, and need to strengthen the popularisation and upgrading of Internet technology.



### 2.4. Histogram of the distribution of Internet users by country-region in 2020

A function called `entities_2020_internet_users_percentage_distribution_histogram` is defined to plot a histogram of the distribution of the percentage of Internet users by country in 2020. In this function, the DataFrame encapsulating the 2020 country data was first obtained, and then the histogram was plotted using the seaborn library.

```python
# data-get
data = pd.DataFrame({'Entity': internet_users_percentage_sr.index, 'Percent':internet_users_percentage_sr.values})

# Plotting histograms
sns.histplot(data, x='Percent')
```



![image-20240529104153487](https://fakercodes.oss-cn-hangzhou.aliyuncs.com/sl/OS202405291041520.png?sleflearingnotes)

As can be seen in the figure:

- In 2020, the distribution of the share of Internet users in each country-region shows a right-skewed distribution, with most of the country-regions clustered in the lower range, while a few country-regions reach a higher level of Internet users.

- In 2020, the highest value for the share of Internet users in each country-region is 100 per cent, the lowest value is 0 per cent, the mean is 47.9 per cent, the median is 53.9 per cent, and the standard deviation is 36.1 per cent. This shows that there are great differences and imbalances in the proportion of Internet users in various countries and regions, and that there is still much room for improvement in the level of Internet development in some countries and regions.



### 2.5. Scatter Plot of Internet Users Percentage and Mobile Internet Subscriptions by Country Region in 2020

A function called `entities_2020_internet_users_percentage_distribution_scatter` is defined to plot a scatterplot of the percentage of Internet users and mobile Internet subscriptions by country-region in 2020. In this function, the DataFrame encapsulated with the 2020 country-region data is first obtained, then the scatterplot is plotted using the seaborn library, and the relationship between the two is analysed using the linear regression model in the sklearn library.

```python
# Scatterplotting
sns.scatterplot(data=entity_2020_df, x='Internet Users(%)', y='Cellular Subscription',
                    palette='husl', hue='Entity', legend=None)  # Setting the hue parameter according to the region to make the colours rich


# One-way linear regression to analyse the relationship
x = entity_2020_df[['Internet Users(%)']]
model_1 = linear_model.LinearRegression()
model_1.fit(x, entity_2020_df[['Cellular Subscription']])
data = pd.DataFrame({'x': x['Internet Users(%)'], 'pred_y': [x[0] for x in model_1.predict(x)]})
sns.lineplot(data=data, x='x', y='pred_y')
```



![image-20240529104214541](https://fakercodes.oss-cn-hangzhou.aliyuncs.com/sl/OS202405291042572.png?sleflearingnotes)

As can be seen in the figure:

- In 2020, the proportion of Internet users and mobile Internet subscriptions in each country-region show a positive correlation, that is, the higher the proportion of Internet users in a country-region, the higher the mobile Internet subscriptions, and vice versa. This shows that the proportion of Internet users and the number of mobile Internet subscriptions are two indicators that influence and promote each other, reflecting the level of Internet development and convenience of a country or region.



### 2.6. Generate word clouds using the names of the three countries with the largest percentage of Internet users each year

A function called `draw_internet_users_percentage_annual_top_3_wordcloud` is defined to generate a word cloud by drawing the names of the three countries with the largest percentage of Internet users in each year. In this function, we first get the names of the three countries with the largest percentage of Internet users in each year, and then we use the wordcloud library to draw the word cloud.

```python
text = ''
year_groups = global_users.groupby('Year')
# Obtain data on the top three countries with the largest percentage of Internet users in each year.
for year, year_df in year_groups:
    year_df.sort_values(by='Internet Users(%)', ascending=False, inplace=True)
    top_3 = year_df.head(3)
    entities = top_3['Entity']
    # data processing
    for entity in entities:
        if len(entity.split()) > 1:
            text += entity.replace(' ', '_') + ' '  
            # Replacing spaces with underscores _ in the names of countries and territories with spaces in the name to avoid splitting a name into multiple words
        else:
            text += entity + ' '

# Mapping word clouds
wc = WordCloud(max_words=100, width=800, height=400, background_color='White',
               max_font_size=150, stopwords=STOPWORDS, margin=5, scale=1.5)
wc.generate(text)
plt.imshow(wc)
plt.axis("off")
plt.show()
```



![image-20240529104233984](https://fakercodes.oss-cn-hangzhou.aliyuncs.com/sl/OS202405291042019.png?sleflearingnotes)

As can be seen from the figure:

- Iceland, Norway and Sweden are the most frequently occurring countries and regions in the period 1980-2020, indicating that these countries and regions have a long history of high levels of development and dominance in the Internet sector, as well as high levels of population penetration and access.

- In the period of 1980-2020, the names of countries and regions with high frequency of occurrence also include Bermuda, Denmark, Finland, Moracco, Afghanistan, and United_States, etc. This indicates that these countries and regions have a long-term high level of development and advantages in the field of Internet, as well as high population penetration and access rate. This indicates that these countries and regions also have a long history of high levels of development and advantages in the Internet sector, as well as high population penetration and access rates.

- In the period of 1980-2020, the names of countries and regions that appear less frequently or do not appear are China, India, Brazil, Indonesia and so on. Combined with the results in 2.4, some of these country-regions are latecomers, such as China and India, while others have more room and potential for development in the Internet sector, such as Brazil and Indonesia.



### 2.7. Analysing and Visualising Chinese Internet User Data

Finally, we define a function named `chinese_users_analysis` for analysing and visualising Chinese Internet user data. Firstly, we obtain the information of Chinese Internet users by slicing. Then we used matplotlib and seaborn libraries to plot the value and growth rate of each index, and used the multiple linear regression model in sklearn library to predict the total number of Chinese Internet users by 2050.

```python
# Line chart of basic information
sns.lineplot(data=chinese_users, x='Year', y='No. of Internet Users', label='数量（单位：千万人）', lw=3)
sns.lineplot(data=chinese_users, x='Year', y='Internet Users(%)', label='占人口的比例', lw=3)
sns.lineplot(data=chinese_users, x='Year', y='Cellular Subscription', label='移动互联网订阅每一百人比例', lw=3)
sns.lineplot(data=chinese_users, x='Year', y='Broadband Subscription', label='宽带每一百人订阅比例', lw=3)
```



![image-20240529104306273](https://fakercodes.oss-cn-hangzhou.aliyuncs.com/sl/OS202405291043316.png?sleflearingnotes)

It can be seen from the figure:

- The number of Internet users in China shows a trend of rapid growth, especially after 2000, the growth rate is more obvious. This shows that China has a huge market scale and potential in the field of Internet, as well as strong competitiveness and influence in Internet technology, application and service.

- The proportion of Internet users in the population in China also shows a trend of rapid growth, especially after 2005, the growth rate is more obvious. This indicates that China has a high penetration and access rate in the Internet sector, as well as China's demand and reliance on the Internet sector are increasing.

- The ratio of mobile Internet subscriptions per 100 people in China also shows a rapid growth trend, especially after 2005, the growth rate is more obvious. This indicates the high penetration and convenience of mobile devices in China, as well as China's increasing demand and preference for mobile Internet.

- China's broadband subscription ratio per 100 people shows a slow growth trend, but after 2017, the growth rate has slowed down. This suggests that there is still some room and potential for broadband networks in China, as well as the fact that China's competitiveness and attractiveness in the broadband network space may have been affected by mobile networks.

```python
# Calculation of individual growth rates
rows = len(chinese_users.index)
for i in range(rows - 1):
    chinese_users.loc[:, 'increase of No. of Internet Users'].iloc[i + 1] = 0 if chinese_users.iloc[i]['No. of Internet Users'] == 0 else (chinese_users.iloc[i + 1].loc['No. of Internet Users'] - chinese_users.iloc[i]['No. of Internet Users']) / chinese_users.iloc[i]['No. of Internet Users']
······

# graph of figure
sns.lineplot(data=chinese_users, x='Year', y='increase of No. of Internet Users', lw=4,
                 label='数量（单位：千万人）增长率')
······
```



![image-20240529104333276](https://fakercodes.oss-cn-hangzhou.aliyuncs.com/sl/OS202405291043321.png?sleflearingnotes)

It can be seen from the figure:

- The growth rate of the number of Internet subscriptions and the growth rate of the ratio per 100 population in China are basically year-on-year growth, which tends to level off after a faster growth between 1993-2005, which shows that China has reached a high level of development in the field of Internet, and that China is developing steadily in the Internet.

- The growth rate of China's mobile Internet subscription per 100 people showed a levelling off after a faster growth between 1987-2005, especially after 2010, which indicates that China has reached a high level of penetration and convenience in the field of mobile devices, and that China has formed a good development trend in the field of mobile Internet.

- The growth rate of China's broadband subscription rate per 100 people declined and levelled off after soaring in 2000-2002. This indicates that China has some space and potential in the field of broadband networks, as well as strong competitiveness and attractiveness in the field of broadband networks.



```python
# scatterplot
sns.scatterplot(data=chinese_users, x='Year', y='No. of Internet Users')

# Ternary linear regression fitting
poly_reg = PolynomialFeatures(degree=3)
······
model_2.fit(x_m, chinese_users[['No. of Internet Users']])
data = pd.DataFrame({'x': x['Year'], 'pred_y': [x[0] for x in model_2.predict(x_m)]})

# Plotting line graphs
sns.lineplot(data=data, x='x', y='pred_y')
```



![image-20240529104352148](https://fakercodes.oss-cn-hangzhou.aliyuncs.com/sl/OS202405291043182.png?sleflearingnotes)

It can be seen from the figure:

- We used a multiple linear regression model from the sklearn library to fit a fitting curve to the total number of Internet users in China from 1980 to 2020. This curve can be used to describe the pattern of change of the total number of Internet users in China over time, as well as to evaluate the effect and significance of the fit.

```python
# predictions
pred_x = pd.DataFrame(np.arange(1980, 2031), columns=['Year'])
pred_x_m = poly_reg.fit_transform(pred_x)

# graph
plt.plot(pred_x, model_2.predict(pred_x_m))
```



![image-20240529104405227](https://fakercodes.oss-cn-hangzhou.aliyuncs.com/sl/OS202405291044263.png?sleflearingnotes)

It can be seen from the figure:

- By 2030, the total number of Internet users in China will reach 2.11 billion, this prediction has a certain degree of reasonableness, because China's Internet users of all indicators are growing rapidly, China's Internet has great potential for development and vitality of development.
- However, this prediction also has some limitations, this prediction only uses a data set, without considering the specific conditions of China, it is unreasonable to rely only on the linear growth of the number of analyses, more advanced models are needed, and take into account the problem of China's aging population, combined with the growth rate of China's population to further analyse, so that the prediction effect will be better./nthe end
