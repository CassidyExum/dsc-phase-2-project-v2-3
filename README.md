# Phase 2 Modeling Project

# Creating a model to predict house prices for Blackrock

The purpose of my project was to iterate on a model, using the features of the data given to me, to create a model for my stakeholder, Blackrock. Blackrock is an American Investment firm that has been getting involved in Real Estate all across America. The location given to us in the Data is new for them, and they tasked me with investigating and creating some way for them to determine housing prices.

## Step 1: Data Cleaning

The first thing I did was find missing values and clean up the columns in order to better use each column for modeling. 3 columns weren't completely full, but using my best guess for 2 of them I was able to fill the NAN values. The final column had no obvious assumption about what the NAN values can be substituted as, and I noted that the column was likely unnecessary for modeling, so it was dropped. 

## Step 2: Heatmap, Graphing, and Baseline Model

I begun by creating a heatmap of each features correlation to the price of the house, as well as a graph of every feature vs the price.

#### Distrubution of House Prices
![image](https://user-images.githubusercontent.com/104473048/185767031-d8a2455e-3dfb-4482-9e11-d23100263bb0.png)

#### Heatmap of Feature Correlation
![image](https://user-images.githubusercontent.com/104473048/185767042-57f10894-b45c-4e90-a9fd-df303c116333.png)

#### Scatterplot of every Feature vs Price
![image](https://user-images.githubusercontent.com/104473048/185767047-21d2b3a0-67d2-4285-971f-881db915f91e.png)

The first model only has a validation score of .48, so there was a lot of work to be done.

## Iteration

