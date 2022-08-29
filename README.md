# Phase 2 Modeling Project

# Creating a model to predict house prices for Blackrock

The purpose of my project was to iterate on a model, using the features of the data given to me, to create a model for my stakeholder, Blackrock. Blackrock is an American Investment firm that has been getting involved in Real Estate all across America. The location given to us in the Data is new for them, and they tasked me with investigating and creating some way for them to determine housing prices.

## Step 1: Data Cleaning

The first thing I did was find missing values and clean up the columns in order to better use each column for modeling. 3 columns weren't completely full, but using my best guess for 2 of them I was able to fill the NAN values. The final column had no obvious assumption about what the NAN values can be substituted as, and I noted that the column was likely unnecessary for modeling, so it was dropped. 

## Step 2: Heatmap, Graphing, and Baseline Model

I began by creating a heatmap of each features correlation to the price of the house, as well as a graph of every feature vs the price.

#### Distribution of House Prices
![image](https://user-images.githubusercontent.com/104473048/185767031-d8a2455e-3dfb-4482-9e11-d23100263bb0.png)

#### Heatmap of Feature Correlation
![image](https://user-images.githubusercontent.com/104473048/187032892-bf31826b-5c0b-4bd6-817f-5bb0b0b03a62.png)

#### Scatterplot of every Feature vs Price
![image](https://user-images.githubusercontent.com/104473048/187032903-0a0c8af8-86b2-441c-b3cb-968a9ae57815.png)

The first model only has a validation score of .48, so there was a lot of work to be done.

## Iteration

The second model dropped features I believed to be unnecessary. This list was:

to_drop = ['id', 'lat', 'long', 'yr_built', 'zipcode']

After dropping these features the second model had a validation score of .61.

The third iteration features were chosen by running an Ordinary Least Squares model on the previous training data, and selecting only the significant features, i.e. p>|t|. This resulted in chosoing significant_features = ['bedrooms', 
                        'bathrooms', 
                        'sqft_living', 
                        'waterfront', 
                        'view', 
                        'floors', 
                        'sqft_above', 
                        'sqft_lot15',
                        'grade',
                        'condition',
                        'sqft_basement']. 
                        
The third iteration scored another .61.

The fourth model used Recursive Feature Elimination to select what features to use. 
The chosen features were 

fs_chosen_features = ['bedrooms', 
                      'bathrooms',
                      'sqft_living', 
                      'waterfront',
                      'view',
                      'condition',
                      'grade',
                      'sqft_above', 
                      'sqft_basement',
                      'sqft_living15', 
                      'sqft_lot15', 
                     ]

The fourth model scored .61, which was the same as the second model.

## Eliminating Outliers and Trying Again

At this point I realized that using the entire dataset was probably throwing things off. 62% is ok, but I wanted to try and do better. I decided to limit the data down to 0 < x < 2,500,000 price, rather than all the way up to the max (roughly 8,000,000). The first model done with this used every feature (suggested from Recursive Feature Selection), and resulted in a score of .71. This is the best score so far. I made an attempt to iterate on this approach, and limit outliers further. The 75th percentile was around 800,000 price, so I chose 1,000,000 as the cutoff point. I once again used Recursive Feature Selection, used the features offered, and obtained a similar score of .70.

With this result I decided that the .71 was a good stopping point.

## Future testing

In the future, creating a loop to change the maximum house price, limit the features to only numerical only, run Recursive Feature Selection, and then create the regression model and store the results would be a good stopping point to ensure higher accuracy.

I also attempted a few other tests. Both tests were attempting to learn about renovations and how they impact price. I first tried using the assumption that a renovation would increase the grade of the house by 1. So create a model that trains before adding 1 to grade, then testing after. Grade wasn't a good enough predictor and I lacked the ability to properly create the model. The second attempt was separating the data by the median renovated year (after dropping all houses that haven't been renovated). This left me with only 750ish data points. From here I wanted to find groups of similar sized houses (sqft_lot or sqft_living) and compare those houses depending on the recency of the renovation. I struggled to organize the data to accomplish this, and 750 data points felt too low.

