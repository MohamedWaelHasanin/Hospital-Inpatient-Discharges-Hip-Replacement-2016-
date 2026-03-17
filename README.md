# Power BI Hospital Discharges: Hip Replacement Analysis

## Project Overview
This project is an end-to-end Power BI analytical solution focused on hospital inpatient discharges for total and partial hip replacements. It demonstrates the complete business intelligence workflow: ingesting data directly from the web, cleaning and categorizing the data in Power Query, building robust DAX measures for benchmarking, and designing a highly interactive, multi-page dashboard.

The primary goal of this dashboard is to provide clear, actionable insights into hospital performance, cost efficiency, and patient length of stay (LOS), allowing stakeholders to compare individual facilities against overall benchmarks.

## Data Source & ETL Process
The data is sourced directly from a Web CSV file (DataCamp Hospital Inpatient Discharges dataset) using Power Query's `Web.Contents`. 

**Transformations Applied:**
* **Data Cleaning:** Promoted headers and assigned accurate data types for numerical analysis and date/text processing.
* **Targeted Filtering:** Filtered the `ccs_procedure_description` strictly to `"HIP REPLACEMENT,TOT/PRT"` to maintain focus on the specific procedure.
* **Conditional Segmentation:** Created an **Age Bins** calculated column using logical grouping:
  * `"Age 50+"` (for age groups 50 to 69, or 70+)
  * `"Age <50"` (for all other age groups)

## Data Modeling & Core DAX Measures
To facilitate the analytical requirements, several key performance indicators (KPIs) and benchmark metrics were developed using Data Analysis Expressions (DAX):

* **Volume Metrics:** * *Total Discharges* (Count of records)
  * *Total Surgeons* (Distinct count of surgeon license numbers)
  * *Total Hospitals* (Distinct count of facility IDs)
*
