# Video-Game-Metacritic-Scores-Prediction
 An attempt to predict Metacritic scores of video games using several machine learning models in Python. <br>
 A complete walkthrough of the process can be found in each of the 5 notebooks.
 
 ## Contents
 1. Gathering Data from RWAG API
 2. Data Cleaning
 3. Video Game Data Analysis
 4. Preprocessing Dataset for Prediction
 5. Predictive Models Results - Regression


## Part 1: Gathering Data From RWAG API
Using the request library, make API calls from the [RWAG database](https://rawg.io/apidocs) to collect video game data.
**Note: Extract the data.rar file if needed (csv file is too large to push to GitHub)**

## Part 2: Data Cleaning
Examine the raw data, and trim it down such that the dataset only contains useful information for analysis and prediction. <br>
Data is processed with pandas, numpy and Abstract Syntax Trees (ast).

## Part 3: Video Game Data Analysis
Investigate the dataset to derive insights on the most popular games, genres, trends, etc. <br>
Data is visualised using matplotlib, seaborn, plotly and workcloud.

## Part 4: Preprocessing Dataset for Prediction
Prepare the cleaned dataset as an input for machine learning models. <br>
Specifically, the platforms, genres and tags columns (containing lists) are processed into binary columns:
- Platform families are grouped together with numpy
- Tags are cross-checked with [the tags scrapped from Steam](https://store.steampowered.com/tag/browse/#global_4305) with fuzzywuzzy and BeautifulSoup

These 3 pieces of information will be used as features in the predictive models. <br>
The train and test sets are then generated with sklearn. <br>
A simple prediction test using the Logistic Regression is made as well.

## Part 5: Predictive Models Results - Regression
The following regression models are used, along with their respective RMSE on the test set:

| Model                        | Test RMSE           |
| ---------------------------- |:-------------------:|
| Linear Regression            | 169784033252.96356  |
| Random Forest Regressor      | 9.487118217587387   |
| Support Vector Machine       | 9.857068901488233   |
| Decision Tree Regression     | 13.64271924908898   |
| K-Nearest Neighbors          | 10.592563672173583  |
| AdaBoost                     | 10.62350517308404   |
| Gradient Boost Regressor     | 10.086508353719507  |
| Extra Tree Regressor         | 13.182428792510434  |
| XGBoost Regressor            | 28.081992487362925  |
| Ridge Regression             | 9.877904001325112   |

Optimisation is been attempted to fine-tune the parameters of the models. Furthermore, the [pycaret library](https://pycaret.org/) is also used as well:

| Model                        | Test RMSE (with GridSearch)| Test RMSE (Base)   | Absolute Error   |
| ---------------------------- |:--------------------------:|:------------------:| -----------------|
| Random Forest Regressor      | 9.487118217587387          | 9.547566374653456  | 7.317760953625915|
| Support Vector Machine       | 9.857068901488233          | 9.516711070354274  | 7.132888084897704|
| PyCaret                      | -                          | 9.815711126761942  | 7.570090718963135|
