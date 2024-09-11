
# The Analysis

## 1.What Are The most demanded skills for popluar data roles ?

To find The Most demanded skills for popular roles 
specifically three roles. I filtered out 5 of the most requested skills for these roles in job postings .This query highlights the most popular skills for the respective data roles, laying out skills which viewers  may need to pay attention to depending on the role Which they are targeting.

View my notebook with details steps here:
[2_Skills_Demand.ipynb](3_Project\2_Skills_Demand.ipynb)

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
![Viusalization of Top Skills For Data Roles](3_Project\images\skill_demand_barchart.png)

## Insights
-Python is a versatile Skill,highly demanded across all three roles but most prominently in data science(70%) and data engineering (61%)

-Sql is the most demanded skills it's the most requested skill in both data analysics and data engineering but most data science python is the most sough-after skill
 
-cloud environmets and tools are mostly needed for data engineers aws is placed high in both data science and data engineering postings