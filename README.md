# VeggiePrice

A robust prediction model for the wholesale produce market to be used by Souper Seconds. 

## Step 1: Data Munging
This was a tough and time consuming process. Since farmer's generally aren't the most data-savvy, all of the data came from hundreds of excel sheets with different formats. I created a macro that was able to import years of data regardless of the format, and involved a lot of data cleaning. 

## Step 3: Natural Language Processing
One of the most important things about the data was the name of the products. I performed TF-IDF on the product descriptions gage their importance. 

## Step 4: Dimensionality Reduction
Applying NLP techniques was useful, but it created a very sparse matrix. To reduce the dimensionality of the data and extract common features, I transformed it using RandomizedPCA from scikit-learn. 

## Step 5: Modeling
I tried a couple of different models to predict prices, but a Random Forest Regressor was a clear winner.

## Step 6: Validation and Results
An issue with the data was that popular products appeared numerous times since they were on many spreadsheets. It wouldn't say much about the model if it was predicting prices for produce that it had been trained on. To account for this, I created my own K-Fold Cross Validation so that with each fold, it was testing only products that did not appear in the training set at all. The model was able to predict prices of produce it had not seen before with R-square 0.96 and mean squared error 13%. 

The error was an interesting and beneficial result as it highlighted opportunity to improve pricing from what was originally in place. For example, there were cases where kale was the same price per pound for a 3 lb purchase and a 5 lb purchase. My model accounted for this quantity difference and suggested a customer pay less per pound for the 5 lb purchase than for the 3 lb purchase. If a customer agrees to buy more product, shouldn't they receive a lower rate?