D
SpaceX Falcon 9 First Stage Landing Prediction

Capstone project for the IBM Data Science Professional Certificate. The goal is to predict whether the first stage of a Falcon 9 rocket will land successfully after launch.

Why this matters

SpaceX can offer Falcon 9 launches at a fraction of competitors' prices largely because it recovers and reuses the first stage. A recovered booster and a lost one are very different costs, so being able to predict landing success is effectively a way to estimate the real cost of a launch. A competitor bidding against SpaceX would want exactly that estimate.

Data

Launch records were gathered by scraping two public sources:

A third-party site that tracks SpaceX launch statistics
Wikipedia's Falcon 9 launch tables

The scraped pages were parsed into structured records and combined into a single dataset covering launch date, launch site, payload mass, orbit, booster version, and landing outcome.

Approach

Data collection and wrangling. Scraped and parsed the source pages, normalized inconsistent fields across the two sources, handled missing values, and engineered the binary landing-outcome variable used as the prediction target.

Exploratory analysis. Examined the cleaned data with Python and SQL to see how payload mass, orbit type, booster version, launch site, and flight number relate to landing success, and how the success rate has changed over time.

Visualization and dashboard. Built an interactive dashboard so the data can be explored directly rather than only through static charts, with filtering by launch site and payload range.

Modeling. Trained and evaluated several classification models on the prepared dataset, tuning hyperparameters and comparing performance on held-out data to select the strongest performer.

Results
As time has increased both the ratio of successful missions, and the variety of missions that Space X takes part in has increased.
Due to the lack of data points their is not enough data for the different prediction methods to have many differences.
Tools

Python (pandas, NumPy, Matplotlib, scikit-learn), SQL, Jupyter Notebook, BeautifulSoup

Running the project
bash
git clone https://github.com/Taylor-jat/IBM-data-scientist-capstone.git
cd IBM-data-scientist-capstone

Open the notebooks in Jupyter to follow the analysis in order, or run the dashboard application to explore the data interactively.
