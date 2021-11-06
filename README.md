# Predicting Pet Insurance Claims in the Second Policy Year

[![Python 3.8](https://img.shields.io/badge/python-3.8-blue.svg)](https://www.python.org/downloads/release/python-380/)
[![Maintenance](https://img.shields.io/badge/Maintained%3F-no-red.svg)](https://github.com/stevenrhart/predicting-claims/graphs/commit-activity)
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)

**[Executive Summary](#exec-summary)** | **[Datasets](#data)** | **[Wrangling](#wrangling)** | **[EDA](#eda)** | **[Modeling](#model)** | **[Results](#results)** | **[Future](#future)**

See the [presentation](#insert link to presentation)

See the [complete report](#insert link to report)


## EXECUTIVE SUMMARY <a id='overview'></a>

Insert background paragraph on pet insurance industry (and picture?)

When a pet insurance policy holder incurs veterinary expenses related to their enrolled pet, they can submit claims for reimbursement, and the insurance company reimburses eligible expenses. To price insurance products correctly, the insurance company needs to have a good idea of the amount their policy holders are likely to claim in future policy years. The goal of this project is to create a machine learning model to predict how much (in dollars) a given policy holder will claim for during their second policy year based on pet information and claims data from their first policy year. 

Insert paragraph on summary results


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
* **Outlier Claims** - On the flip side, both species have some significant outliers in both categories (number and amount of claims)


## EDA <a id ='eda'></a>

During exploratory data analysis, 

#### Dogs tend to have more claims and higher claims totals on average

<img src="https://github.com/stevenrhart/predicting-claims/blob/main/figures/Total-Claims-by-Species.png" />

#### And as a result, dogs tend to have higher premiums

<img src="https://github.com/stevenrhart/predicting-claims/blob/main/figures/Premium-by-Species.png" />

**Breed**
* As the average number of claims for a breed goes up, the average total claims amount goes up in a linear fashion
* As the number of pets in a breed increases, the variability in claims (number and amount) goes down, moving the breed closer to the linear trend line
* Breed matters when it comes to total claims amounts and we'll need to determine how to handle this categorical feature given the large number of unique values

**Correlation**
* Generally, we have weak to no correlation between our features and our target variable (AmtClaimsYr2)


## PREDICTIVE MODELING <a id ='model'></a>

<p align = 'justify'>TBD </p>


## RESULTS <a id='results'></a>

<p align = 'justify'> TBD </p>


## FUTURE RESEARCH <a id = 'future'></a>

- <p align = 'justify'>TBD</p>