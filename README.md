# Job Prediction Model 
## A Case Study Using 2012 OKCupid Dating Profile Information 
Authors: [Jiji Craynock](https://github.com/DataOnATangent)

<p><img src="/images/banner.png" alt="Header"></p>

## Overview
The US is known as the melting pot of the world a fact that demonstrates pride in diversity. Nevertheless, those of us who live here are aware that in many spaces the lack of variety in background is something that seems to occur quite often. In this case study, I test several categorical models in order to determine whether an individual can be properly classified as working in the computer/tech space by features by demographic information.   In order to do this, I have used the okcupid dataset (available on kaggle and linked below) and focus on the following questions:

<p align="center"><img width="240" height="200" src="/images/okc_logo.png" alt="okc_logo"></p>

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

<p align="center"><img width="400" height="300" src="/images/Corr.png" alt="correlation_chart"></p>


Once the features had been peen put into charts individually, I was able to see that many features including had major imbalances. These imbalances were even more apperant when grouped compared specifically to those that do and do not work in the tech sphere.  

<p align="center">
    <img width="200" height="150" src="/images/Dist_gen.png" alt="gender_chart">
    <img width="200" height="150" src="/images/Dist_body.png" alt="body_chart">
    <img width="200" height="150" src="/images/Dist_ethn.png" alt="ethn_chart">
</p>

That being said, the differences between the general sample and tech workers was still highly relative due to the class imbalance between the positive and negative class. Something that is a bit easier to see when looking at parallel plots

<p align="center">
    <img width="200" height="150" src="/images/p_sex_ethn.png" alt="gender_chart">
    <img width="200" height="150" src="/images/p_bod_ori.png" alt="body_chart">
    <img width="200" height="150" src="/images/p_sm_dri_drug.png" alt="smo_chart">
</p>


When moving on to models the complicated nature of the data once again became evident. Despite trying multiple types of models, all of them had a tendency to overfit. In the case of all the ensemble methods I attempted, all of them were very unstable with metric results varying dramatically from prediction to prediction. This ultimately lead me to choosing logistic regression for my final model. 

 
<p align="center"><img width="400" height="300" src="/images/roc.png" alt="roc_chart"></p> 

This model ultimately produced the best results for my data, though notable also overfit. This despite two rounds of feature selection and gridsearch to optimize my parameters. This leads me to believe that in order to perfect this predictor additional work and possibly outside data would be needed to move forward with the overall goal of being able to classify observations by these kinds of features. 

## Conclusion

This project took many twist and terms and ultimately my model did not perform as well as I may have like but I do think there are reasons for that beyond the model. The fact that the model had trouble predicting is a good thing. It means my target is varied enough to not be easily distinguished which leads me to think that the population of people who work in tech, is in fact, quite diverse. Though further testing would be needed to prove this theory.

## Next Steps

In order to take this project to the next level, I believe there are a number of things that could be done. Among the first steps would be to re-integrate many of the attitudes and more specific categories that were simplified early on in this project. Next, I think using data from a non-dating site would perhaps also give a clearer picture since it is hard to say if this sample is truly representative of the whole give where the data was sourced from. 

## Repository Structure
    
    ├── data_exploration                  Preprocsing Notebook, EDA Notebooks, and Relevan Data
    ├── model_tests                       Original and resampled model testing noteboks    
    ├── final_notebook                    Final notebook containing final model
    ├── images                            Images
    ├── README.md                         ReadMe
    └── presentation_deck                 Contains the presentation deck associated with this project