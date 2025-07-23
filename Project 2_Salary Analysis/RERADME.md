# 📈 Data Nerds Salary Analysis

![EXCEL_RtiMhr3Ruv](https://github.com/user-attachments/assets/d5861fa2-61d9-492d-938f-97ca5e6b23aa)

## 🧭 Overview
This Excel-based project explores key trends in the data job market — such as how skills impact salary, which regions pay best, and which tools dominate the field.

Unlike dashboards, this project focuses on deep-dive analysis using raw data, pivot tables, and advanced Excel features to answer real-world job market questions for data professionals.

▶️ **[Salary_Analysis.xlsx](Salary_analysis.xlsx)** — includes all the pivot tables, charts, and measures used in the analysis.

## 📚 Research Questions
This project dives into four main questions:
1. Does having more skills lead to higher pay?
2. How do data job salaries compare across regions?
3. What are the most in-demand skills in data-related roles?
4. Which top skills are linked to the highest salaries?

### 📄 Dataset Description
The dataset used in this project is [data_jobs_salary_all.xlsx](./data_jobs_salary_all.xlsx), which contains real job listings from 2023. It includes:

- 💼 Job Titles (e.g., Data Scientist, ML Engineer, Analyst)
- 💰 Salary Information (annual pay in USD)
- 🌍 Locations (country-level data)
- 🛠️ Required Skills per job
- 🔗 Unique Job IDs

This structure enabled clean relational modeling for deeper analysis using Power Pivot.

### 🛠️ Excel Skills Used
This analysis applies a full set of modern Excel tools to uncover trends:
- 🔍 Power Query: For data cleaning and transformation
- 💪 Power Pivot: For building data models
- 📊 Pivot Tables & Charts: For slicing and comparing key metrics
- 🧮 DAX: For advanced calculations (like conditional medians)

## 1️⃣ Does having more skills lead to higher pay?
### 🧮 Method: Power Query (ETL)
#### Extract
I started by importing the original dataset (data_salary_all.xlsx) using Power Query. From there, I created two separate queries:
- 🗃️ One that stores general information about each data job.
- 🔧 Another that organizes the listed skills by job ID.
#### Transform
Next, I cleaned things up by adjusting column types, removing unnecessary fields, tidying up text (like getting rid of filler words), and trimming extra spaces to ensure everything was neat and ready to go.
#### Load
After the cleanup, I loaded both refined datasets back into the workbook—laying the groundwork for the analysis stage.

### 📊 Key Findings

<img width="495" height="246" alt="EXCEL_OhT9d0BhfS" src="https://github.com/user-attachments/assets/68eba77d-a8cb-4ceb-a73b-1bdec9a5fc71" />

- 📈 There's a noticeable trend: jobs that demand more skills tend to come with higher median salaries. Roles like Senior Data Engineer or Data Scientist clearly reflect this.
- 💼 Meanwhile, positions with fewer required skills—like Business Analyst—often come with lower pay, indicating a clear value in specialization.

### 💭 Final Thoughts
These results show that developing a broader skill set can lead to better compensation. The more tools you bring to the table, the more opportunities open up—especially in the data industry.

## 2️⃣ How do data job salaries compare across regions?
### 🧮 Method: PivotTable & DAX
#### 📈 Pivot Table Setup
- 🧩 I built a PivotTable using the Data Model created with Power Pivot.
- 📌 I placed job_title_short in the Rows and salary_year_avg in the Values.
- 🧠 Then I added a custom measure to get the median salary for jobs located in the United States:
``` DAX
=CALCULATE(
    MEDIAN(data_jobs_all[salary_year_avg]),
    data_jobs_all[job_country] = "United States"
)
```
#### DAX
To calculate the overall median salary, I used:
``` DAX
Median Salary := MEDIAN(data_jobs_all[salary_year_avg])
```
### 📊 Key Findings

<img width="694" height="277" alt="EXCEL_xdmqFwhwpi" src="https://github.com/user-attachments/assets/1c6187bb-0a61-447b-a21d-02a1ca3a1144" />

- 🎯 Roles like Senior Data Engineer and Data Scientist lead with high median salaries in both US and non-US regions — a strong indicator of their continued global value.
- 🌍 There’s a clear salary gap between US and international positions, particularly in tech-heavy roles, likely driven by the density of tech companies in the US.

### 💭 Final Thoughts
Understanding these salary patterns can help both professionals and companies make smarter decisions — whether it’s for career planning, job switching, or negotiating offers based on region-specific benchmarks.

## 3️⃣ What are the most in-demand skills in data-related roles?
### 🧮 Method: Power Pivot
- 🛠️ I built a data model by combining data_jobs_all and data_jobs_skills into a single, integrated model.
- 🧼 The data had already been cleaned in Power Query, allowing Power Pivot to establish relationships seamlessly.
- 🔗 A relationship was created using the job_id field to link the two tables.
#### 🧭 Power Pivot Menu
I used the Power Pivot menu to fine-tune the model and easily set up measures for further analysis.

### 📊 Key Findings

<img width="386" height="214" alt="EXCEL_oibF4CeSL7" src="https://github.com/user-attachments/assets/b86b9f51-1991-4cc8-9e17-aac4ca209e19" />

- 🌐 SQL and Python emerged as the most common skills among data professionals, reaffirming their essential role in the data field.
- ☁️ Skills like AWS and Azure are also on the rise, highlighting the growing emphasis on cloud platforms and big data solutions.

### 💭 Final Thoughts
Keeping up with in-demand skills helps professionals stay relevant in a fast-evolving field — and helps training programs stay aligned with what the market truly needs.

## 4️⃣ Which top skills are linked to the highest salaries?
### 🧮 Method: Advanced Chart (Pivot Chart)
#### 📈 Combo PivotChart
I built a combo chart to show how salary compares to skill popularity:
- 🪙 Primary Axis: Median Salary (Clustered Columns)
- 📉 Secondary Axis: Skill Likelihood (%) (Line with Diamond Markers)
To keep things clear, I cleaned up the design — added labels, removed unnecessary lines, and styled the markers.

### 📊 Key Findings

<img width="348" height="215" alt="EXCEL_TTxbZ4chWQ" src="https://github.com/user-attachments/assets/7718414e-384a-4dbd-b973-c55de6c312b7" />

- 🐍 Python, Oracle, and SQL stand out with higher median salaries — signaling their demand in top-paying tech jobs.
- 🧾 Tools like PowerPoint and Word show lower salaries and usage, hinting they’re less valuable for high-salary roles.

### 💭 Final Thoughts
If you're aiming for better pay, upskilling in high-impact tools like Python or SQL can make a big difference. This chart reinforces the value of learning in-demand, tech-forward skills.

## ✅ Conclusion
As someone passionate about data, this project gave me a hands-on way to explore the data job market. Using real job postings, I analyzed trends in salary, region, and skills — all in Excel. With the help of tools like Power Query, PivotTables, Power Pivot, and visualization features, I uncovered key links between top-paying jobs and in-demand skills like Python, SQL, and cloud platforms.

🔍 I hope this project offers helpful insights and a fresh perspective — whether you're into data, job hunting, or exploring what Excel can do.
