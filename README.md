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
