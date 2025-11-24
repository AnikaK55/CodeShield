# Exploratory Data Analysis Documentation

This document explains the contents and structure of the **Exploratory Data Analysis (EDA)** notebook used in the **CodeShield AI** project. The goal of the notebook is to simulate a dataset of Python code snippets labeled for vulnerabilities and use basic Python data analysis tools to evaluate the structure and labeling quality of the dataset.

## Purpose of the Notebook

The notebook is designed to:

- Simulate a realistic dataset of vulnerable and safe Python code snippets  
- Visualize the distribution of key attributes like code length and vulnerability types  
- Evaluate annotation consistency between two simulated annotators using **Cohen's Kappa**  

This helps ensure the dataset design supports our **LLM evaluation goals**.

## Libraries and Tools Used

- `numpy` and `pandas` for data generation and manipulation  
- `matplotlib.pyplot` and `seaborn` for visualizations  
- `sklearn.metrics` for calculating inter-annotator agreement (**Cohen's Kappa Score**)  

## Dataset Simulation Details

The dataset contains **60 synthetic examples** with the following fields:

- `code_id`: Unique identifier for each snippet (1 to 60)  
- `vulnerability_type`: One of five types (e.g., SQL Injection, Unsafe Eval)  
- `is_vulnerable`: Boolean indicating whether the code is vulnerable  
- `code_length`: Randomized number of lines (between 5 and 30)  
- `annotator_1_label`: First simulated annotator's label (biased 70% toward 'vulnerable')  
- `annotator_2_label`: Second simulated annotator's label (biased 60% toward 'vulnerable')  

## Visualizations and Metrics

### A. Code Length Distribution

- **Plot**: Histogram of `code_length`
- **Insight**: Most code snippets fall between 10 and 30 lines, suitable for LLM evaluation

### B. Vulnerability Type Frequency

- **Plot**: Bar chart of `vulnerability_type`
- **Insight**: SQL Injection is the most common, followed by Unsafe Eval; "No Vulnerability" is least frequent

### C. Annotator Agreement

- **Metric**: Cohen's Kappa Score
- **Output**: `-0.03` (poor agreement, expected from random annotations)

## File Output

The simulated dataset is exported as a CSV file:

- **Filename**: `codeshield_dataset.csv`  
- Can be versioned and uploaded to GitHub for tracking and collaboration



