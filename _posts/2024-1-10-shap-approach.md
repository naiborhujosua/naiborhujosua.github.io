---
layout: post
title: This 1 Explainable AI(XAI) package can solve your business problems
subtitle: a method to interpret your black box models
gh-repo: naiborhujosua/Blog_Notes
gh-badge: [star, fork, follow]
cover-img: /assets/img/thumb.JPG
thumbnail-img: /assets/img/shap.JPG  
share-img: /assets/img/shap.JPG
tags: [shap,method,xai]
comments: true
mathjax: true
author: Jos Labs
---


Developing machine learning applications need a lot of steps. Gathering the data, doing data cleaning, exploring the data through exploratory data analysis, feature engineering, feature selection, modeling, evaluation, and interpretation. Interpretation is one of the crucial parts of developing a machine learning application. This process needs a lot of attention due to the business process. The machine learning engineer needs to explain how the machine learning model makes a particular prediction on the data to the non-technical experts/stakeholders.

Imagine if you are using a neural network model with complex features for developing your machine learning application, Will the non-technical experts trust your model prediction? Absolutely no. It is going to be a big problem for the technical experts and the stakeholders to accelerate the business processes using machine learning due to misinterpretation of the models. Thus, the ability to interpret the model is essential knowledge to know for making non-technical experts to trust our machine learning model when making a specific prediction on the data.

Shap (Shapley Additive exPlanations) is one of the most of Explainable Artificial Intelligence(XAI) tools to interpret why machine learning models make a specific prediction on the data instances. Shapley Additive exPlanations uses shap value in order to explain the prediction made by machine learning model. Shap value is based on the game theory approach to making a prediction.

Imagine you are participating in a machine learning hackathon with your team that consists of 4 members. Everyone has their own unique abilities in order to approach the problem given in the hackathon. If your team wins the hackathon, how do you decide on the fair payout for the particular member of the contribution given by a particular member.

It is definitely wise to divide a distinct portion of the payout for a particular member. That is the same with how shap interpret our model based on the data we train on the machine learning model. Mathematically speaking, this is a complex thing to explain. You can check the research paper of the mathematical explanation for this interpretable tool and their GitHub repository for the update features.

We will walk through an example to implement shap for telco churn dataset that we can download here

Telco Customer Churn
Focused customer retention programs
www.kaggle.com

This dataset contains 7043 customers and 21 features to predict whether the customers will churn or not based on data instances. We are not diving deeper into the complete machine learning process here. I just do a simple exploratory data analysis and preprocessing data.

It is recommended to make a proper exploratory data analysis, data cleaning, feature engineering, feature selection, cross-validation, and evaluation steps in order to get a much better prediction of the data instance. We are mainly focused on the implementation of Shap for interpreting the models for this tutorial.

You can take a look at the implementation in this notebook for your reference.

Deepnote
Managed notebooks for data scientists and researchers.
deepnote.com

Interpreting Result
The first thing we need to do before interpreting the result is to train our machine learning model on the training data. On this dataset, we use XGBoostClassifier for solving this classification problem to look into the customers who churn or not as follows.


Shap works as a surrogate model to interpret our machine learning model prediction using shap value. We have to get this value using the following code. We instantiate the shap object and test the shap algorithm to our test data.


Shap framework has the ability to interpret the data based on 2 approaches namely local Interpretability and global Interpretability. Local interpretability is the way how shap interprets the data based on a specific data instance whereas global interpretability interprets the data on the holistic features and data we have. Oftentimes, It is better to predict based on a particular data instance over all the data due to different interpretations and results. We will be visualizing the global interpretability and local one for our own use cases.

Global interpretability with feature importance

![GLobal Interpretability](https://github.com/naiborhujosua/naiborhujosua.github.io/blob/master/assets/img/1.JPG)

The preceding barplot shows how each feature impacts the prediction we make on training data based on the machine learning model we use. We can see Contract feature has the most significant influence on predicting the target outcome followed by MonthlyCharges and tenure.

Global interpretability with heatmap plots

![GLobal Interpretability](https://github.com/naiborhujosua/naiborhujosua.github.io/blob/master/assets/img/2.JPG)

The heatmap shows the impact of all features on the model. We can see the increase contract feature will also increase tenure and TotalCharges in the red region due to the higher shap value for these features. The f(x) curve on the top shows how the predicted Churn with the increase of data instances. We can see how the Churn predictions influence the increase of the data instances.

Global interpretability with hierarchical

![GLobal Interpretability](https://github.com/naiborhujosua/naiborhujosua.github.io/blob/master/assets/img/3.JPG)

This plot shows that feature tenure and TotalCharges form a group and OnlineSecurity and Multiplines form another group. This process is then called hierarchical clustering. This graph also shows how a few features have some interaction based on the subgroup and it could be a feature that we can detect in our EDA for further analysis.

Global interpretability with SHAP summary plots

![GLobal Interpretability](https://github.com/naiborhujosua/naiborhujosua.github.io/blob/master/assets/img/4.JPG)


The violin plots show the positive or negative impact of the feature for some data points. TotalCharges shows a positive correlation with the target outcome because of the red color gradient. However, it differs with Contract, tenure, and TotalCharges in which low values indicate churn.


Global interpretability with feature dependence plot

![GLobal Interpretability](https://github.com/naiborhujosua/naiborhujosua.github.io/blob/master/assets/img/5.JPG)

A feature independence plot is like a scatterplot where we can look at the correlation of two variables. The visualization shows the increase of TotalCharges will increase the Contract too.

Local interpretability using Waterfall plots

![GLobal Interpretability](https://github.com/naiborhujosua/naiborhujosua.github.io/blob/master/assets/img/6.JPG)

![GLobal Interpretability](https://github.com/naiborhujosua/naiborhujosua.github.io/blob/master/assets/img/7.JPG)

we can see from an inference of data instance towards the features on the first and second observation shows different results in which on the first observation, the contract feature contributes negatively towards the model prediction whereas the contract feature contributes positively towards the model prediction on the second one.

Local interpretability with decision plot

![GLobal Interpretability](https://github.com/naiborhujosua/naiborhujosua.github.io/blob/master/assets/img/8.JPG)

Decision plots help the interpretability to handle many features in our dataset to interpret. We can see from the preceding plots how each current local predictions are higher or lower than the average predicted outcome and how the value of the features is affecting the model outcome. In the two examples shown, the cases features contract to TechSupport are negatively impacting the model while most features on the second observation are positively impacting the model prediction.

You can also read another article related to [Explainability AI (XAI) published by Freecodecamp](https://www.freecodecamp.org/news/interpret-black-box-model-using-lime/)

References:

[1]. Scott M. Lundberg. “A Unified Approach to Interpreting Model Predictions”. (2017).

[2]. Scott M. Lundberg. “Shapley Additive Explanations”. (2017).

Thank you for reading!
I really appreciate it! 🤗 If you liked the post and would like to see more, consider following me. I post topics related to machine learning and deep learning. I try to keep my posts simple but precise, always providing visualization, and simulations.


