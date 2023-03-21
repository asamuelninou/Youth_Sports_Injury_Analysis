# Emergency Department Youth Sport-Related Injury Analysis
## Overview
According to the Centers for Disease Control and Prevention (CDC), 131.3 million visits to the Emergency Department (E.D.) in 2020, and 38 million trips were injury related. The USA Department of Health and Human Services *2021 Trends in the Utilization of Emergency Department Services between 2009-2018* report aware congress of the misuse of E.D. resources for "non-emergency" or "inappropriate" visits. We hope to support hospitals and optimize healthcare resources by highlighting statistical findings of sport-related injuries for youth patients that would help an alternative injury management plan.

Our target demographic is the youth who visited the E.D. for sport-related injuries over ten years. The World Health Organization and the United Nations define 'youth' as those persons between the ages of 15 and 24. The definition of youth may change with circumstances: demographic, financial, economic, and socio-cultural settings. However, the definition that uses the 15-24 age cohort as youth appropriately describes people who benefit from guidance as they transition from the dependence of childhood to adulthood independence. Our objective is to focus on the most popular sports played by males and females according to the National Federation of State High School Associations: track and field, basketball, and soccer. We are analyzing E.D. visits due to concussions, sprains, fractures, and dislocations at schools, daycares, or recreation sports fields. By studying specific sports and injuries, we hope to find significant statistical findings to guide an injury management plan. We are querying data over ten years from 2009 to 2019 from the National Electronic Injury Surveillance System (NEIISS) Database. 

**Our hypothesis is that most E.D. visits are the youth under 18, has the highest percentage of "non-emergency" or "inappropriate" visits.** This target audience would benefit from an injury management plan that utilizes other healthcare resources. 

