# 💼 Data Nerds Salary Dashboard

![salary_dashboard_gif](https://github.com/user-attachments/assets/935d8982-68df-4ab5-b326-9e7f00ce49f1)

## 🧭 Overview

This dashboard was created to help **job seekers** explore salary trends across various data-related roles. By using key filters such as job title, location, and work type, users can investigate whether they’re being fairly compensated and where the best opportunities lie.

It presents insights on:
- Median salary by role and region  
- Top platforms for job listings  
- Work type distribution across countries  

▶️ **[1_Salary_Dashboard.xlsx](Project%201_Data_Nerds_Salary%20Dashboard.xlsx)** — this is the main file containing the interactive dashboard.

---

## 📄 Dataset Description

The dataset contains job listing data from 2023, including:

- **🧑‍💼 Job Titles** (e.g., Data Analyst, Data Engineer, ML Scientist)  
- **🌍 Job Locations** (countries)  
- **💰 Annual Salaries** in USD  
- **⏱️ Job Schedule Types** (full-time, part-time, etc.)  
- **🌐 Job Posting Platforms** (LinkedIn, Indeed, etc.)

---

## 🛠️ Excel Skills Used

This dashboard uses only **core Excel 365** features—no Power Pivot or Power Query required.

- **📉 Charts**: Bar, map, and column charts to display salaries and distributions  
- **🧮 Formulas & Functions**: `MEDIAN()`, `IF()`, `FILTER()`, `SEARCH()`, etc.  
- **📋 Data Validation**: For filter dropdowns (job title, country, type)

---

## 📊 Dashboard Build Details

### 🔹 Median Salary by Job Title

<img width="299" height="330" alt="EXCEL_WBGwF0LoE9" src="https://github.com/user-attachments/assets/a370c563-72ee-4785-887c-a7e9b7bff455" />

- ⚙️ **Implementation Detail**: Excel bar chart with clean formatting and currency in USD.
- 🖼️ **Visualization Style**: Horizontal layout for easier role comparison at a glance.
- 📂 **Data Sorting**: Job titles were arranged from highest to lowest median salary for instant readability.
- 🧭 **Key Insight**:The chart reveals that *Engineer* and *Senior* roles typically command higher median salaries than *Analyst* positions—especially in tech-focused job markets.

**Formula used**:
```excel
=MEDIAN(
IF(
    (data[job_title_short]=A2)*
    (data[job_country]=country)*
    (ISNUMBER(SEARCH(type,data[job_schedule_type])))* 
    (data[salary_year_avg]<>0),
    data[salary_year_avg]
)
)
```
- 🧩 **Filter Logic**: Filters based on job title, country, schedule type keyword, and excludes zero salaries.
- 🧮 **Formula Mechanics**: Leverages MEDIAN() and IF() in an array formula to evaluate matching entries only.
- 📌 **Focused Result**: Outputs salary insights specific to your selected job role, location, and work schedule.
- 📥 **Use Case**: Feeds the summary table with dynamic median salary data using custom inputs.

### 🔹 Median Salary by Country

<img width="280" height="333" alt="EXCEL_8RWvC2eadY" src="https://github.com/user-attachments/assets/5bd549e5-6529-4a4a-b7a2-3d1e36bd550a" />

- ⚙️ **Implementation Detail**: Excel filled map chart using country-level median salary data, formatted in USD.
- 🖼️ **Visualization Style**: Color gradient representing salary levels—darker shades indicate higher median salaries.
- 📂 **Data Sorting**: Country names are cleaned and standardized to match Excel's mapping engine. Missing or ambiguous entries were excluded.
- 🧭 **Key Insight**:Countries like the United States, Sudan, and Germany tend to offer higher median salaries for data roles, making them attractive markets for professionals seeking competitive compensation.

**Formula used**:
```excel
  =MEDIAN(
       IF((data[job_country]=A4)*
          (data[salary_year_avg]<>0)*
          (data[job_title_short]=title)*
          (ISNUMBER(SEARCH(type,data[job_schedule_type]))),
           data[salary_year_avg]
         )
       )
  ```
- 🧩 **Logic**: Calculates median salary using 4 filters — job country, non-zero salary, job title, and schedule type.
- 🧮 **Function**: Array formula combining `IF()` with `MEDIAN()` for conditional calculation.
- 🔎 **Filter Use**: Matches selected dropdown inputs for dynamic output.
- 📊 **Result**: Returns median salary specific to the selected role, country, and job type only.

### 🔹 Top Platform by Country
```excel
=COUNTIFS(
  data[job_via], A2,
  data[job_title_short], title,
  data[job_country], country,
  data[job_schedule_type], type
)
```
- 📌 **Purposes**: Counts how many job listings meet all specified criteria: job source, title, country, and schedule type.
- 🧵 **Output**: Returns the number of matching jobs — ideal for summary tables and conditional insights.
  
### 🔹 Job Type by Median Salary

<img width="298" height="330" alt="EXCEL_YcC5yxVeoc" src="https://github.com/user-attachments/assets/bbbe68cd-68df-4a61-94e8-316cd6321775" />

```excel
=FILTER(J2#,(NOT(ISNUMBER(SEARCH("and",J2#))+ISNUMBER(SEARCH(",",J2#))))*(J2#<>0))
```
- 📌 **Purposes**: Removes multi-type entries (like "Part-time and Freelance") for cleaner analysis.
- 🧵 **Output**: Returns a simplified list of job types — ready for dropdowns or pivot use.

### 🔒 Clean Data Validation

![EXCEL_WgzlWctPrN](https://github.com/user-attachments/assets/64d12523-5faa-4bfe-a7b7-13d8e36aeb22)

- ⚙️ **Data Validation Rule**: Uses the filtered list as a dropdown under Job Title, Country, and Type columns.  
- 🎯 **Purpose**: Restricts input to validated values—minimizing errors and boosting consistency.  
- 🧵 **Output**: Clean, user-friendly inputs that improve overall dashboard usability.

## ✅ Conclusion

This Excel dashboard streamlines salary data analysis through clean formatting, smart filters, and intuitive visuals. With enhanced validation, interactive charts, and job-type cleanup, it ensures clarity, consistency, and actionable insights for data nerds and career analysts alike. It also demonstrates my ability to turn raw data into a structured, insight-driven dashboard — blending logic, usability, and design for effective decision-making.
