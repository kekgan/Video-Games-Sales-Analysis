# **SC1015: Data Science Mini Project**

School of Computer Science and Engineering \
Nanyang Technological University \
Lab: FCSB 
 

Members: 
1. Chen YiChen
2. Keagan Kong Kai Yi
3. Tng Jun Wen

---
### Description:
This README briefly highlights what we have accomplished in this project. If you want a more detailed explanation of things, please refer to the the Jupyter Notebooks in this repository. They contain more in-depth descriptions and smaller details which are not mentioned here in the README.

---
### Table of Contents:
1. [Problem Formulation](#1-Problem-Formlation)
2. [Data Preparation and Cleaning](#2-Data-Preparation-and-Cleaning)
3. [Exploratory Data Analysis](#3-Exploratory-Data-Analysis)
4. [Machine Learning](#4-Machine-Learning)
5. [Conclusion](#5-Conclusion)

### **1. Problem Formulation**

#### 1.1) Our Question:
For this Mini-project, we will use data and variables in the form of the Genre, Publisher and Platform of a video game, to predict the correlation and pattern in Global Sales for the game.

#### 1.2) Our Dataset: 
The dataset we have chosen to use for this Mini-Project is "[Video Game Sales](https://www.kaggle.com/datasets/gregorut/videogamesales)" by Gregory Smith, username [gregorut](https://www.kaggle.com/gregorut), on Kaggle. This dataset contains a list of all video game sales with greater than 100,000 copies sold between the years 1980 and 2020. The fields, or columns that are included in this dataset are RANK of overall sales, NAME of the game, PLATFORM of the game's release, YEAR of the game's release, GENRE of the game, PUBLISHER of the game, sales in North America, Europe, Japan, other parts of the world (in millions), and total worldwide sales (millions).

#### 1.3) Rationale:
Entertainment has always been a large part of humanity and cultures all over the world. Even before industrialisation, indigenous people in villages were had folk songs to sing and intricate stories to tell. Over the past century, entertainment has evolved leaps and bounds, from theatre acts and plays to films and even more recently, short form videos on platforms like TikTok. However, one aspect of entertainment that has not changed is the presence of fun and enjoyment. Over the last half century, this fun and enjoyment has evolved to people of all ages playing video games, first as retro 8-bit games in arcades, then as games on our modern computers and console platforms in each household, such as the older Nintendo 64 or more modern consoles like the Sony PS5. As SCSE students, many of us have vast interests in video games and these games were large parts of our childhood, or played frequently in our current daily lives, or even both. As such, we have decided to look into the sales of video games over the years.



### **2. Data Preparation and Cleaning**
In this section of the project, we prepared and cleaned the dataset to help us analyse our data better and also to help us use our data for the purposes of machine learning in the later sections. 

We performed the following:
1. We use the isnull() function to check if there are any data entries that are missing any information, and the sum function to see how many Null values are in each column.
2. We use the dropna() function to remove Null data entries to "clean" the data to ensure that all the data can be compared to each other. 
3. Since 'Year' should not be a 'Float" data type, we can change the dtype of 'Year' to be in the datetime format using the to_datetime() function.



### **3. Exploratory Data Analysis**
Then, we explored our DataFrame further using Exploratory Data Analysis. To achieve this we did the following:

#### 3.1) Basic Exploration: 
We first check the columns of our DataFrame and then use the describe function to describe the dataset to get a general sensing of the data in each column and plot a heatmap to see the correlation values between each of the variables and see how all the variables correlate to one another.

From our heatmap, we can see that Global Sales has a high correlation with both NA and EU sales, much higher than JP and Other regions. This perhaps suggests that those two regions make up a majority of the sample count, or that their preferences are generally the most aligned with the Global audience. We will continue to zoom into the specifics of how each variable affects the Global Sales in the follow sections.

#### 3.2) Explored Sales By Region:
First we categorised games published by year and found that there were large increases after the years 1990 and 2000. We credited these results to the increasing presence of computers in homes and the release of the PlayStation 2 and XBOX respectively. 

Next, we grouped and compared video game sales over the years. Our findings show that NA produced more video game sales than EU, JP and other region sales in every single year (even though it was close in 1980). We can also see that the 3 years with the most sales are 1986, 2000 and 2003. Zooming in on those years in the dataset, these years saw the release of the original Legend of Zelda in 1986, Pokemon Crystal and Final Fantasy IX in 2000, and Need for Speed Underground and Mario Kart: Double Dash!! in 2003. Our findings also showed the periods with low video games sales, such as between 1983-1985 and 2004-2010, which both denoted periods of global recession. 

We then plotted a pie chart consolidating all the years and showed us the overall proportion of sales overall. From the pie chart, it is clear to see that NA sales make up a huge proportion of sales, accounting to almost half of all sales. This could be why NA Sales were shown to have an extremely high correlation with Global Sales earlier. EU has a population of 448 million people, Japan with 125 million and NA with 579 million. Even though NA's population is about 30% more than EU's population, the proportion of sales in NA are almost double that of EU. EU's population is more than triple that of Japan's, but Japan's sales still add up to more than half that of EU's. Overall, these numbers suggest that taking into account their respective population sizes, video games are the most popular in NA, followed by Japan, then EU and lastly the rest of the world.

#### 3.3) Explored Sales By Genre:
Here, we look at the number of games pubished by genres. We find that Action and Sports games overshadow the other genres. 

Next, we plot a bar graph to visualise how the number of video games in each genre stack up against each other in total. Our graph tells us that 'Action' is the genre with the largest number of games sold out of all the genres, with a sales of almost 500 million over the next highest genre, 'Sports'. This suggests that either (1) action games popular among gamers, or (2) the genre is very broad and many games end up falling into this category and counting as 'Action' sales. 

We tried to gather more insights by looking at how each Genre performed per region. We found that Action and Sports largely dominated and held the number 1 and 2 spots in terms of sales for every single region except one, which is largely in line with global sales. However, let us analyse the outlier here, being Japan. In Japan, we can see that although Action and Sports were still largely popular, holding the number 2 and number 3 spots respectively, the first place actually went to Role Playing Game(RPG), which falls as far as 6th or 7th place in the other regions. But why is this the case? This could be because many Japanese game developers have come up and published some of the "All-time Greats" when it comes to RPGs. Some examples of these would be Super Mario and Pokemon, which are household names even among non-gamers. Other popular RPGs made by Japanese companies include Final Fantasy, Monster Hunter and Sekiro. As a whole, Japan is home to many renowned video game companies like Bandai, Nintendo, SNK, FromSoftware, Capcom, etc.

#### 3.4) Explored Sales By Platform:
Another variable that may affect sales of the game is the platform that the game is released on. In this case, the popularity and availability of the console platform itself may also affect the sale of the video games released for the platform. Again, we first compared the number of games published by platform. we found that DS and PS2 games were the most popular throughout the 50 years that the dataset spans. 

Next, we delve into how well each platform actually sold by plotting it out in a bar graph to compare them. Here, we can see that games produced for the PS2, PS3, Xbox 360, Wii and DS had the highest amount of sales by a large margin compared to all other console platforms. This suggests that games produced for these 5 systems perhaps (1) were very large in quantity and many games were made for these platforms, (2) these 5 platforms were particulary popular with gamers, or (3) the particular games released during the lifespans of these platforms were particularly well received compared to other platforms.

Previously, we found that the PS2 and DS had the most games published for their platforms. Despite the PS3, XBOX 360 and Wii having less games published, they were still able to do exceedingly well in sales. This perhaps suggests these 3 platforms were extremely popular or that games released for these platforms were big titles.

#### 3.5) Explored Sales By Publisher: 
The 3 publishers that generated the most global sales are Nintendo, Electronic Arts, and Activision (not including Activision Blizzard and Activision Value). Even today, these studios are still considered to be among the top video game publishers today, publishing many AAA titles.

#### 3.6) Others: 
Lastly, we looked at the individual video games that ranked the highest in terms of sales in order to find anomalies that may have boosted the sales numbers of a particular Genre or Platform. Comparing the regions, we can see that Wii Sports had the most sales in NA and EU, and was 2nd place in other regions. Sales in NA and EU alone accumulated to account for almost 70 million of the roughly 80 million copies sold globally. Wii Sports is a game that was bundled with the Wii console and sold at a cheaper price, potentially accounting for this huge amount of sales. In Japan specifically, we can see that games in the Pokemon franchise held 5 out of the top 10 spots in games sold. Furthermore, the addition of Super Mario Bros., New Super Mario Bros. and Animal Crossing: Wild World, all also published by Nintendo, means that within Japan, 8 of the 10 most sold games were published by Nintendo. This could suggest that Japanese gamers had high loyalty or perception of Nintendo, which allowed Nintendo games to perform so well locally.

For further findings and explanations, please refer to the Jupyter Notebook.



### **4. Machine Learning**
Finally, we use the machine learning techniques we have learnt both within and outside the course to solve our problem.

#### 4.1) Uni-Variate Linear Regression
In particular, we will first perform Uni-Variate Linear Regression to use the amount of sales in North America, 'NA_Sales', to predict the total global sales, 'Global_Sales', for a game. For this problem, we will create a 80:20 train-test split. After taking a quick look at the correlation between the factors, we plot the Linear Regression lines and checked the intercept and coefficient of our regression line. Lastly, checked the Goodness of Fit on each dataset.

Goodness of Fit on Train Set:\
R^2 score		    : 0.8951904208681856\
Mean Squared Error	: 0.2679651464540287\
Mean Absolute Error	: 0.20178173874442204

Since our model's R^2 score is high, it indicates that our model explains more variance in the response variable. The relatively low MSE and MAE in our model suggests that our model's predictions are extremely close to the actual values. Overall, our model's high R^2 score and low MAE and MSE scores indicates that our model performs well.

Goodness of Fit on Test Set:\
R^2 score		: 0.8371062963220217\
Mean Squared Error	: 0.3348212574829934\
Mean Absolute Error	: 0.19400933193723097

Similar to the train data, our model's R^2 score is high and MSE & MAE are relatively low, indicating that our model explains more variance in the response variable and that our model's predictions are extremely close to the actual values.

Overall, our model's high R^2 score and low MAE and MSE scores indicates that our model performs well, even on the Test Set data.

#### 4.2) Multi-Variate Linear Regression
Now, we will perform Multi-Variate Linear Regression on our data. For the purpose of this Linear Regression, we will use 'NA_Sales', along with 'Genre' and 'Platform' to predict the total global sales for the game. Since both 'Genre' and 'Platform' are categorical data, we will use **Label Encoding** to convert those categorical variables into numerical variables that can be used in a linear regression model. With label encoding, we assign a numerical value to each possible value of the categorical variable. Now, we can once again create a 80:20 split in the data, and then use sklearn's LinearRegression model to perform Linear Regression on our data. Much like in our Uni-Variate Linear Regression, we use X_train as our predictor and y_train as our response, and then check the intercept and coefficients for this model, before lastly checking the goodness of fit on each model.

Goodness of Fit on Train Set:\
R^2 score		: 0.8953784343102612\
Mean Squared Error	: 0.26748445518555436\
Mean Absolute Error	: 0.2020273957408097

Once again, our model's R^2 score is high, while its MSE and MAE values are low, indicating that our model performs well.

Goodness of Fit on Test Set:\
R^2 score		: 0.8371478224418119\
Mean Squared Error	: 0.33473590226463595\
Mean Absolute Error	: 0.1938837218359854

Similar to the train data, our model's R^2 score is high and MSE & MAE are realtively low, indicating that our model explains more variance in the response variable and that our model's predictions are extremely close to the actual values.Overall, our model's high R^2 score and low MAE and MSE scores indicates that our model performs well, even on the Test Set data.

#### 4.3) Reflection and Modification:
By using more variables in our model, we expect the accuracy of our model's predictions to increase. However, we find that the R^2 score did not increase significantly between Uni-Variate and Multi-Variate Linear Regressions.

After being label encoded, the categorical data became numerical. Genre 'Sports' has a value 10, genre 'Racing' has a value 6, platform 'Wii' has a value of 26, platform 'NES' has a value of 11, etc. This will confuse the model because it may think that 'Sports' is somehow greater than 'Racing', while 'Wii' is somehow greater than 'NES', and so on. In other words, using label encoding presents a false numerical relationship, which should be avoided.

Instead, we tried using **one-hot encoding** to create new columns for each 'Genre' and 'Platform' and give them binary values, with True indicating the game is on the platform or in the genre, while False indicates it is not. Now, we can re-train our Multi-Variate Linear Regression model with our new DataFrame.

After splitting our dataset in a 80:20 train-test split again, we plotted our regression lines to see how the model performs, both on the Train Set and the Test Set. After checking the Goodness of Fit of the Model on each dataset, we are left with the followiing findings.

Goodness of Fit on Train Set:
R^2 score		: 0.9015339475927185
Mean Squared Error	: 0.25174674273697234
Mean Absolute Error	: 0.19716586966852673

Goodness of Fit on Test Set:
R^2 score		: 0.8423727711583765
Mean Squared Error	: 0.32399623670320493
Mean Absolute Error	: 0.19224731021548905

We find that switching the method of encoding from Label Encoding to One-hot Encoding did not increase the accuracy of our model. Since we already established that NA sales and global sales had a high correlation and accuracy of model, all this showed was that there was a weak relationship between platform and genre, and global sales.

As such, we looked into the relationship between platform and genre, and global sales. By training a Linear Regression model using only these variables, we were able to find the relation between these models. Below is the Goodness of Fit of the Model for these findings.

Goodness of Fit on Train Set:\
R^2 score		: 0.03989516078189126\
Mean Squared Error	: 2.4546862603917057\
Mean Absolute Error	: 0.5622799812100164

Goodness of Fit on Test Set:\
R^2 score		: 0.0661869029307719\
Mean Squared Error	: 1.919414123168939\
Mean Absolute Error	: 0.5664269067429719

The result is as we suspected. R^2 value is very close to 0, indicating that there is a very weak relationship.

For further findings and explanations, please refer to the Jupyter Notebook.



### 5. Conclusion
In conclusion, this data science project aimed to predict video game sales based on various features such as genre, platform, and sales by individual region. Through the implementation of linear regression, we were able to develop a predictive model with promising performance in our Uni-Variate Linear Regression model.

Other than content covered during the course, our project included new techniques used in preparing the data for Linear Regression, in the form of Label Encoding and One-hot Encoding. Through encoding, we were able to use categorical data such as Genre and Platform as predictors in our data, in hopes of helping to make our final Linear Regression model more accurate.

Our final findings showed that both a Uni-Variate Linear Regression model comparing sales in NA to global sales, as well as a Multi-Variate Linear Regression model that added Genre and Platform into these predictors had extremely high accuracy, with an R^2 score of over 83%, indicating that it explains more than 83% of the variance in video game sales. Additionally, the model exhibited a low mean squared error and mean absolute error, suggesting that, on average, the model's predictions were close to the actual sales figures. 

However, when we tried to remove sales in NA as a predictor, in order to create a Multi-Variate Linear Regression model to see if there was a strong relationship between genre and platform of the game, when compared to the global sales of the game. The extremely low R^2 value of this model indicates that there is a very weak relationship between these factors.

Overall, these results could possibly indicate that a Multi-Variate Linear Regression model is not always necessarily better than a Uni-Variate Linear Regression model. This is because the additional independent variables we use as predictors may have a very weak relationship with the variable being predicter. In the example of our Linear Regression models, we found that Genre and Platform had a weak relationship with Global Sales, and as such did not necessarily help make our original Multi-Variate Linear Regression model better.

Future work could involve further refining the model by incorporating additional predictors from other datasets or exploring different machine learning algorithms to improve predictive performance.

\
\
\
\
\
\
\
Contributions by members:\
Finding the dataset: Chen Yichen\
Problem formulation: Keagan Kong, Tng Jun Wen\
Data preparation and cleaning: Keagan Kong, Tng Jun Wen\
Exploratory Data Analysis: Keagan Kong, Chen Yichen, Tng Jun Wen\
Uni-Variate Linear Regression: Keagan Kong, Chen Yichen\
Multi-Variate Linear Regression (Label Encoding): Keagan Kong, Chen Yichen\
Multi-Variate Linear Regression (One-hot Encoding): Chen Yichen\
Introduction and conclusion: Keagan Kong\
Analysis and explanatory text: Keagan Kong
