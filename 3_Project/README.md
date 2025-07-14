
# The Analysis

## 1.What Are The most demanded skills for popular data roles ?

To find The Most demanded skills for popular roles 
specifically three roles. I filtered out 5 of the most requested skills for these roles in job postings .This query highlights the most popular skills for the respective data roles, laying out skills which viewers  may need to pay attention to depending on the role Which they are targeting.

View my notebook with details steps here:
[2_Skills_Demand.ipynb](3_Project/2_Skills_Demand.ipynb)

## Visualize Data
````python
job_titles=['Data Analyst','Data Scientist','Data Engineer']
fig,ax=plt.subplots(3,1)
for i,job_title in enumerate(job_titles):
    df_skill_plot=df_skill_percent[df_skill_percent['job_title_short']==job_title].head(5)
   y='skill_percent',ax=ax[i],title=job_title)
    sns.barplot(df_skill_plot,x='skill_percent',y='job_skills',ax=ax[i],hue='job_skills',palette='mako')
    ax[i].set_ylabel('')
    ax[i].set_title(job_title)
    ax[i].set_xlabel('') 
    fig.tight_layout()
    ax[i].set_xlim(0,80)
    if i != len(job_titles)-1:
     ax[i].set_xticks([])
    fig.suptitle('Likelihood of Skills Requested in Indian Job Posting')
    for n,v in enumerate(df_skill_plot['skill_percent']):
        ax[i].text(v+1,n,f'{v:.0f}%',va='center')
````
## Results
![Viusalization of Top Skills For Data Roles](3_Project/images/skill_demand_barchart.png)

## Insights
- Python is a versatile Skill,highly demanded across all three roles but most prominently in data science(70%) and data engineering (61%)

- Sql is the most demanded skills it's the most requested skill in both data analysics and data engineering but most data science python is the most sough-after skill
 
- cloud environmets and tools are mostly needed for data engineers aws is placed high in both data science and data engineering postings

## 2.How Are In-Demand Skills Trending For Data Analysts?

To Observe the trending of skills overtime i have filtered the most popular skills for data analytics job postings and plotted a chart to show the skills trending overtime This query highlights how the most popular skills are trending throughout the year ,providing insights to skills which are most in-demand for viewers to see 

View my notebook with details steps here:[3_Skills_Trends](3_Project/3_Skills_Trends.ipynb)

## Visualize Data
````python
sns.lineplot(data=df_DA_percent.iloc[:,:5],dashes=False,palette='tab10')
plt.title('Top Skills Trending For Data Analyst In India')
plt.xlabel('')
plt.legend().remove()
for i in range(5):
    plt.text(11.2,df_DA_percent.iloc[-1,i],df_DA_percent.columns[i])
sns.despine()
from matplotlib.ticker import PercentFormatter
ax=plt.gca()
ax.yaxis.set_major_formatter(PercentFormatter(decimals=0))
plt.ylim(10,70)
````
## Results
![Visualization of skills Trends](https://github.com/Johan0957/python-projects/blob/main/3_Project/images/skill_trend_line_chart.png)

## Insights
- sql is the most demanded skill in the data analyst job posting by a comfortably large margin it's consistently around or above 50% of all posting in India  

- python and excel are pretty much the same throughout the year python has a large spike-up in june and excel has a spike-down in both June and August 

- tableau is consistently more popular skill for data visualization than powerbi it is more demanded in job posting and has a spike-up more than 30% in certain months(june,september to october) 

## 3.How Well do Jobs and Skills pay for Data Analyst?

To identify the highest-paying roles and skills, I only got jobs in the United States and looked at their median salary. But first I looked at the salary distributions of common data jobs like Data Scientist, Data Engineer, and Data Analyst, to get an idea of which jobs are paid the most.

View my notebook with details steps here: [4_Salary_Analysis](3_Project/4.Salary_Analysis.ipynb)

### Salary Analysis For Six Of The Most Popular Data Roles :

## Visualize Data
````python
job_order=df_Ind_top6.groupby('job_title_short')['salary_year_avg'].median().sort_values(ascending=False).index
sns.boxplot(df_Ind_top6,x='salary_year_avg',y='job_title_short',order=job_order)
ax=plt.gca()
plt.xlabel('')
plt.ylabel('')
ax.xaxis.set_major_formatter(lambda x,pos : f'${int(x/1000)}K')
plt.show()
````

## Results
![Visualization Of Salary Analysis](3_Project/images/salary_analysis_box_chart.png)

## Insights

- There's a Significant Differnce between The salaries for all jobs the highest being Senior Data Scientist with the largest median and one of the highest outliners in the job postings
- Senior Data Scientists,Data Engineers,Data Scientists and Data Analysts shows a considerable amount of salary outliners suggesting cases where the salary substantial larger than the average 
- The median salary increases with seniority and experience but for data analysts the salary outliners are far greater than that of senior data analysts so in certain cases data analysts may earn more than the median

### Highest Paid & Most Demanded Skills for Data Analysts
Next, I narrowed my analysis and focused only on data analyst roles. I looked at the highest-paid skills and the most in-demand skills. I used two bar charts to showcase these.

## Visualize Data
````python
fig,ax=plt.subplots(2,1)
sns.barplot(data=df_DA_top_pay,x='median',y=df_DA_top_pay.index,hue='median',ax=ax[0],legend=False,palette='flare')
ax[0].set_title('Highest Paying Skills In Data Analysis')
ax[0].xaxis.set_major_formatter(lambda x,pos: f'${int(x/1000)}k')
sns.barplot(data=df_DA_top_skill,x='median',y=df_DA_top_skill.index,hue='median',ax=ax[1],legend=False,palette='flare')
ax[1].set_title('Most Demanded Skills In Data Analysis')
ax[1].set_xlim(ax[0].get_xlim())
ax[1].xaxis.set_major_formatter(lambda x,pos: f'${int(x/1000)}k')
fig.tight_layout()
````

## Results
![Visualization of DA Skills Median](3_Project/images/DA_skill_salary_bar_chart.png)

## Insights
- Cloud Based Tools Are the highest paying skills which reach more than $160k suggesting that cloud proficiency can lead to higher salaries 
- The bottom graph shows the more fundamental skills which are required spark and powerbi tends to pay more python is pay more than r and the number of job postings is also higher
- There's a clear distinction between the skills that are highest paid and those that are most in-demand. Data analysts aiming to maximize their career potential should consider developing a diverse skill set that includes both high-paying specialized skills and widely demanded foundational skills.