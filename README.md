# Predicting Pet Insurance Claims

## 1 Introduction

### 1.1 Background
Whenever a pet insurance policy holder incurs veterinary expenses related to their enrolled pet, they can submit claims for reimbursement, and the insurance company reimburses eligible expenses. To price insurance products correctly, the insurance company needs to have a good idea of the amount their policy holders are likely to claim in the future. 

### 1.2 Project Goal
The goal of this project is to create a machine learning model to predict how much (in dollars) a given policy holder will claim for during the second year of their policy. 

### 1.3 Datasets
The file PetData.csv contains enrollment and premium data for 50000 pets that enrolled in 2018. ClaimData.csv contains the dates and dollar amounts of claim submissions of pets between 2018 and 2021. Claim data for the two years following enrollment is included for the 50000 pets referenced in PetData.csv. 

PetData.csv contains the following columns:
* `PetId` = a unique number that identifies enrolled pets
* `EnrollDate` = the date of customer enrollment
* `Species` = species of pet, dog or cat
* `Breed` = breed of pet
* `PetAge` = the age of the pet at enrollment (not necessarily the current age of the pet)
* `Premium` = the monthly premium (in USD) of the pet’s insurance policy
* `Deductible` = the deductible (in USD) of the pet’s insurance policy 
* `EnrollPath` = indicates whether the member enrolled via the Trupanion website or over the phone

ClaimsData.csv contains the following columns:
* `PetId` = a unique number that identifies enrolled pets
* `ClaimId` = a unique number that identifies individual claims made by our members
* `ClaimDate` = date of claim
* `AmountClaimed` = amount of claim

# Predicting Pet Insurance Claims in the Second Policy Year

[![Python 3.8](https://img.shields.io/badge/python-3.8-blue.svg)](https://www.python.org/downloads/release/python-380/)
[![Maintenance](https://img.shields.io/badge/Maintained%3F-no-red.svg)](https://github.com/stevenrhart/predicting-claims/graphs/commit-activity)
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)

# Update ToC**
**[Overview](#overview)** | **[Findings](#findings)** | **[Datasets](#data)** | **[Wrangling](#wrangling)** | **[EDA](#eda)** | **[Modeling](#model)** | **[Results](#results)** | **[Future](#future)**

See the [presentation](#insert link to presentation)

See the [complete report](#insert link to report)


## OVERVIEW <a id='overview'></a>

<p align="justify"> Whenever a pet insurance policy holder incurs veterinary expenses related to their enrolled pet, they can submit claims for reimbursement, and the insurance company reimburses eligible expenses. To price insurance products correctly, the insurance company needs to have a good idea of the amount their policy holders are likely to claim in future policy years. The goal of this project is to create a machine learning model to predict how much (in dollars) a given policy holder will claim for during the second year of their policy based on pet information and claims data from the first policy year. </p>


## KEY FINDINGS <a id = 'findings'></a>

<p align="justify">TBD </p>


## DATASETS <a id ='data'></a>

<p align = 'justify'> Two datasets... TBD</p>

- [Pet Data](# insert link to data file)
- [Claims Data](# insert link to data file)


## DATA WRANGLING <a id ='wrangling'></a>

<p align = 'justify'>TBD </p>


## EDA <a id ='eda'></a>

<p align = 'justify'>TBD </p>


## PREDICTIVE MODELING <a id ='model'></a>

<p align = 'justify'>TBD </p>


## RESULTS <a id='results'></a>

<p align = 'justify'> TBD </p>


## FUTURE RESEARCH <a id = 'future'></a>

- <p align = 'justify'>TBD</p>