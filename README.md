
# Racial Disparities in the US

## Datastory: https://racial-disparity-usa.ml

## Abstract

Racial inequalities and discrimination against minorities has been a prominent issue throughout US history but in recent years its importance has risen to unprecedented heights. Specifically, after the murder of George Floyd, the discussion on if police acts more violently against minorities and especially black minorities, compared to white people has been on the forefront of American politics and that’s why we decided to take a data driven approach to this issue and the black lives matter movement. We intend on investigating whether the claims of the black community are supported by official statistics, if their demands will indeed have an impact and reduce police brutality and what's the effect of protests on this problem and how we can quantify it. This is connected to the original paper on the basis of examining a different case of police racial bias against minorities and we aim to improve upon that paper’s research by normalizing all the results by the population race density.

## Research Questions

[1]

- What is the connection between racial bias in police stops and in police killings and how does the disparity in killings evolve over time?		
- What's the short-term and long-term impact of protests on police violence?

[2]

- Is it true that the BLM request of defunding the police would decrease the number of police killings of black people?
- Is there any relation between police/healthcare/education funding and police violence (for all races)?
- How is police violence spread across the different states and races, if we were to normalize the data depending on the population distribution in every state, and racial distribution within each state?

[3]

- Is there a racial bias in police violence?
    - How can different categories of people's behaviors (carrying a weapon, fleeing the police) impact the number of victims, within each race? Do these numbers show racial bias?
    - How is the people's behavior changing over time, in each race? 
    - Is there a racial bias in police getting charged for murder? How is this evolving in time?
- Is the system of states' ranking based on gun laws strength valid?
    - Is there a correlation between the gun laws strength and the victim's possessing of a gun?
    - How the number of victims carrying a gun changes over time in states with the strongest and weakest gun laws?



## Proposed datasets

