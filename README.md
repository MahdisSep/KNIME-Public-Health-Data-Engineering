# Public Health Data Engineering & Analysis using KNIME

## 🌟 Project Overview

This project was completed as part of a **Data Engineering Internship**. The goal was to design and implement robust **ETL (Extract, Transform, Load)** pipelines to analyze complex public health datasets (including test results and travel information) and answer critical analytical questions.

The project highlights proficiency in **visual programming for data science** using **KNIME Analytics Platform**, focusing on data preparation, transformation logic, and generating actionable insights from real-world data.

## 🛠️ Technology Stack

| Category | Technology | Purpose |
| :--- | :--- | :--- |
| **Data Workflow** | **KNIME Analytics Platform** | Core tool for building visual ETL and analysis workflows. |
| **Methodology** | **ETL / Data Cleansing / Feature Engineering** | Implementing data pipeline logic. |
| **Data Storage** | **CSV / Excel** (Used for input/output) | Handling structured data formats. |
| **Documentation** | **MS Word (Report)** | Documenting the step-by-step analytical process. |

## 📊 Analytical Tasks and Workflow Breakdown

The project was divided into three main analytical tasks, each requiring a sophisticated KNIME workflow.

### 1\. Identifying Infection Peaks

**Workflow File:** `first,second_question.knwf` (Contains Q1 logic)

  * **Goal:** Determine the three days with the highest number of reported cases.
  * **Key Transformations:**
      * Data loading and initial cleansing of the `test results` dataset.
      * **Group By** node to aggregate the count of positive cases by date (`Count(کدملی شخص)` by `تاریخ آزمایش`).
      * **Sorter** node to rank the days by the case count.
      * Visualization using a **Bar Chart** node to display the peaks.

### 2\. Tracing Asymptomatic Travelers

**Workflow File:** `first,second_question.knwf` (Contains Q2 logic)

  * **Goal:** Trace individuals who traveled from the UK in the latter half of the year, tested negative on arrival, but tested positive within 5 days later.
  * **Key Transformations (Complex Cohort Analysis):**
      * **Filtering:** Applied **Rule-based Row Filter** to isolate travelers from the UK during the specified period (Second half of 1399/2020).
      * **Joining:** Used a **Joiner** node to link the travel data with the test results based on national ID (`کدملی شخص`).
      * **Date & Time Manipulation:** Calculated the difference between the first negative test date (on arrival) and the subsequent positive test date using a **Date/Time Difference** node.
      * **Cohort Isolation:** Filtered the final dataset to include only records where the re-test time difference was less than or equal to 5 days, identifying potential asymptomatic carriers.

### 3\. Geographical Infection Distribution

**Workflow File:** `third_question.knwf`

  * **Goal:** Analyze the geographical distribution of positive cases during a specific month (Bahman 1399 / Jan-Feb 2021).
  * **Key Transformations:**
      * **Filtering:** Filtered data for positive results specifically in the month of Bahman 1399.
      * **Aggregation:** Grouped the data by the city of testing (`شهر آزمایش`) and counted the number of positive cases in each city (`Count(کدملی شخص)`).
      * **Ranking:** Identified the **three cities with the highest and lowest infection counts**.
      * **Visualization:** Generated a **Bar Chart** to visually compare the provincial infection rates.

## 📁 Repository Structure

```
.
├── first,second_question.knwf   # KNIME workflow for analytical questions 1 and 2.
├── third_question.knwf          # KNIME workflow for analytical question 3.
├── output11.xlsx - default_1.csv # Sample output (e.g., Peak Counts per Day).
├── output2.xlsx - default_1.csv  # Sample output (e.g., UK Traveler Cohort).
├── output3.xlsx - default_1.csv  # Sample output (e.g., City Case Counts).
```

## 💡 Demonstrated Skills

This project showcases core skills essential for a Data Engineer:

  * **Data Acquisition and Cleansing:** Handling diverse datasets and preparing them for analysis.
  * **Complex Transformation Logic:** Implementing conditional filtering, joins across multiple tables, and date calculations.
  * **Workflow Automation:** Building reusable and traceable pipelines using KNIME's visual interface.
  * **Analytical Insight Generation:** Translating business/public health questions into quantifiable results.