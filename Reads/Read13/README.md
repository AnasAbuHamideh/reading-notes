Scikit-learn is a powerful Python module for machine learning. It contains function for regression, classification, clustering, model selection and dimensionality reduction. Today, I will explore the sklearn.linear_model module which contains “methods intended for regression in which the target value is expected to be a linear combination of the input variables”.

In this post, I will use Boston Housing data set, the data set contains information about the housing values in suburbs of Boston. This dataset was originally taken from the StatLib library which is maintained at Carnegie Mellon University and is now available on the UCI Machine Learning Repository. UCI machine learning repository contains many interesting data sets, I encourage you to go through it.

So come on lets have fun with linear regression,

Exploring Boston Housing Data Set
The first step is to import the required Python libraries into Ipython Notebook.
This data set is available in sklearn Python module, so I will access it using scikitlearn. I am going to import Boston data set into Ipython notebook and store it in a variable called boston.

sklearn

The object boston is a dictionary, so you can explore the keys of this dictionary.

boston keys

boston data shape

I am going to print the feature names of boston data set.

boston features

I will see the description of this data set to know more about it. In this data set I have 506 instances(rows) and 13 attributes or parameters(columns). The goal of this exercise is to predict the housing prices in boston region using the features given.

boston description

Attribution

I am going to convert boston.data into a pandas data frame.

Pandas DataFrame

As you can see the column names are just numbers, so I am going to replace those numbers with the feature names.

bos columns

boston.target contains the housing prices.

Boston target

I am going to add these target prices to the bos data frame.

Bos Price

RAD

Scikit Learn
In this section I am going to fit a linear regression model and predict the Boston housing prices. I will use the least squares method as the way to estimate the coefficients.

Y = boston housing price(also called “target” data in Python)

and

X = all the other features (or independent variables)

First, I am going to import linear regression from sci-kit learn module. Then I am going to drop the price column as I want only the parameters as my X values. I am going to store linear regression object in a variable called lm.

Skitlearn linear model

If you want to look inside the linear regression object, you can do so by typing LinearRegression. and the press <tab> key. This will give a list of functions available inside linear regression object.