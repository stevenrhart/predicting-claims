# Predicting Pet Insurance Claims in the Second Policy Year

[![Python 3.8](https://img.shields.io/badge/python-3.8-blue.svg)](https://www.python.org/downloads/release/python-380/)
[![Maintenance](https://img.shields.io/badge/Maintained%3F-no-red.svg)](https://github.com/stevenrhart/predicting-claims/graphs/commit-activity)
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)

# Update ToC**
**[Executive Summary](#exec-summary)** | **[Datasets](#data)** | **[Wrangling](#wrangling)** | **[EDA](#eda)** | **[Modeling](#model)** | **[Results](#results)** | **[Future](#future)**

See the [presentation](#insert link to presentation)

See the [complete report](#insert link to report)


## EXECUTIVE SUMMARY <a id='overview'></a>

<p align="justify">Insert background paragraph on pet insurance industry </p>

<p align="justify">When a pet insurance policy holder incurs veterinary expenses related to their enrolled pet, they can submit claims for reimbursement, and the insurance company reimburses eligible expenses. To price insurance products correctly, the insurance company needs to have a good idea of the amount their policy holders are likely to claim in future policy years. The goal of this project is to create a machine learning model to predict how much (in dollars) a given policy holder will claim for during their second policy year based on pet information and claims data from their first policy year. </p>

<p align="justify">Insert paragraph on summary results </p>


## DATASETS <a id ='data'></a>

<p align = 'justify'>The underlying source data for the project consists of two files - `PetData.csv` and `ClaimData.csv`. The former contains enrollment and premium data for 50000 pets that enrolled for insurance during the 2018 calendar year, and the latter contains the dates and dollar amounts of the associated claims for these pets between 2018 and 2021. </p>

<p align = 'justify'><strong>PetData.csv contains the following columns:</strong>
<ul>
    <li>PetId - a unique number that identifies enrolled pets </li>
    <li>EnrollDate - the date of customer enrollment </li>
    <li>Species - species of pet, dog or cat </li>
    <li>Breed - breed of pet </li>
    <li>PetAge - the age of the pet at enrollment (not necessarily the current age of the pet) </li>
    <li>Premium - the monthly premium (in USD) of the pet’s insurance policy </li>
    <li>Deductible - the deductible (in USD) of the pet’s insurance policy </li>
    <li>EnrollPath - indicates whether the member enrolled via company website or over the phone </li> 
</ul>
</p>

<p align = 'justify'><strong>ClaimsData.csv contains the following columns:</strong>
<ul>
    <li>PetId - a unique number that identifies enrolled pets </li>
    <li>ClaimId - a unique number that identifies individual claims made by our members </li>
    <li>ClaimDate - date of claim </li>
    <li>AmountClaimed - amount of claim </li>
</ul>
</p>


## DATA WRANGLING <a id ='wrangling'></a>

<p align = 'justify'>Overall, the two datasets were relatively clean and the bulk of the data wrangling process consisted of verifying the data and determining how to combine the pets data with the associated claims data in preparation for exploratory data analysis. </p>
    
<p align = 'justify'>**Key Observations:**
* Number of Unique Pets - Verified 50,000 unique pets (based on PetId) with an even spread of enroll dates throughout the 2018 calendar year
* 
* EnrollDate - Confirmed a reasonable spread of enroll dates over the period included in the dataset
Species - Observed that the data includes only two species, Cats and Dogs (with dogs greatly outnumbering cats more than 5 to 1)
Breed - Reviewed entries for Breed and made the following observations/updates:
Cleaned up some of the "Mixed Breed" entries for dogs to remove weight ranges while retaining the size category for each
Grouped Labrador Retriever breeds, removing the color designation completely
Removed special characters and extra whitespace from all other breed names (cats and dogs)
Added a new column to designate whether an animal is mixed breed or not
PetAge - Created a new column to capture a pet's age in years at the time of enrollment and a second column to designate pets that were very young when enrolled (< 7 weeks old)
Premium - Identified a handful of outlier premiums worthy of a more thorough review in EDA
Deductible - Verified that the distribution of deductible amounts seems reasonable

Claims data:
PetId - Removed claims data for PetIds not included in our pets dataset (ids > 49999)
ClaimId - Dropped the ClaimId column as no duplicates or missing values were discovered and it seemed to be of low value for our analysis
ClaimDate - Observed and removed claims with dates prior to a pet's enrollment or beyond the 2-year window of our analysis
AmountClaimed:
Removed negative value claims and made note of outlier claims amounts for further review in EDA
Created new columns to summarize claims data by PetId including number of claims in each year, average claim amount in each year and total claim amount in each year

Merged the pets and claims data into a new dataframe

</p>


## EDA <a id ='eda'></a>

<p align = 'justify'>TBD </p>


## PREDICTIVE MODELING <a id ='model'></a>

<p align = 'justify'>TBD </p>


## RESULTS <a id='results'></a>

<p align = 'justify'> TBD </p>


## FUTURE RESEARCH <a id = 'future'></a>

- <p align = 'justify'>TBD</p>