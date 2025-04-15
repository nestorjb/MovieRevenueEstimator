# Movie Revenue Estimator

Colab Link: 

## Business Understanding

The film industry is characterized by significant financial investment and protracted production schedules. Contemporary film budgets can vary dramatically, spanning from $1 million for independent productions to exceeding $1.5 billion for major studio releases and take years to release. Investors are primarily concerned with recouping these substantial costs and generating profit. Therefore, understanding the determinants of box office revenue is essential. This study investigates the elements that significantly influence a film's commercial performance.

## Data Understanding

We will use the Kaggle TMDB Movie Dataset (https://www.kaggle.com/datasets/juzershakir/tmdb-movies-datase). The dataset provides 1208000+ movie information with revenue, budget, popularity and multiple multi-valued columns that describe the movie (genre, keywords, languages, countries, companies, etc). Most of the data has a revenue of 0 and there are outliers above revenue $1,500,000,000. 

## Data Cleaning

We performed the following tasks:

1. Remove revenue outliers by removing all rows where revenue is $0 and revenue is above $1,500,000,000.
2. Separate release date into two columns release month and release year.
3. Fill the NAs of release month and release year with the most frequent value.
4. Fill the NAs in text columns with an empty string.
5. Numeric columns don't have NAs.
6. As the dataset has multiple multi-valued columns (comma separated values), extract the individual values and calculated the impact of each individual value to the target variable (revenue) mean. We only take into account the values that affect more than the 1% of the dataset. The information gather in this task will be used to create boolean columns.

## Data Preparation

For each individual value that impact more than 1% of the dataset we create a boolean column.

## Model

We created over 20 models using different techniques learned during the program. Through the process we saw that having only numeric values with polynomial feature 2 would give us good results as well as using all the data with one hot encoder and standard scale so we prepared multiple models to compare the results. We used an adjusted R2 to compare the models as the models may have different feature count. 
