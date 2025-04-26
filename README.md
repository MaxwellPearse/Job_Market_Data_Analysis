# The Analysis

## 1. What are the most demanded skills for the top 3 most popular data roles?

To find the most demanded skills for the top 3 most popular data roles. I filtered out those positoins by which one were the most popular, and got the top 5 skills for these three top roles. This query hilights the most popular job titles and their top skills, showing which skills I should pay attention to depending on the role I'm targetting. 

View my notebook with detailed steps here:
[2_demand.skill.ipynb](Actual_project/2_demand_skill.ipynb)

## Visualise Data
```Python
fig, ax = plt.subplots(len(job_titles),1)

for i, job_title in enumerate(job_titles):
    df_plot = df_skills_per[df_skills_per["job_title_short"] == job_title].head()

    sns.barplot(data=df_plot, x="skills_perc", y="job_skills", ax=ax[i], hue="skill_count", palette="dark:b_r")
```

## Results

![Visualisation of Top skills for Data nerds](Actual_project/Images/skill_demand_all_data_roles.png)

## Insights

- Python is a versatile skill, highly demanded across all three roles, but most prominently across Data Scientist (72%) and data Engineers (65%).
- SQL is the most requested skill for Data Analyst and Data Scientists, with in in over half the job postings for both roles. For Data engineers, Python is the most sought-after skill, appearing in 68% of the postings.
- Data Engineers require more specialised technical skills (AWS, Azure, Spark) compared to Data Analyst and Data Scientists who are expected to be more proficient in more general data managment and analysis tools (Excel, Tableau) 

## 2. How are in-demand skills trending for data analysts?

### Visualise Data

```Python 
from matplotlib.ticker import PercentFormatter

df_plot = df_DA_US_percent.iloc[:,:5]
sns.lineplot(data=df_plot, dashes=False, palette="tab10")

for i in range(5):
    plt.text(11.2, df_plot.iloc[-2,i], df_plot.columns[i])

ax = plt.gca()
ax.yaxis.set_major_formatter(PercentFormatter(decimals=0))
```

![Trending Top Skills for Data Analyst in the US](Actual_project/Images/skill_trend_DA.png)

## Insights

- SQL remained the most consistently demanded skill thoughout the year, although it shows a gradual decrease in demand.
- Tableau and Python seem relatively stable, througthout the year

## 3. How well do jobs and skills pay for data analysts?

### Salary Analysis for Data Nerds

![Salary Distributions of Data Jobs in the US](Actual_project/Images/boxplot_job_titles.png)

## Insights
- Data Scientists/Engineers are generally paid more than Data Analysts(inclusing Senior Data Analysts)

