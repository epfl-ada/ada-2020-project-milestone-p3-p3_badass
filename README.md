# Milestone P3

#<center>*Racial Disparities in the US*</center>

##Abstract

Racial inequalities and discrimination against minorities has been a prominent issue throughout US history but in recent years its importance has risen to unprecedented heights. Specifically, after the murders of George Floyd and Breonna Taylor, the discussion on if police acts more violently against minorities and especially black minorities, compared to white people has been on the forefront of American politics and that’s why we decided to take a data driven approach to this issue and the black lives matter movement. We intend on investigating whether the claims of the black community are supported by official statistics and if their demands will indeed have an impact and reduce police brutality. This is connected to the original paper on the basis of examining a different case of police racial bias against minorities and we aim to improve upon that paper’s research by normalizing all the results by the population race density.

##Research Questions
- What's the validity of the original paper's results if they are normalized by population race density per state?

- Is there any correlation between the money spending per state on education, healthcare and police VS police killings per race?

- What insights and conclusions can we draw from exploring data regarding police killing in the US?


##Proposed datasets

- [US Government spending](https://www.usgovernmentspending.com/compare_state_spending_2020d50a)
 
This dataset contains information about the distribution of public spending in different domains in the United States. It has data for every state for the past 20 years (and also some projections on future spendings). We can view the amount spent in billions of USD for every state, percentage of GDP, or USD per capita. For our project we will most likely use the spending per capita, since we want a normalized way of viewing the data that will be easy to compare throughout the different states. The data is available as separate csv files, one for every sector of the economy, like Defense, Education, Welfare, etc. We are interested in the data related to police funding as well as Healthcare and Education. There won't be a need to perform a lot of data cleaning, but we must merge the different datasets, one per each year we will want to include in our study. 

- [Police violence](https://mappingpoliceviolence.org)

This is a very comprehensive dataset provided by the Mapping Police Violence organization. From it, we can draw 4 big dataframes containing information regarding police killing in general, police killings per police department, police killings per state and police killing of black people per city. The data contain killings that took place between 01/01/2013 and 31/12/2019 except the first dataframe which spans until 18/11/2020. This dataset contains an immense amount of information with numerous possible ways to exploit and draw meaningful conclusions from but given the amount of time and scope of the project we will focus on the first and the third dataframes and see if we can find any evidence of police discrimination against minorities.

- [Gun laws ranking](https://giffords.org/lawcenter/resources/scorecard/#rankings)

The Giffords is a non-profit advocacy and research organization focused on promoting gun control. Each year, they gather data about gun-related incidents and analyze them to show the trend of violence in each state. Besides, the attorneys in Giffords organization track and analyze gun legislation in all 50 states, assigning laws and policies point values. States gain points for strong gun laws and lose points for laws that make their residents less safe. These points are tabulated and the states are ranked and then assigned letter grades. These grades are compared to the most recent gun death rates released by the CDC (Centers for Disease Control and Prevention). 


- [Original paper data](https://openpolicing.stanford.edu/data/)

This is the dataset used by the original paper. It contains data about the different stops and information about the drivers. The data is available as separate csv files per many different counties, so we will need to merge them manually, and make sure that we deal with missing data.

##Methods

- **Data collection:** Scraping gun laws data from the Giffords organization website.
- **Data preprocessing:** Merging the gun laws dataset with the Police Violence one to use the state’s ranking as a feature.

##Proposed timeline
- **1st week:** 
We will each work individually on the new replication task.
- **2nd week:**
We will split the workload evenly in the team so that each team member has one research question to work on (see section below). We are aiming that by the end of the second week, we will each have completed every question.
- **3rd week:**
The last week will be dedicated to proof-check what each one of us has completed in the previous week, improve on that and merge our works in one place. After this is done, the remaining amount of time will be dedicated to creating the data story. 


##Organization within the team
- **First question** (improving upon the study of the paper by including a normalization factor for the racial distribution per state): **Feten**
- **Second question** (correlation between government spendings and killings per race): **Gerald**
- **Third question** (finding interesting statistical insights on data related to police killings): **George**

##Questions for TAs
- We are thinking of including in our project a prediction model based on data related to racial disparity, but we are unsure on what to predict. If you have any idea or advice on this, we would appreciate it. 
- Are the research questions we are currently presenting enough to serve as an interesting extinction to the study?



