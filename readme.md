# Travel Management System Analysis - Using Process Mining to Predict Rejected Expense Reports

## Table of contents

- [Project Overview](#project-overview)
- [Dataset Description](#dataset-description)
- [Feature Engineering and Selection](#feature-engineering-and-selection)
- [Model Details](#model-details)
- [Results and Analysis](#results-and-analysis)
- [Challenges and Lessons Learned](#challenges-and-lessons-learned)
- [Future Work and Improvements](#future-work-and-improvements)
- [Getting Started](#getting-started)
- [Requirements](#requirements)
- [Running the Code](#running-the-code)
- [Authors](#authors)
  - [Adam Broniewski](#adam-broniewski)
  - [Himanshu Choudhary](#himanshu-choudhary)
  - [Tejaswini Dhupad](#tejaswini-dhupad)
- [License](#license)

## Project Overview

This project focuses on using process mining techniques to predict rejected declarations in a Travel Management System (TMS). We aim to understand the impact of rejections on the process flow and whether a machine learning model can predict these rejections to improve efficiency.

## Dataset Description

The dataset comprises travel permit data for international travel declarations, including activities, organizational units, and declaration submission dates. Key features like trace activities and organizational units are emphasized to understand declaration patterns.

## Feature Engineering and Selection

Features were selected based on their correlation with rejection rates and business relevance, including trace activities, organizational units, and declaration months. Additional features like partial lead time and wasted time between activities were generated to enhance model accuracy.

## Model Details

A decision tree algorithm was utilized due to its interpretability and balance between precision and recall. The model was trained using different trace lengths and encoding methods, with a focus on early prediction to allow for declaration adjustments.

## Results and Analysis

The model achieved an F-score of 0.545, outperforming a naive prediction model. It highlighted the extra processing time and touchpoints added by rejections, providing valuable insights into improving the TMS process.

## Challenges and Lessons Learned

The project encountered challenges in feature selection and data quality, leading to the exclusion of monetary value features due to potential data leakage. Lessons learned include the importance of thorough data preprocessing and the need for balanced model evaluation metrics.

## Future Work and Improvements

Future iterations could explore different trace lengths and encoding methods, as well as the inclusion of previously excluded features after appropriate preprocessing. The model could also benefit from the integration of clustering techniques to handle unique process traces.

## Getting Started

This project is a process mining initiative aimed at predicting rejected declarations in the Travel Management System (TMS) as part of the BPI data challenge 2020. It employs machine learning techniques to analyze patterns in travel declarations, reducing processing time and improving approval rates by providing early insights into potential rejection causes.

## Requirements
- Python 3.9
- pandas
- sklearn
- numpy
- matplotlib
- plotly
- pm4py
- seaborn
- tabulate

## Running the Code

These steps will run the full data-preparation, model building, prediction generations.

1. Install the dependencies:
    ```bash
    pip install -r requirments.txt
    ```
   ***Note***: *The scripts have been developed and tested with `Python 3.9`*
   
    ***Note 2***: If using ARM32 or ARM64 machine and an error is encountered installing pm4py, follow pm4py install instructions [here](https://pm4py.fit.fraunhofer.de/install-page).

2. Once all dependencies are installed, we can run the data preperation python file (default length 6 with complex encoding). The outputs are saved in `training_data/encodings` directory.
    ```bash
    python3 src/data_preparation.py
    ```
    **Expected Outcome -** 
    ```
    train test and validation split times are - 2018-09-17 11:34:42 , 2018-11-08 15:42:36 
    train, val and test count
    4020 861 861
    preparing training data for prefix length 6
    preparing test data for prefix length 6
    preparing val data for prefix length 6
    Done!
    ```

3. The below code will run our machine learning model (Default Decision Trees) on generated encodings. The outputs are saved in `results/` directory.

    ```bash
    python3 src/model_building_and_evaluation.py
    ```
    **Expected Outcome -** 

| Model                | Encoding   |   Trace Length |   F-score |   Precision |   Recall |   Accuracy |
|----------------------|------------|----------------|-----------|-------------|----------|------------|
| Decision Tree (Test) | complex    |              6 |  0.544791 |    0.263736 | 0.421053 |   0.651568 |
| Decision Tree (Val)  | complex    |              6 |  0.510082 |    0.307167 | 0.357143 |   0.576074 |
| Baseline             | complex    |              6 |  0.481256 |    0.26484       | 0.230159   |   0.587689 |


## Authors

#### Adam Broniewski [GitHub](https://github.com/abroniewski) | [LinkedIn](https://www.linkedin.com/in/abroniewski/) | [Website](https://adambron.com)
#### Himanshu Choudhary
#### Tejaswini Dhupad [GitHub](https://github.com/tejaswinidhupad) | [LinkedIn](https://www.linkedin.com/in/tejaswinidhupad/) 

## License

This project is open source, [licensed as MIT][license].
