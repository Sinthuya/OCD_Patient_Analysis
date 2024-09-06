# OCD_Patient_Data_Analysis

### Table of contents
- [Project overview](#project-overview)
- [Data sources](#data-sources)
- [Tools](#tools)
- [Data cleaning/preparation](#data-cleaning-and-preparation)
- [Explanatory data analysis (EDA)](#explanatory-data-analysis-EDA)
- [Results/Findings](#results-and-findings)
- [Recommendations](#recommendations)
- [Limitations](#limitations)

### Project overview
This data analysis project aims to provide insights into Obsessive-Compulsive Disorder (OCD) patient trends by analyzing a  dataset of 1,500 individuals diagnosed with OCD. The project explores demographic and clinical characteristics,including duration of sypmtoms,  Y-BOCS scores and co-occurring mental health conditions By leveraging SQL for data cleaning and analysis and Tableau for visualization, this project aims to help healthcare professionals and researchers better understand OCD trends and make informed decisions in clinical practice and research.

![Tableau dashboard](![Screenshot 2024-09-05 131213](https://github.com/user-attachments/assets/6bd9363f-0b29-4397-89eb-49526d7e5b8c)

Tableau Dashboard [Click here](https://public.tableau.com/app/profile/sinthuya.sivasubramaniam/viz/OCD_17255044776680/Dashboard1?publish=yes)

### Data sources
The dataset used in this analysis is fictional and contains 1,500 patients diagnosed with Obsessive-Compulsive Disorder. It includes demographic and clinical information such as Y-BOCS scores, OCD subtypes, and co-occurring conditions.

### Tools
- MySQL Workbench - data cleaning and analysis
- Excel - initial data preparation
- Tableau - data visualization

### Data cleaning and preparation
In the initial data preparation phase, the following steps were performed:
1. **Data inspection**: Reviewed the dataset for missing or inconsistent values.
2. **Handling missing values**: Addressed missing values in relevant columns, particularly in demographic and clinical information.
3. **Data transformation**: Reformatted the columns for consistency, such as ensuring all dates were in a standard format, and transformed the Y-BOCS score into categorical ranges.

### Explanatory data analysis (EDA)
The goal of this EDA is to uncover key trends and patterns in the demographic and clinical characteristics of OCD patients to answer key questions such as: 
- What is the Count and Percenatge of F vs M that have OCD & and the Average obsession score by Gender
```Sql
SELECT gender, COUNT(patient_id) AS patient_count, round((COUNT(*) / (SELECT COUNT(*) FROM ocd_patient_data) * 100),2) AS percentage_pct, round(AVG(Y_BOCS_Score_Obsessions),2) AS avg_obsession_score
FROM ocd_patient_data
GROUP BY gender
ORDER BY patient_coun
```Sql

- What is the Count of patients by Ethnicity and thier respective average obsession score?
```Sql
SELECT 
    YEAR(ocd_diagnosis_date) AS diagnosis_year,
    COUNT(*) AS num_diagnosed_with_ocd
FROM 
    ocd_patient_data
GROUP BY 
    YEAR(ocd_diagnosis_date)
ORDER BY 
    diagnosis_year;
```Sql

- What is the most common obsession type & its respective average obsession score?
```Sql
SELECT Obsession_Type, COUNT(Obsession_Type) AS obs_type_count, AVG(Y_BOCS_Score_Obsessions) AS avg_obs_score
FROM ocd_patient_data
GROUP BY Obsession_Type
ORDER BY  obs_type_count DESC
LIMIT 1;
```Sql

- What is the most common compulsion type & its respective average obsession score?
```Sql
SELECT Compulsion_Type, COUNT(Compulsion_Type) AS compul_type_count, AVG(Y_BOCS_Score_Obsessions) AS avg_obs_score
FROM ocd_patient_data
GROUP BY Compulsion_Type
ORDER BY  compul_type_count DESC
LIMIT 1;
```Sql

### Results and Findings

The analysis results are summarised as follows:

1. There is a fairly even split between male and female patients, with 747 females and 753 males diagnosed with OCD. Both genders have an average age of approximately 46.9 years. The average duration of symptoms is around 121-122.5 months for both genders, indicating prolonged periods of suffering before diagnosis. The average obsession score is 19.7 for males and 19.6 for females. The similar scores between genders reflect comparable OCD severity.

2. OCD patients are distributed across various age groups, with the highest concentration in the 70+ age group, followed by 20-25 and 50-55. Younger patients under 20 have the lowest numbers of diagnoses, potentially suggesting that OCD is either underdiagnosed in younger populations or tends to manifest more prominently with age.

3.  The consistent number of OCD diagnoses each year, with occasional spikes in diagnoses around 2016, 2019, and 2020. The number tends to fluctuate between 10 and 25 patients per month. The year 2023 shows a sharp decline, possibly because of incomplete data for the year. There is a higher number of patients who are diagnosed with both Depression and Anxiety disorders, showing a strong correlation between these conditions and OCD.

4. The most common obsession type is harm-related, followed by conatamination and religious. The most common compulsion type is Washing, followed closely by Counting and Checking.

5. The distribution of OCD patients by ethnicity shows that the majority of patients are Caucasian (398), followed by Hispanic (392), Asian (386), and African (324) ethnicities.
The relatively balanced distribution across ethnic groups reflects the widespread nature of OCD across diverse populations.

### Recomendations
Based on the analysis I recomend the following:
- Enhance Early Detection and Diagnosis Among Younger Populations
The data indicates a lower diagnosis rate among younger patients (under 20 years old). OCD often begins in adolescence, but the low diagnosis rate may indicate underdiagnosis in this age group.
Recommendations would be to Implement targeted mental health screening programs in schools and pediatric clinics to improve early detection of OCD. Increasing awareness among parents, teachers, and healthcare professionals can help identify early symptoms and lead to timely intervention.

-Develop Tailored Treatment Programs for High-Risk Age Groups
Healthcare providers should develop tailored treatment programs for older adults (70+) that address the challenges of long-term OCD and co-occurring mental health conditions like depression and anxiety.

- Focus on Co-occurring Mental Health Conditions
Develop comprehensive, multidisciplinary treatment plans that address both OCD and its common co-occurring conditions. Mental health professionals should work closely with patients to simultaneously manage depression and anxiety symptoms to improve overall treatment outcomes.

-Increase Access to OCD Treatment for All Ethnicities
 Create culturally sensitive outreach programs that focus on diverse communities, ensuring that individuals from all ethnic backgrounds can access OCD treatment and mental health services. This may include providing language-specific resources, education on OCD in culturally appropriate ways, and ensuring that healthcare providers are trained to offer inclusive care.

-Prioritize Interventions and Research Focused on Most Common Obsessions and Compulsions
Washing and Checking are the most common obsession and compulsion types among OCD patients. Addressing these specific behaviors can significantly improve the quality of life for many individuals. Educational programs and self-help tools tailored to these behaviors could be beneficial, as well as focusing research on why these obsession types are so prevalent and research to evaluate the long-term effectiveness of different therapies.

### Limitations
-Small Sample Size
With only 1500 patients, the dataset may not be large enough to represent the full spectrum of OCD symptoms, treatment responses, or demographic variation. The limited sample size can skew results and limit the generalizability of the findings to broader populations.

- Self-reported Data Bias
If certain data points (such as obsession and compulsion scores or co-occurring conditions) were collected through self-reporting, they may be subject to recall bias or inaccuracies. Patients may not accurately remember or assess their symptoms, leading to potential distortions in the data.

-Limited Ethnicity and Socioeconomic Information
While the dataset includes ethnic categories, it lacks detailed socioeconomic data (e.g., income, education, occupation), which can play a significant role in healthcare access and outcomes. Without these variables, the analysis may miss important factors contributing to OCD diagnosis and treatment disparities across different populations.

-No Long term data Data
The dataset provides a snapshot of patients at a single point in time but does not include longitudinal data to track the progression of symptoms, treatment response, or recurrence of OCD over time. Long-term patterns, such as remission and relapse, cannot be studied without long term data.

-Lack of Geographical Information
The dataset does not include geographical data, such as patient location or access to mental health services. Understanding geographic trends in OCD diagnosis and treatment could provide valuable insights into service disparities and regional differences in mental health care access. Without this, it’s difficult to identify potential service gaps or regional patterns in the prevalence of OCD.



