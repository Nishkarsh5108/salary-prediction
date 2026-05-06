#### dataset:

[Job Salary Prediction | Kaggle](https://www.kaggle.com/competitions/job-salary-prediction/data)


#### target encode:(encode them)

1. Location
2. Company
3. catagory
4. SourceName

* on the basis of the SalaryNormalised of training data
* if a new field is found we will just use global mean of training data
  eg: if we get a new SourceName, we will use a Training data mean of SalaryNormalised in the SourceName's encoded version, same for new location catagory Company
* instead of global mean we can use the bigger reagion rule for mean
  like for example if the traiing data didnt have haggerston
  so instead of using the global mean, it should use the mean of all the places in East London

#### Dropping ID

#### one hot encoding:

ContractType
ContractTime

#### Embeddings

use DistilBERT on Title and FullDescription(concatinated on a same column) to generate a vector for the text
due to lack of resources FineTuning the BERT models is pretty wild, so we aint doing that shi

with these final we will make predictions using gradinet boosted trees

nvm raw emeddings are kinda shit.. we gonna do fine tuning.. but tameez se... laptop nahi jalana

used XGB(goated), L1 regression, L2 regression (both of them are shit), MLP (kinda cool), catboost(performed similar to XGB), lgbm(performed similar to XGB)

seeing boosted trees are cooking

i am going ot make an ensemble of the three types of trees as base learners and L2 regression as meta learner (as we would have 3 outputs from the base learners, L2 regression is kinda goated for that shi)

got goated scores (score in top 19 ranks, yayy): 18th rank MAE:5008, 19th Rank MAE: 5150 20th Rank MAE: 5154.85622

trying Tabnet (suggested by gemini)... that shit takes long, so gonna turn it up and go to sleep
