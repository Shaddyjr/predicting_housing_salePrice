# Predicting Sale Price of homes in Ames, Iowa using Linear Regression and Regularization

## Problem Statement
Large purchases, such as buying a home, carry inherent risks that may be unforseen when buyers have incomplete information. Accurate predictions in home prices could mean the difference between a risky investment and a dream home. By providing a benchmark for a home's true value, both buyer and seller can feel confident a fair purchase is taking place.  

The value of a house is not easily summarized in a few lines. Buyers and sellers considers multiple aspects of a property when considering the overall cost of the lot. If a model could accurately predict a home's sale prices, the variables involved would show what the most important aspects of a house are. So, what variables about a house are needed to make an accurate prediction of it's sale price?

## Project Files
This project used 2 provided datasets:
1. [Training Dataset](https://git.generalassemb.ly/mahdi/project_2/blob/master/datasets/train.csv)
2. [Kaggle Test Dataset](https://git.generalassemb.ly/mahdi/project_2/blob/master/datasets/test.csv)

These data give housing data for Ames, Iowa from 2006-2010.

## Executive Summary
These data were provided by General Assembly, parsed from the Ames Iowa Housing Dataset, publicly available for use. This 
dataset was originally created by Dr. Dean DeCock, Professor of Statistics at Truman State University - [source](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt).  

Initially, I assumed the best predictions would come from a simple model including 3 key components: house quality, house size, and house age. However, these factors failed to account for the more granular affects on a house's sale price. I learned quite quickly if a variable plays even a small role in the determining the target, it should be included in the model, since the coefficient will essentially take care of the overall influence the variable plays.

Feature engineering was also something I struggled with. I intially only created one variable, house age, and then I made thousands of interaction terms. I discovered through research and speaking with others, engineered features should be __interpretable__ and relate to the problem in context. Failing to do so is akin to throwing "garbage" or random noise into the model, which will contribute to overfitting and an overall poorer model.

Although this problem was intended for a [Kaggle Contest](https://www.kaggle.com/c/dsi-us-8-project-2-regression-challenge), it ultimately served as a challenge for myself to rethink how I understood data. On multiple occasions I had to go backwards through my workflow in order to correct assumptions I made or faulty understandings of the data.

## Conclusions and Next Steps
Looking as some of the most significant coefficients, we can see the most important features that govern a house's sale price. We see some variables as expected, such as house area, quality, and age. However, some unexpected variables are also present.  

Having a __high scoring finished basement__ will play a large part in a house's sale price. This might suggest the functionality of having liveable basement space is a big benefit to the home owner. This may be unsurprising, though, as Ames is well known to be a college town with a high number of college students. Being able to utilize their basements allows home owners to maximize the amount of space they can rent out.  

Another surprising variable was the dummy variable for the __Crawford neighborhood__. Perhaps Ames residents would not be surprised by this, but all things being equal, a house in this neighborhood has a significant advantage and will tend to sell for more than houses in other neighborhoods. This suggests there are factors these data are not capturing fully, since neighborhoods are not easily quantifiable. Qualitative factors are likely at play here, such as the average income of local residents, education, age, demographics, number of children, etc.

### Assumptions
There are certian assumptions that come with a multiple regression model.  

One assumption is __the variables and the target are linearly related__. I'm confident this relationship is not violated, as the intuitive and common understanding of these housing variables is to be directly related to the house's sale price.

Another assumption is __the variables are independent from each other__. Viewing the correlations between the largest model coefficients, this assumptions would be difficult to avoid, as many of these variables are intrinsicly related.

Another assumption is __the residuals are normally distributed around 0, independent, and have a constant variance__. The residuals have a normal-looking distribution and show homoskedasticity, which suggests these assumptions are not violated.

I removed a number of outliers from the training dataset. For those erroneous outliers, I assume they were not significantly different from the rest of the data points. For those extreme outliers (more than 3 standard deviations from the mean), I am inherently fixing my model to predict on houses that do not show an extreme sale price. This means my model will likely be better at predicting typical houses, but will not accurately account for extremely high or low-end houses.

Lastly, these data are from 2006-2010, which is fairly old. In terms of predicting power, this model should be tested against more up-to-date information.

## Source Documentation
1. [Data Dictionary](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt)
2. [Researching Feature Engineering]()https://nycdatascience.com/blog/student-works/machine-learning/machine-learning-project-ames-housing-dataset/