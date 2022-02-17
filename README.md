# movie_and_series_data
Analyze movie and series data from the database:
https://www.kaggle.com/tmdb/tmdb-movie-metadata

Skill Keywords: Python(Jupyter, Pandas, Matplotlib/Seaborn, Numpy), Data Cleaning, Exploratory data analysis

# Questions asked
Q1. What independent variable data are estimators in regression analysis for dependent variable 'vote_average' (0-10 rating of movie)<br>
Q2. Is there a connection between movie release month (Can be extracted from 'release_date') and 'vote_average'? When is the best month to release a movie to get a high score?<br>
Q3. When is the most common release month for movies?<br>

# Work
See "regression_analysis.ipynb"<br>
Linear regression for target 'vote_average' (Movie score 0-10) was performed with these input variables (features):<br>
'popularity', 'runtime', 'vote_count', 'profit_percent', 'title_char_length', 'release_year', 'release_month_x'(11 month variables)

The below columns had to be wrangled out from original database:<br>
'profit_percent', 'title_char_length', 'release_year', 'release_month_x'(11 variables for months)

'profit_percent' was chosen over 'budget' or 'revenue' since it is not affected by inflation.

Data was split with a 80-20% between training and test.

# Exploratory data analysis
![Screenshot](Post-clean_vote_average_distribution.png)
![Screenshot](release_month_distribution.png)
![Screenshot](release_year_distribution.png)
![Screenshot](title_char_length_distribution.png)
![Screenshot](profit_percent_distribution.png)

# Linear regression result
The R-squared of the model was low, showing the model is not yet mature enough: <br>
0.3127<br>
![Screenshot](linear_regression_training_result.png)
![Screenshot](linear_regression_test_result.png)
<br>
The resulting scaled weights can infer what makes a movie score a higher 'vote_average'. <br>
Personal note: It might be difficult to predict a very subjective movie score ('vote_average')

# Resulting scaled weights:<br>
|  Features  | Weights |
| ------------- | ------------- |
| popularity  | 0.04  |
| runtime  | 0.22  |
| vote_count  | 0.25  |
| profit_percent  | 0.11  |
| title_char_length  | -0.04  |
| release_year  | -0.15  |
| release_month_2  | 0.02  |
| release_month_3  | 0.01  |
| release_month_4  | 0.01  |
| release_month_5  | 0.03  |
| release_month_6  | 0.01  |
| release_month_7  | 0.00  |
| release_month_8  | -0.01  |
| release_month_9  | 0.10  |
| release_month_10  | 0.07  |
| release_month_11  | 0.04  |
| release_month_12  | 0.05  |


The weights show these relationships between target and inputs<br>
'runtime':        Longer movies = higher vote_average<br>
'vote_count':     More votes = higher vote_average<br>
'profit_percent': More profitible = higher vote_average<br>
'release_year':   Older movies = higher vote_average<br>
'release_month':  Movies released in September = Slightly higher vote_average<br>

# Conclusions
Q1. 'vote_count', followed by 'runtime' had the strongest weight on the target 'vote_average' (0-10 rating of movie).<br>
Q2. September month seems to historically had the highest score 'vote_average' (0-10 rating of movie).<br>
Q3. September month was also the most common month for movies to be released.<br>

# Future possible work:
1. Inflation adjust 'budget' and 'revenue' and use as input.

# Misc notes
Popularity is defined by <br>
https://developers.themoviedb.org/3/getting-started/popularity