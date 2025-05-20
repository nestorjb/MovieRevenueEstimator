# Movie Revenue Estimator

[Link to codelab](MovieRevenueEstimator.ipynb)

## Business Understanding

The film industry is characterized by significant financial investment and protracted production schedules. Contemporary film budgets can vary dramatically, spanning from $1 million for independent productions to exceeding $300 million for major studio releases and take years to release. Investors are primarily concerned with recouping these substantial costs and generating profit. Therefore, understanding the determinants of box office revenue is essential. This study investigates the elements that significantly influence a film's commercial performance.

## Data Understanding

We will use the Kaggle TMDB Movie Dataset (https://www.kaggle.com/datasets/juzershakir/tmdb-movies-datase). The dataset provides 1208000+ movie information with numerical columns revenue, budget, runtime, popularity, vote_count, and vote_average and multiple multi-valued columns that describe the movie (genre, keywords, languages, countries, companies, etc). There are also 3 text columns (title, original_title, and overview). Most of the data has a revenue of 0 and there are outliers above revenue $1,500,000,000. 

For this specific model we will take into account the vote_average as movies are evaluated before releasing to the public.

## Data Cleaning

We performed the following tasks:

1. Removed revenue outliers by removing all rows where revenue is $0 and revenue is above $1,500,000,000.
2. Separated release date into two columns release month and release year.
3. Filled the NAs of release month and release year with the most frequent value.
4. Filled the NAs in text columns with an empty string.
5. As the dataset has multiple multi-valued columns (comma separated values), extract the individual values and calculated the impact of each individual value to the target variable (revenue) mean. We only take into account the values that are present in more than 1% of the dataset. The information gather in this task will be used to create boolean columns.

## Data Preparation

For each individual value that impact more than 1% of the dataset we create a boolean column.

## Model

We created 27 models using different techniques learned during the program. Through the process we saw that having only numeric values with polynomial feature 2 would give us good results as well as using all the data with one hot encoder and standard scale so we prepared multiple models to compare the results. We used Tfidf and Bert for the text columns but the model did not improve. We used an adjusted R2 to compare the models as the models may have different feature counts. The best model we found, that did not overfit, was a Random Forest model with max depth 5, one hot encoder, and polynomial features degree 2 with an adjusted R2 of 0.636748.

The elements that affect box office revenue positively in order are: 

1. Budget
2. Release_year
3. Vote_count
4. Runtime
5. Popularity
6. Vote_average
7. Production company is from the United States
8. It's available in English
9. The original language is English
10. Genres: Action, Comedy, Family, Fantasy, Animation, Thriller, Romance in that order
11. Production company: Universal Pictures, Paramount, 20th Century Fox, Columbia Pictures, Walt Disney Pictures, New Line Cinema, in that order
12. It's a sequel
13. Has keywords: During Credit Stinger, Based on a Novel or Book, After Credits Stinger, Musical, California
14. Release months: June, December, July

The elements that affect box office revenue negatively in order are: 

1. Genres: Drama, Documentary, in that order
2. Release months: September, April, January, October, in that order
3. Original language: Spanish, French, Russian, Turkish, Italian, in that order
4. Production Countries: Spain, India, France, Russia, Italy, Turkey, in that order
