SpaceX Falcon 9 First Stage Landing Prediction

Capstone project for the IBM Data Science Professional Certificate. The goal is to predict whether the first stage of a Falcon 9 rocket will land successfully after launch.

Why this matters

SpaceX can offer Falcon 9 launches at a fraction of competitors' prices largely because it recovers and reuses the first stage. A recovered booster and an expended one are very different costs, so predicting landing success is effectively a way to estimate the true cost of a launch. A company bidding against SpaceX would want exactly that estimate.

Data

Launch records were assembled from two sources:

Wikipedia, scraped with requests and BeautifulSoup from the List of Falcon 9 and Falcon Heavy launches tables, then parsed into structured records
Course-provided launch datasets hosted as CSV, used for the wrangling, SQL, and modeling stages

Fields include launch site, payload mass, orbit type, booster version, flight number, and landing outcome. After wrangling, the modeling dataset covers 90 launches.

Approach

Web scraping (jupyter-labs-webscraping.ipynb) Extracted Falcon 9 launch tables from Wikipedia, handling the irregular HTML of the source tables and normalizing the results into a dataframe.

Data wrangling (labs-jupyter-spacex-Data wrangling.ipynb) Cleaned and standardized the data with pandas and NumPy, examined launch-site and orbit distributions, and engineered the binary landing-outcome variable used as the prediction target.

SQL exploratory analysis (jupyter-labs-eda-sql-coursera_sqllite.ipynb) Loaded the dataset into SQLite and queried it directly to profile launch sites, payload ranges by booster version, mission outcomes, and landing results over time.

Visual exploratory analysis (edadataviz.ipynb) Used Matplotlib and Seaborn to examine how flight number, payload mass, launch site, and orbit type relate to landing success, and how the yearly success rate has trended.

Geospatial analysis (lab_jupyter_launch_site_location.ipynb) Built interactive Folium maps to plot launch sites and their proximity to coastlines, railways, highways, and nearby cities, examining whether site placement relates to outcomes.

Interactive dashboard (spacex-dash-app.py) A Plotly Dash application with a launch-site dropdown and a payload-range slider, rendering a pie chart of success counts and a scatter plot of payload mass against landing outcome by booster version, so the data can be explored rather than just read.

Predictive modeling (SpaceX_Machine Learning Prediction_Part_5.ipynb) Standardized the features, split the data 80/20, and trained four classifiers with GridSearchCV hyperparameter tuning at 10-fold cross-validation: logistic regression, support vector machine, decision tree, and k-nearest neighbors.

Results
Model	Best CV accuracy	Test accuracy
Decision Tree	0.889	0.833
Support Vector Machine	0.848	0.833
K-Nearest Neighbors	0.848	0.833
Logistic Regression	0.846	0.833

The decision tree achieved the strongest cross-validation score at 88.9%. All four models scored identically on the held-out test set at 83.3%, which is a caution rather than a result: the test set is only 18 launches, so a single reclassified launch moves accuracy by more than five points. With a sample this small, the cross-validation scores are the more trustworthy comparison, and the honest conclusion is that these models are close to indistinguishable on this data.

The exploratory analysis was more informative than the accuracy figures. Landing success improves markedly with flight number, consistent with SpaceX learning across the program, and success rates vary meaningfully by orbit type and launch site.

Repository contents
File	Description
jupyter-labs-webscraping.ipynb	Scraping and parsing Wikipedia launch tables
labs-jupyter-spacex-Data wrangling.ipynb	Cleaning, normalization, target variable creation
jupyter-labs-eda-sql-coursera_sqllite.ipynb	Exploratory analysis in SQL via SQLite
edadataviz.ipynb	Exploratory analysis and visualization
lab_jupyter_launch_site_location.ipynb	Folium geospatial analysis of launch sites
spacex-dash-app.py	Plotly Dash interactive dashboard
SpaceX_Machine Learning Prediction_Part_5.ipynb	Model training, tuning, and evaluation
Data Science Capstone Project Report..pdf	Final written report
Tools

Python (pandas, NumPy, Matplotlib, Seaborn, scikit-learn, BeautifulSoup, Folium, Plotly Dash), SQL (SQLite), Jupyter Notebook

Running the dashboard
bash
git clone https://github.com/Taylor-jat/IBM-data-scientist-capstone.git
cd IBM-data-scientist-capstone
pip install pandas dash plotly
python spacex-dash-app.py

Then open http://127.0.0.1:8050 in a browser. The notebooks can be opened in Jupyter and run in the order listed above.
