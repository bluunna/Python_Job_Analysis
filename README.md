# Overview
This project is an analysis of the data job market, focusing on data analyst roles in Mexico. The data contained in this project is from hugging face and it's author is Luke Barousse, who provides a foundation for my analysis, containing detailed information on job titles, salaries, locations, and essential skills.

Through a series of Python scripts, I explore and analyze some of the key questions related to the most demanded skills and salary trends for data analysis job roles.

# The Questions
Below are the questions that I answered in the project:
1. What are the most demanded skills for the top 3 most popular data roles?
2. How are in-demand skills trending for Data Analysts?
3. How well do jobs and skills pay for Data Analysts?
4. What is the most optimal skill to learn for Data Analysts?

# Tools I Used
* __Python__: It was the core tool,it allowed me to clean and analyze and plot the data.
    * __Pandas__: Library used to analyze the data.
    * __Matplot__: Library used to plot the data.
    * __Seaborn__: Library to personalize and create more advanced visuals.
* __Jupyter Notebooks__: I used it to run my `Python` scripts.
* __Visual Studio Code__: Served as the development environment where I wrote, ran, and debugged all my `Python` scripts.

# Data Preparation and Cleanup
For each notebook, I started by importing the necessary libraries, loading the dataset and performing initial data cleaning to ensure data quality and standarization.

```python
# Importing Libraries
import ast
import pandas as pd
import seaborn as sns
from datasets import load_dataset
import matplotlib.pyplot as plt

# Load data, Author: Luke Barousse, Site: Hugging Face
df = pd.read_csv("hf://datasets/lukebarousse/data_jobs/data_jobs.csv")

# Data Cleanup (job_skills to list and dates with correct format)
df['job_posted_date'] = pd.to_datetime(df['job_posted_date'])
df['job_skills'] = df['job_skills'].apply(lambda x: ast.literal_eval(x) if pd.notna(x) else x)
```

To focus just on the Mexican market, I applied filters to the dataset.

```python
df_mexico = df[df['job_country'] == 'Mexico'] 
```