![CDC ED Visits by Age 2020 edited](https://user-images.githubusercontent.com/92180070/223150165-c573d96f-f267-44e1-9c6b-a0eb0124df84.png)

### Technology, Languages, and Tools
- Extract data from NEISS Database
- Transform data in Jupiter Notebook using Python
- Demonstrate Entity Relationship Diagram (ERD) with PostgreSQL
- Load and analyze visualizations in Tablaeu
- Use Jupyter Notebook to create machine learning model that will cluster injuries based on age group

#### National Electronic Injury Surveillance System (NEISS) Database
For over 45 years, the CPSC has operated a statistically valid injury surveillance and follow-back system known as the National Electronic Injury Surveillance System (NEISS). The primary purpose of NEISS is to collect data on consumer product-related injuries occurring in the United States. CPSC uses these data to produce nationwide estimates of product-related injuries.
##### Description of Data
NEISS is based on a nationally representative probability sample of U.S. hospitals and territories. Each participating NEISS hospital reports patient information for every emergency department visit associated with a consumer product or a poisoning. They have become an important public health research tool for CPSC, researchers, and consumers throughout the United States and worldwide. In 2000, CPSC expanded NEISS to collect data on all injuries for the Centers for Disease Control and Prevention through an interagency agreement. The next major update to NEISS occurred in 2018 with seven new variables: Diagnosis_2, Other_Diagnosis_2, Body_Part_2, Product_3, Ethnicity, Alcohol_Involved, and Drug_Involved. In addition to the new variables, the maximum length of the Narrative text was increased from 142 to 400 characters. These changes were effective, starting with the treatment date of January 1, 2019.

## Analysis

![image](https://user-images.githubusercontent.com/92180070/226080625-3c0343ce-8f02-4707-afec-fc803882594c.png)

Over the past ten years, there has been a decrease in the amount of youth E.D. visits. As suspected minors from 15 to 17 years of age visited the E.D. more than adults age 18 to 24 combined. 

![E D  Visits by Gender](https://user-images.githubusercontent.com/92180070/226109789-a27c4939-4914-4e07-91a3-580911ed13b7.png)

There are more males going to the E.D. than women. 

![image](https://user-images.githubusercontent.com/92180070/226080581-3d8c2ee6-08ea-4381-91b0-cb1da6b5e272.png)

The primary reason our targeted audience went to the E.D. were due to a strain/sprain. 

Majority of clients were treated/examined and released.

![Percentage of E D  Visits by Disposition](https://user-images.githubusercontent.com/92180070/226111847-716ac72c-0a9f-46b9-b59c-98656f2c3468.png)
The top 2 locations of injury are the ankles and knees. 

![image](https://user-images.githubusercontent.com/92180070/226080643-7dba5a11-f253-4c7d-a51d-6947736d8f82.png)

### Interactive Dashboard
View our interactive dashboard by clicking the following link: [Tableau](https://public.tableau.com/app/profile/zenat1847/viz/E_D_TrendsOverthePast10YearsbyDisposition/E_D_TrendsOverthePast10YearsbyDisposition)
 
### Machine Learning Clusters
Supervised machine learning separating people into categories into high risk and low risk based on age. Create a machine learning model that would predict if someone is high or low risk.

The first step in this process was creating a risk variable that separated people into high risk and low risk groups. This variable was named "high risk" and was true if the injuries were on the person's face, eyes, neck, or head. Otherwise, the variable would be labeled "false" (meaning the person was low-risk.) From there the data was cleaned, were X dropped the "high risk" column and y was equal to the "high risk" column. Value counts for y were found and the number of low-risk (false) far outweighed the high-risk (true) class. Due to this, the team decided to undersample for the machine learning model, randomly selecting a number of low-risk individuals to match the number of high-risk. From there the BalancedRandomForest was used to classify with n-estimators set to 50. The confusion matrix can be seen below: 

![confusion matrix](https://github.com/asamuelninou/Youth_Sports_Injury_Analysis/blob/d53f4c92a62da93301f034f9c4576441fa40cabb/Machine%20Learning/confusion_matrix.png)

As the confusion matrix shows, our model did extremely well in predicting low versus high risk individuals. A balance report was also found and can be seen below.

![balance report](https://github.com/asamuelninou/Youth_Sports_Injury_Analysis/blob/d53f4c92a62da93301f034f9c4576441fa40cabb/Machine%20Learning/balance_report.png)

As the balance report shows, the Balanced Random Forest was exttremely accurate and precise when it came to sorting our high-risk versus our low-risk groups. After finding this report, we sorted the features by importance. 

![features list](https://github.com/asamuelninou/Youth_Sports_Injury_Analysis/blob/d53f4c92a62da93301f034f9c4576441fa40cabb/Machine%20Learning/features_importance.png)

The most important feature in this model was age, which accounted for roughly 62% of if a person was put into a low or high risk category. Following that, sex accounted for approximately 27% of the likelihood someone was sorted into a low or high risk category. 


## Summary
If a person could die or be permanently disabled, it is an emergency. For our study, the following are reasons to visit the E.D.:
- Injury to the head with passing out, fainting, or confusion, 
- Injury to neck or spine, particularly if there is loss of feeling or inability to move
- Severe chest pain or pressure
- Seizures
- Trouble breathing, passing out, fainting, 
- Pain in the arm or jaw
- Unusual or bad headache, particularly if it starts suddenly
- Suddenly not able to speak, see, walk, or move, 
- Suddenly weak or drooping on one side of the body
- Dizziness or weakness that does not go away
- Sudden confusion
- Heavy bleeding
- Possible broken bone, loss of movement, particularly if the bone is pushing through the skin
- Deep wound
- Coughing or throwing up blood
- Severe pain anywhere on the body
- High fever with headache and stiff neck
- High fever that does not get better with medicine
- Throwing up or loose stools that do not stop

**We concluded that most E.D. visits were minors and their primary injury were in low-risk locations. Further research would need to be gathered to determine if the emergency visit was justified.**
### Injury Management Plan
In regards to the development of an injury management plan, further research must be done to determine what resources or protocals need to be in place to redirect "non-emergency" injuries. This plan will need the cooperation of public healthcare officials, healthcare professionals, coaches, parents, and patients. 
#### Strength
The strength of this research proposal was organized data from the (NEISS) Database
#### Limitations
We are not medical professionals that can determine which injuries are deemed "inappropriate" or "non-emergency." More data will need to be gathered on what medical professionals conclude as "inappropriate" uses of the E.D. 
#### Future Finding
##### Who brought the patient into the hospital
##### Medical Education of patient and transportation personal
##### Medical Professionals Feedback

# Project Management
Our team has two departments: Analytical and Data Wrangling and Visualization Team.
#### Analytical Team
The Analytical Team's role is to narrow down the selected topic and determine the reasonings for research proposals. We determine the data source used for our analysis. Our objectives are to use insights uncovered by the visualization team to further our analysis through machine learning models. 
##### Alicia Samuel-Ninou
- Project Research 
- README.md Report
- Jupyter Notebook CSV Files Concat
- README.md Analysis
- PostgreSQL Database
- Introduction Powerpoint
##### Kailey O'Shaughnessy
- Project Research
- Initial Clean
- Statistical Analysis
- Machine Learning Model
#### Data Wrangling and Visualization Team
The Data Wrangling and Visualization Team's role is to clean data further and determine and create visualizations for our analysis. By answering data-driven questions, we determine what variables were primitive to support or reject our hypothesis. The questions the team planned to respond to with the data will help determine how we will use our machine-learning model.  
##### Alejandro Miranda Miranda
- Wrangle Data
- Pie Chart Visualization
- Summary
##### Edward Yi
- Bar Chart Visualization
- README Updates
- Visualiztion clean up
- Powerpoint Visualizations
##### Zenat
- Wrangle Data
- Line Graph Visualization
- Pie Chart Visualization
- Future Findings 
 
## Data Exploration Phase
The first step of our exploration phase is determining critical variables influencing our hypotheses and uncovering insights into sport-related injuries based on age, gender, disposition, and location. Next, we will identify areas or patterns for our machine-learning model with bar graphs, line graphs, and pie charts. Then, using interactive dashboards that filter data by sport, our audience can be able to understand our data-driven story.

## Data Analysis Phase
Data Analysis systematically applies statistical and logical techniques to describe, illustrate, condense, recap, and evaluate data.

## Time Management Outline
- 2/27: Determine the research topic and sub-groups
- 2/28: Research the research topic and determine the data and direction of the project
- 2/29: Update group on the research topic and direction of the project
- 3/1: Finalized Youth Injury Analysis
- 3/6: Updates on project, designated visualization tasks, Master NEISS csv
- 3/8: Edited, uploaded, discussed visualizations, discussed next meet up time
- 3/13: Edited graphs, 
- 3/15: Finalize our story and pick top graphs to represent our story
- 3/20: Practice presentation

## Resources
- Presentation PPT: https://docs.google.com/presentation/d/1PNGkagYsRhEGqGaS-2org3AKvUiXmIBFPbWmnMIhYvY/edit?usp=sharing
- Initial Analysis Questionnaire PDF: [Initial Visualization Questionnaire.pdf](https://github.com/asamuelninou/Youth_Sports_Injury_Analysis/files/11008831/Initial.Visualization.Questionnaire.pdf)
