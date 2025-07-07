# The Analysis
## 1. What are the most demanded skills for the top 3 most popular data roles?

To find the most demanded skills for he top 3 most popular data roles, I filtered out those positions by which ones were the most populars and got the top 5 skills requested for those roles. This query highlights the most popular job titles with their top skills.

View the detailed steps in my notebook: [2_Skills_Count.ipynb](2_Skills_Count.ipynb)

### Visualize Data
```python
fig, ax = plt.subplots(len(job_titles), 1)

for i, job_title in enumerate(job_titles):
    df_plot = df_skills_percent[df_skills_percent['job_title_short'] == job_title].head(5)
    sns.barplot(x='skill_percentage', y='job_skills', data=df_plot, ax=ax[i], legend= False, hue = 'skill_count', palette='dark:g_r')
    ax[i].set_title(job_title)

fig.suptitle('Skills Requested in Mexico Job Postings', fontsize=16)    
```
### Results
![Visualization of Top Skills](images/top_skills_per_job.png)

### Insights
* Python is a versatile skill, highly demanded across all three roles, but most prominently for Data Scientists and Data Engineers (62%).
* SQL is the most requested skill for Data Analysts and Data Engineers, however for Data Scientists is requested in over half the job postings of this role.
* Data Engineers require more specialized techical skills (AWS, Azure, Spark) compared to Data Analysts and Data Scientist who are expected to be proficient in more general data management and analysis tools (Tableu).

## 2. How are in-demand skills trending for Data Analysts?
### Visualize Data
To find the top trending skills for Data Analysts, I filtered the data frame to include only that specific job title, sorted it by month and skill demand throughout the year, and extracted the top 5 skills based on their demand over time.

View the detailed steps in my notebook: [3_Skills_Trend.ipynb](3_Skills_Trend.ipynb)

```python
ax = plt.gca()
ax.yaxis.set_major_formatter(plt.FuncFormatter(lambda x, _: f'{x:.0f}%'))
for i in range(5):
    plt.text(11.2, df_percent.iloc[-1, i] + 0.15, df_percent.columns[i])
```

### Results
![Visualization of Trending Skills](images/trending_skills.png)

### Insights:
* SQL remains the most consistently demanded skill throughout the year.
* Excel experienced a significant increase around April, surpassing SQL, althought it shows a substantial decrease around May.
* Both Tableau and Power BI show relatively stable demand throughout the year with some fluctuations. Python shows a slightly higher demand compared to the other ones and also remains stable towards the year's end.