- [US Government spending](https://www.usgovernmentspending.com/compare_state_spending_2020d50a)
 
This dataset contains information about the distribution of public spending in different domains in the United States. It has data for every state for the past 20 years (and also some projections on future spendings). We can view the amount spent in billions of USD for every state, percentage of GDP, or USD per capita. For our project we will most likely use the spending per capita, since we want a normalized way of viewing the data that will be easy to compare throughout the different states. The data is available as separate csv files, one for every sector of the economy, like Defense, Education, Welfare, etc. We are interested in the data related to police funding as well as Healthcare and Education. There won't be a need to perform a lot of data cleaning, but we must merge the different datasets, one per each year we will want to include in our study. 

- [Police violence](https://mappingpoliceviolence.org)

This is a very comprehensive dataset provided by the Mapping Police Violence organization. From it, we can draw 4 big dataframes containing information regarding police killing in general, police killings per police department, police killings per state and police killing of black people per city. The data contain killings that took place between 01/01/2013 and 31/12/2019 except the first dataframe which spans until 18/11/2020. This dataset contains an immense amount of information with numerous possible ways to exploit and draw meaningful conclusions from but given the amount of time and scope of the project we will focus on the first and the third dataframes and see if we can find any evidence of police discrimination against minorities.

- [Gun laws ranking](https://giffords.org/lawcenter/resources/scorecard/#rankings)

The Giffords is a non-profit advocacy and research organization focused on promoting gun control. Each year, they gather data about gun-related incidents and analyze them to show the trend of violence in each state. Besides, the attorneys in Giffords organization track and analyze gun legislation in all 50 states, assigning laws and policies point values. States gain points for strong gun laws and lose points for laws that make their residents less safe. These points are tabulated and the states are ranked and then assigned letter grades. These grades are compared to the most recent gun death rates released by the CDC (Centers for Disease Control and Prevention). 

- [Racial distribution per State](https://www.governing.com/gov-data/census/state-minority-population-data-estimates.html/)
The data here is very straightforward. We have on each row information about the racial distribution of every state in the US. There are many races covered in the dataset, but we are only interested in White, Black and Hispanic


- [Original paper data](https://openpolicing.stanford.edu/data/)

This is the dataset used by the original paper. It contains data about the different stops and information about the drivers. The data is available as separate csv files per many different counties, so we will need to merge them manually, and make sure that we deal with missing data.

## Methods


- **Police Killings vs Police stops**
To answer our first research question we decided to compare the disparities against the different races in each problem. Specifically we explored how are the disparities distributed across all states we had data for for each race and metric (killings and stops) and how the disparities evolve over time on each specific state for each race. It's worth noting that although for killings we had data for all 50 states, for police stops we only had data for 8 of them so we focused our first analysis on this subset whereas the second one which is independent of stops was performed over all states. To calculate the disparity, we first calculated the percentage of each race per state, normalized the number of killings per race per state by these demographics and then took the difference between percentage of population and percentage of victims per race.		

- **Effect of protests**		The first step we took for answering the second research question was to compile a list of major Black Lives Matter protests and plot the timeseries of police victims per race before and after these events. For the short-term effect we calculated the average number of victims in the 5 weeks leading to and following the protests and compared them. For the long-term effect, we fitted a regression line in the timeseries to represent their trends and compared their slopes.

- **Government funding**
The data we have available is separated in different files for every year as well as every economic sector. We have merged theses separate files into one dataset containing government funding ***per capita***  for every state, in the 3 sectors we are interested in. It is important to note that we are only interested in the per capita spending (meaning how much money does the state invest for every resident for Police/ Healthcare/ Education. This i crucial because we want to compare states with one another, and there are states with huge populations and huge budgets, that we want to compare with smaller states.

- **Police Killings**
We have available a dataset containing information about every murder caused by the police. We will use information about the state the murder happened in, as well as the race of the victim. By grouping by state, we will have a total count of police murders in every location, together with the number of murders per race. 
However this is not sufficient for what we are looking for. We need a fair way of comparing states with massive amount of populations, with smaller states. Also we want to be able to be able to compare the number of killings of each race equally. What we mean by that is that we want to be able to compare murders states with 70% black populations, to states with 10% black population. It is true that the first state will probably have many more murders in raw numbers for the black community, but that is probably due to the fact that there are many more black residents there. 
So ultimately, what we would like to end up with is a dataset containing number of deaths if every state had the same population, and every state had 33% white, 33% black and 33% hispanic population. The way we intend to achieve this is by doing the following:

	- First we collect data on what is the percentage of population in each state compared to the total US population. We then use these fractions, and multiply the dataset of police killings with the corresponding value depending on the state
	- Next, using a dataset that specifies the racial distribution per each state, we want to normalize the number of killings of every state, by the fraction of racial distribution on each state. 
	
- **Viewing relation of government funding to police killings**
	In order to view if there is a relationship between the government funding, and the number of deaths caused by the police, we will merge the two datasets we prepared (described above), and show them together on the same plot. We use the name of the state on the common axis, and plot the data as bar plots (the number of killings will be stacked so it contains killings per race). Then by sorting  the data on funding/killings we will discuss what conclusions we can draw for the data. 


- **Racial bias**
We are interested in features related to victim's race and behavior (victim carrying a weapon, victim fleeing the police), the one related to criminal charges inorder to inspect any potential racial bias, and then time. 
We normalize the data in each race to make the comparisons more correct. We look at data aggregated on the total number of victims and then study each feature more in depth by inspecting its trend over time. We finally try to generalize our remarks by making linear regressions to see how the victims' behaviors are changing within each race.

- **Gun laws**
We compute the portion of victims carrying a gun in each state, then in each category of states based on the strength of their gun laws.

## Proposed timeline
- **1st week:** 
We will each work individually on the new replication task.
- **2nd week:**
We will split the workload evenly in the team so that each team member has one research question to work on (see section below). We are aiming that by the end of the second week, we will each have completed every question.
- **3rd week:**
The last week will be dedicated to proof-check what each one of us has completed in the previous week, improve on that and merge our works in one place. After this is done, the remaining amount of time will be dedicated to creating the data story. 


## Organization within the team

- **Question [1]** **George** Disparity exploration and impact of protests
- **Question [2]** **Gerald** Correlation between government spendings and killings per race.
- **Question [3]:** **Faten** Exploring police violence


