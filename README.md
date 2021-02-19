# Job Prediction Model 
## A Case Study Using 2012 OKCupid Dating Profile Information 
Authors: [Jiji Craynock](https://github.com/DataOnATangent)

<p><img src="/images/banner.png" alt="Header"></p>

## Overview
The US is known as the melting pot of the world a fact that demonstrates pride in diversity. Nevertheless, those of us who live here are aware that in many spaces the lack of variety in background is something that seems to occur quite often. In this case study, I test several categorical models in order to determine whether an individual can be properly classified as working in the computer/tech space by features by demographic information.   In order to do this, I have used the okcupid dataset (available on kaggle and linked below) and focus on the following questions:

<p align="center"><img width="150" height="100" src="/images/okc_logo.png" alt="okc_logo"></p>

* How do physical attributes such as body type, age, and height affect the likelihood of a person working in the tech space?
* How do cultural attributes such as religion, ethnicity, and language affect the likelihood of a person working in the tech space?  
* How do lifestyle attributes such as diet, smoking, and pets affect this likelihood? 

## Approach

### Data and model preparation in 3 major steps:

1. **Cleaning and Preprocessing:** Handeled all missing information, dropped unneeded/unusable columns, simplified categorical features by grouping similar groups together and removing attitudes from responses. The notebook containing this process with explanations on how each feature was treated can be found in the data_exploration folder. 

2. **Exploratory Data Analysis:** Features were manipulated and used to create a myriad of visuals in order to better understand the distribution of the observations and possible relationships.

3. **Modeling:** Tested several classification models to find the best option for the dataset. 

### Models tested:

* Logistic Regression
* KNN
* Decision Tree 
* Random Forests 
* AdaBoost
* Gradient Boosting
* XG Boosting


## Findings

During the preprocessing stage it became immediately clear that this data would contain high variance. A fact that is expected given that the observations are real people and the sorce was dating profiles. This lead to a lengthy cleaning process in order to pair down features in the hopes of reducing the noise in the data. In the end, I still had many features to work with as seen in the correlation chart.  

<p align="center"><img width="300" height="300" src="/images/corr.png" alt="okc_logo"></p>



This case study is speculative in nature, and so we use accuracy as our metric to evaluate the success of each model. Simply put, we use the accuracy score here because there is no particularly heavy risk associated with either Type I or Type II errors.

The null accuracy, which is a baseline metric used to evaluate the final model, is 71%. Our best model uses scikit-learn Random Forests, which produced an **82% accuracy**. We can therefore say that using Random Forests provides significant predicting power for the data.

Several straight forward features helped the model such as occupation, weekly hours worked, age, education, and work industry.

More notably, using sklearn's GridSearch, additional valuable features were identified: 

* Place of birth
* Sex
* Couple status (married v. unmarried and same-sex partner vs opposite-sex partner)
* Whether or not a person has given birth in the last 12 months.

 
<p><img src="./images/important_features.png" alt="Features"></p>

## Conclusion



## Next Steps

Next we recommend to take a look into individual states. We saw in our final model that an person's place of birth is a strong indicator of income. (Birth place in this data set is coded by state and also by country if outside of the US.) Place of birth is likely a strong indicator of where an individual currently lives as well. Access to more drilled-down information should prove inciteful. 

There are also a few variables not included which may provide further insight such as features indicating disability, number of dependants, and zipcode.

Lastly, the target variable for this particular model is income which includes a myriad of revenue. According to census.gov, "income" includes: 

"income received from wages, salary, commissions, bonuses, and tips; self-employment income from own nonfarm or farm businesses, including proprietorships and partnerships; interest, dividends, net rental income, royalty income, or income from estates and trusts; Social Security or Railroad Retirement income; Supplemental Security Income (SSI); any cash public assistance or welfare payments from the state or local welfare office; retirement, survivor, or disability benefits; and any other sources of income received regularly such as Veterans' (VA) payments, unemployment and/or worker’s compensation, child support, and alimony."

It may be relevant to compare income with salary, which is defined simply as compensation of employees from an employer (and not including tax or retirement witholdings). Looking into salary may yield different, and perhaps more precise, results as it would not include as many variables.


## Repository Structure
    
    ├── data_exploration                  Preprocsing Notebook, EDA Notebooks, and Relevan Data
    ├── model_tests                       Original and resampled model testing noteboks    
    ├── final_notebook                    Final notebook containing final model
    ├── images                            Images
    ├── README.md                         ReadMe
    └── presentation_deck                 Contains the presentation deck associated with this project