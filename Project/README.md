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
To find the top trending skills for Data Analysts, I filtered the data frame to include only that specific job title, sorted it by month and skill demand throughout the year, and extracted the top 5 skills based on their demand over time.

View the detailed steps in my notebook: [3_Skills_Trend.ipynb](3_Skills_Trend.ipynb)

### Visualize Data

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

## 3. How well do jobs and skills pay for Data Analysts?
For this visualization, I extracted the top 6 jobs based on their average yearly salary and arranged them by median salary.

View the detailed steps in my notebook: [4_Salary_Analysis.ipynb](4_Salary_Analysis.ipynb)

### Visualize Data

```python
sns.boxplot(data=df_mexico_top6, x='salary_year_avg', y='job_title_short', order=job_order)
sns.set_theme(style='ticks')

plt.title('Salary Distribution for Top 6 Data Jobs in Mexico')
plt.xlabel('Yearly Salary')
plt.ylabel('')
plt.xlim(0, 300000)
plt.gca().xaxis.set_major_formatter('${x:,.0f}')
```
### Results
![Visualization of payment](images/salary_analysis.png)

### Insights
* Senior Data Scientist and Senior Data Engineer have the highest median and upper-range salaries among the listed roles.
* The Data Analyst role has the lowest median salary, this reflects a more limited salary range, possibly due to it being an entry-level position.
* The Data Scientist role has one of the widest interquartile ranges, suggesting large variability in pay.
