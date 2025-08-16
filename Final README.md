### Box Office Trends and Genre Performance: Can We Predict Future Success?

Cindy Kohlleppel

#### Executive summary
This project explores whether we can predict the financial performance of different movie genres using data on budgets, revenues, and audience ratings. Using a dataset of movies released up to July 2017, I conducted exploratory data analysis (EDA) and built baseline regression models. The analysis shows that while certain genres—particularly Action, Adventure, and Animation—consistently outperform others in revenue, budget is an even stronger predictor of success. Models achieved moderate predictive power (CV R² ≈ 0.59, Validation R² ≈ 0.49), suggesting we can identify broad trends but not precisely forecast individual movie outcomes.

#### Rationale
Movie production typically involves substantial financial risk, and studios often rely on past trends to guide investment decisions. Understanding which genres historically generate higher revenues can help inform these decisions, while identifying the limits of prediction highlights the unpredictability of the industry. By analyzing past performance, this project aims to shed light on whether genre-based predictions can provide meaningful guidance for future films.

#### Research Question
Can we predict the performance of certain movie genres in the future based on performance via ratings and box office $$ of currently released movies?

#### Data Sources
The Movies Dataset: https://www.kaggle.com/datasets/rounakbanik/the-movies-dataset/data?select=movies_metadata.csv
  - The dataset consists of movies released on or before July 2017. 

  - Metadata on 45,000+ movies including budget, revenue, release dates, languages, production details, and genres

  - Includes additional files for cast/crew, plot keywords, ratings, etc.

  - Provides a much larger and richer dataset compared to our earlier merged sources

  - Enables stronger exploratory analysis and more reliable baseline modeling

#### Methodology
The project followed a CRISP-DM approach, beginning with data cleaning and exploratory data analysis (EDA). I combined metadata (genres, budget, revenue, ratings, keywords) into a working dataset and engineered features such as primary genre indicators. I also used various visualization techniques to examine trends in revenue and profitability across genres, budgets, and ratings.

For modeling, I applied several baseline regression models (Linear Regression, Ridge, Lasso, Decision Tree, Random Forest, and Gradient Boosting). Model performance was evaluated using cross-validation (CV R²) and a hold-out validation set (Validation R², RMSE, MAE). This approach allowed me to assess whether genre, alongside other features, could reliably predict future box office performance.

#### Results
The analysis reveals that Action, Adventure, and Animation are the strongest financial performers, frequently appearing among the top revenue-generating films. Budget has a strong positive correlation with revenue, meaning that higher spending generally leads to higher box office returns, though some lower-budget films achieve breakout success. Ratings provide additional insight but are less directly tied to revenue. Overall, genre matters, but budget level remains a stronger predictor. The models suggest we can generalize about which genres are most likely to succeed but cannot precisely predict future box office revenue.

#### Next Steps

**Expand or Update the Dataset**  
- Incorporate more recent box office and streaming data (e.g., post-2020 releases) to better capture shifts in audience demand and distribution channels.  
- Ensure dataset size remains large enough to preserve statistical power while improving the model’s relevance to today’s market & more recent releases.  

**Feature Engineering Enhancements**  
- Explore richer text-based features (e.g., plot summaries, keywords, director/actor information) to capture more of what drives audience engagement and incorporate that into drivers of financial success for movies.
- Break down budget into categories (marketing vs. production) if available, to test which component has more predictive power.  
- Refine genre features (multi-label encoding, interaction terms such as budget × genre).  

**Modeling Extensions**  
- Evaluate alternative ML approaches such as XGBoost, LightGBM, or Neural Networks to capture non-linear relationships more effectively than baseline models.  
- Consider classification framing (e.g., “hit vs. non-hit”) alongside regression to test model robustness across tasks.  
- Perform more systematic hyperparameter tuning (GridSearchCV or RandomizedSearchCV with cross-validation).  

**Evaluation & Interpretability**  
- Broaden the question a bit to understand *which* features most influence predicted revenue, rather than focusing on genre alone.
- Perform segmented analysis by release decade, budget tier (indie vs. blockbuster), or language/region.  

**Business Application**  
- Test the predictive model on “upcoming movies” datasets (pre-release info only) to simulate real-world decision-making and see if the prediction and actual real-life result matches upon release


#### Outline of project

- [Technical Report](https://github.com/cindy-py13/MLAICourse/blob/Capstone/Final_Capstone_Tech_Report.ipynb)
- [Kaggle - The Movies Dataset](https://www.kaggle.com/datasets/rounakbanik/the-movies-dataset/data?select=movies_metadata.csv)


##### Contact and Further Information
Email: cindylkohlleppel@icloud.com