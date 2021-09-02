# Predicting Pet Insurance Claims - Data Wrangling

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

