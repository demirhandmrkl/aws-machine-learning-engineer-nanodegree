
# Customer Segmentation and Acquisition - Bertelsmann Arvato

## Udacity Nanodegree Capstone Project: Machine Learning Engineer

This repository contains the code and report for the "Arvato Customer Segmentation" Capstone Project, completed as part of the Udacity Machine Learning Engineer Nanodegree program.

## Table of Contents

- [Project Overview](#project-overview)
- [Data Description](#data-description)
- [Technical Overview](#technical-overview)
- [Requirements](#requirements)
- [Results](#results)

---

`<a id='project-overview'></a>`

## Project Overview

The goal of this project is to analyze the demographic data of the German population and customer data to perform Customer Segmentation and Acquisition for Arvato Financial Solutions. Arvato is a global service provider offering financial, IT, and supply chain management solutions to businesses.

In collaboration with a mail-order company, this project aims to identify potential customers for their organic products by understanding how customer demographics differ from the general population. The project is divided into two key steps:

1. **Customer Segmentation with Unsupervised Learning:** In this phase, data exploration and feature engineering are conducted to prepare the dataset. Principal Component Analysis (PCA) is used for dimensionality reduction, followed by K-Means clustering on the reduced data to segment both the general population and customer data into clusters. These clusters are then analyzed to identify features that are indicative of potential customers.
2. **Customer Acquisition with Supervised Learning:** In this phase, supervised learning models are trained using labeled customer data, which indicates past responses from customers. The trained models are then used to predict whether a person in the test dataset could be a potential customer.

`<a id='data-description'></a>`

## Data Description

The dataset was provided by Udacity and Arvato Financial Solutions. It includes four main data files and two description files that explain the features. The data files include:

- **Customer Segmentation:**
  - General Population Demographics
  - Customer Demographics
- **Customer Acquisition:**
  - Training Data
  - Test Data

`<a id='technical-overview'></a>`

## Technical Overview

The project is divided into several stages:

- Data Exploration and Cleaning
- Feature Engineering
- Dimensionality Reduction
- Clustering
- Supervised Learning
- Model Evaluation
- Predictions on Test Data

Details regarding the methodology, algorithm choices, and evaluation metrics are provided in the project report (`Report.pdf`).
