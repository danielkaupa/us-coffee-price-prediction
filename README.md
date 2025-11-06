# U.S. Coffee Price Prediction

This repository contains the code and analysis from the project “U.S. Coffee Production”, originally completed in 2020 at Concordia College. The goal of this project was to investigate patterns in U.S. coffee production and pricing, and to develop predictive models for U.S. coffee prices using prices from other fruit and tree-nut crops with potentially similar climate requirements.

Although the United States is one of the largest consumers of coffee in the world, it produces only a small fraction of the coffee it consumes. This project explores how coffee prices in the U.S. have changed since the late 1960s, and how closely those changes relate to the prices of other agricultural commodities such as apples, cranberries, cherries, grapefruit, and tangerines.

<br>

## Project Objectives

* Explore and clean U.S. agricultural commodity price data.
* Compare coffee prices with prices of other fruits and nuts to identify meaningful correlations.
* Develop predictive models to estimate coffee prices based on these related commodities.
* Evaluate modeling approaches including:
  * k-Nearest Neighbor (KNN) Regression
  * Linear Regression
  * Decision Trees
  * Random Forests

<br>

## Data Sources

All data was obtained from the United States Department of Agriculture (USDA) National Agricultural Statistics Service (NASS) QuickStats [database](https://quickstats.nass.usda.gov/)

For this project, commodity price data was selected at the national (U.S. total) level and filtered to include consistent annual records from 1967 to 2017.

<br>

## Key Findings

Several fruit prices are moderately correlated with coffee price, the strongest being Apples, Cranberries and Grapefruits
Despite these crops being primarily grown in different climates, they still exhibited meaningful price correlation with coffee.

Of all tested models, the Decision Tree model using the five most correlated predictors performed the best.

| Model Type	| Best R² (Test Data) |
| ------------ | ------------------- |
| Linear Regression | 	~0.60  |
| KNN Regression | 	~0.67  |
| Random Forest | 	~0.73  |
| Decision Tree (Best Model) | ~0.79 |

**Final Selected Model:** TREEModeltrim5
This model achieved the highest predictive performance (R² ≈ 0.79) and offered interpretable variable splits.

<br>

## Repository Contents
```
.us-coffee-price-prediction
    ├── additional_information/      # includes written report
    │
    ├── data/      # includes 'USDA_Data.csv' - raw price dataset downloaded from USDA NASS
    │
    ├── images/    # includes primary graphics from written report, model graphs, correlation analysis
    │
    ├── coffee_production_analysis.Rmd	      # Main analysis file (R Markdown) with data cleaning, visualization, and modeling.
    │
    └── README.md       # you are here

```

<br>

## How to Run the Analysis
1. Install R (≥ 3.6) and RStudio (recommended)
2. Install required packages
  * install.packages(c("tidyverse", "caret", "tree", "randomForest", "car", "visdat", "naniar"))
3. Open the .Rmd file in RStudio
4. Set your working directory
  * setwd("path/to/repository")
5. Run notebook
  * Either:
    * Click Run All, or
    * Knit to HTML → Generate full report.

<br>

### Example Visualization

**Coffee price trend in the U.S., 1967–2017:**

```
ggplot(base_dataNUM, aes(x = Year, y = `COFFEE - PRICE RECEIVED, MEASURED IN $ / LB`)) +
  geom_point() +
  geom_smooth(se = FALSE) +
  labs(title = "Price Received for U.S. Coffee Over Time")
```

<br>

## Future Improvements

* Incorporate climate and weather variables affecting coffee growth.
* Examine import vs domestic production dynamics.
* Include additional crops to broaden the predictor set.
* Explore advanced non-linear models (e.g., boosted trees, spline regression, or neural networks).

<br>

## References

USDA NASS QuickStats, Coffee & Health Foundation, Statista, WorldAtlas, and secondary literature on global coffee consumption and trade.
Full bibliography is included in the original report.
