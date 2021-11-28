# Predicting Pet Insurance Claims

[![Python 3.8](https://img.shields.io/badge/python-3.8-blue.svg)](https://www.python.org/downloads/release/python-380/)
[![Maintenance](https://img.shields.io/badge/Maintained%3F-no-red.svg)](https://github.com/stevenrhart/predicting-claims/graphs/commit-activity)
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)

**[Executive Summary](#exec-summary)** | **[Datasets](#data)** | **[Wrangling](#wrangling)** | **[EDA](#eda)** | **[Results](#results)** | **[Future](#future)**

See the [presentation](https://github.com/stevenrhart/predicting-claims/blob/main/report/Predicting%20Pet%20Insurance%20Claims.pdf)

See the [complete report](https://github.com/stevenrhart/predicting-claims/blob/main/report/Predicting%20Pet%20Insurance%20Claims%20Final%20Report.pdf)


## EXECUTIVE SUMMARY <a id='overview'></a>

In 2020, the global pet insurance market is estimated to exceed 4 billion dollars [1](https://www.grandviewresearch.com/industry-analysis/pet-insurance-market). And in the US alone, the market value is anticipated to be close to half this total amount ($1.6 Billion USD) with sustained year-over-year growth of nearly 15% for the foreseeable future [2](https://www.ibisworld.com/industry-statistics/market-size/pet-insurance-united-states/). With so much potential revenue at stake, the need for competitive policy pricing is as important as ever.

The idea behind pet insurance is simple and similar to the human health insurance market. When a pet insurance policy holder incurs veterinary expenses related to their enrolled pet, they can submit claims for reimbursement, and the insurance company reimburses eligible expenses. Given the stochastic nature of claims submissions however, policy pricing remains a challenge. 

To price insurance products correctly, the insurance company needs to have a good idea of the amount their policy holders are likely to claim in future policy years. The goal of this project is to create a machine learning model to predict how much (in dollars) a given policy holder will claim for during their second policy year based on pet information and claims data from their first policy year. After evaluating a range of models, the best performing model resulted in claims predictions that were $400 more accurate than predictions made using a simple baseline model.   


## DATASETS <a id ='data'></a>

The underlying source data for the project consists of two files - `PetData.csv` and `ClaimData.csv` obtained from a national pet insurance provider. The PetData file contains data for 50000 unique pets who enrolled for policies during the 2018 calendar year. The pet data includes 8 features which provide information about the type of pet (e.g., species, breed, age) and the cost of the policy (i.e., premium and deductible). The claim data includes 4 features detailing insurance claims recorded over a 3-year period between 2018 and 2020 providing the claim date and amount. The two datasets are linked by a common feature, PetId, which can be used to understand the claims totals for each individual pet. prediction.


## DATA WRANGLING <a id ='wrangling'></a>

Overall, the two datasets were relatively clean and the bulk of the data wrangling process consisted of data verification and determining how best to combine the pets data with the associated claims data. A few columns required some additional manipulation in preparation for exploratory data analysis. 
    
### Key Observations:
* **Pet Count** - Verified 50,000 unique pets (based on PetIds)
* **Species** - Data consists of two species of pets, cats and dogs (with dogs outnumbering cats 5 to 1)
* **Breed** - Observed 373 unique breeds in total (55 cat and 318 dog) 
* **Age** - Pet ages range between 0 (i.e., < 1 year) and 13 
* **Premium** - Premiums fall into a wide range with a few outlier values close to $1000 
* **Deductible** - Deductibles are fairly well distributed and appear to be stratified across a range of common values 
* **Median Claims** - For cats and dogs, the median value for total number and total amount of claims is 0 
* **Outlier Claims** - Both species have some significant outliers in both categories (number and amount of claims)


## EDA <a id ='eda'></a>

During exploratory data analysis, a number of observations stood out in relation to overall claims totals. In general, dog owners have more claims and higher total claims amounts than cat owners. As expected, this tends to translate to higher premiums. 

#### Dogs tend to have more claims and higher claims totals on average

<img src="https://github.com/stevenrhart/predicting-claims/blob/main/figures/Total-Claims-by-Species-cropped.png" />

#### And as a result, dogs tend to have higher premiums

<img src="https://github.com/stevenrhart/predicting-claims/blob/main/figures/Premium-by-Species-cropped.png" />

Looking at the data from the perspective of pet breeds, we see that as the average number of claims for a breed goes up, the average total claims amount goes up in almost a linear fashion. That said, one limitation of the data is that there is a significant imbalance in terms of the number of pets per breed. Generally, as the number of pets in a breed increases, the variability in claims (number and amount) goes down, moving the breed closer to the overall linear trend line.

And... unsurprisingly, cat breeds tend to occupy the lower left quadrant of the plot indicating fewer claims and lower total claims on average when compared to dogs.

#### We see a linear trend in average number and amount of claims by species as the number of pets increases 

<img src="https://github.com/stevenrhart/predicting-claims/blob/main/figures/Avg-Claims-by-Species-cropped.png" />


## PREDICTIVE MODELING RESULTS <a id='results'></a>

In this project, we evaluated data for 50,000 pet insurance customers with a goal of building a model to predict the total claims amount in the second policy year based on basic info about the pet (breed, age, species, etc.) and claims data (number of claims, amount of each claim, etc.) for the first policy year. We evaluated a variety of different models (listed below) and in the end, found the best performance using a Gradient Boosting Regressor with some parameter tuning. 

Using our best model on our test data, we achieved a mean absolute error of ~638, well inline with our cross-validation scores from model tuning. While still somewhat high, this is down from ~1020 using our baseline model of a simple dummy regressor. This represents an improved accuracy of nearly \$400 per customer. When considered in the context of a customer base of 65-75 million, these results are significant and could lead to substantial savings for the business in terms of improved pricing and risk models.

**Model Evaluation Results:**

| Regressor | Notes | Score |
| :- | :- | -: |
| Dummy Regressor | Using the mean | 1020.41|
| Simple Linear Regressor | | 930.46 |
| Linear Regressor | w/ feature selection | 930.40 |
| Simple Lasso Regressor | | 930.28 |
| Lasso Regressor | simple tuning | 930.18 |
| Gradient Boosting Regressor | | 932.25 |
| Gradient Boosting | n_iter & learning_rate tuning | 931.92 |
| Gradient Boosting | loss & alpha tuning | 677.75 |
| Gradient Boosting | tree-specific tuning | 673.82 |

**Results with Test Data:**

| Regressor | Notes | Score |
| :- | :- | -: |
| Gradient Boosting | best estimator | 638.64 |


## FUTURE RESEARCH <a id = 'future'></a>

Although we observed a dramatic improvement in model performance using a gradient boosting regressor, our mean absolute error still leaves quite a bit of room for improvement. 

The following are recommendations for potential next steps to refine or further expand upon the work done in this project:

* **Obtain a more balanced dataset** - The dataset for this project is highly imbalanced across a number of features (species, breed, age, etc.). While this imbalance likely reflects the population of pets, it presents challenges when building a model that predicts the claims amount for a specific pet. By starting with a more balanced dataset, it's possible the predictive accuracy could be improved overall.
* **Engineer additional features** - Feature engineering in this project was largely focused on relating pet age and breed to claims data. It's possible that additional feature engineering could be done to improve model performance. Suggestions include:
    * **Timing of Claims** As part of data wrangling, we rolled up our claims data into totals and averages per pet. But it stands to reason that the timing of when claims are submitted could be a powerful predictor of claims amounts in the second policy year. For example, a pet with \$10,000 in claims in the first 3 months of year 1 may be less likely to have claims in year 2 when compared with a pet having an equal amount of claims in the last month of year 1. 
    * **Additional Breed Data** It is widely known that different pet breeds have different characteristics, but our limited dataset did not include any data specific to each breed. By including additional breed specific data in our analysis, it may be possible to engineer meaningful features to improve the predictive power of our model. Examples of this could be including an average weight or average lifespan per breed or engineering a feature that calculates the 'risk index' for a pet given their age, breed and species. 