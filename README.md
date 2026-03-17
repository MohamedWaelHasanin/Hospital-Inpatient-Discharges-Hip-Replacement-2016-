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
* **Performance Metrics:** * *Average Cost per Discharge* * *Average Length of Stay (LOS)*
* **Benchmarking & Variance Analysis:**
  * Created **Overall Benchmarks** using `CALCULATE` and `ALL()` to ignore active filters and establish a baseline.
  * Computed **Percentage Variance** for both Cost and LOS to evaluate how specific hospitals or segments perform relative to the overall average: `(Current - Overall) / Overall`.

## Dashboard Architecture & Design
The Power BI report is structured into a cohesive, interactive multi-page application prioritizing clean design, logical flow, and effective data storytelling.

### 1. Executive Overview
* **Purpose:** Answers *"What is the overall performance across hospitals?"*
* **Features:** High-level KPI cards, aggregated visual analysis (by year, age group, program size), and interactive slicers for dynamic filtering.

### 2. Hospital Comparison
* **Purpose:** Answers *"How do hospitals perform relative to each other?"*
* **Features:** Comparative charts, segmentation variables (age bins, gender), and variance analysis visuals to highlight facilities performing above or below the overall benchmarks.
* **Interactive Bookmarking:** Utilizes buttons and bookmarks to toggle between analytical perspectives (e.g., swapping visuals to focus on *Financial Performance* vs. *Operational Efficiency*) without cluttering the screen.

### 3. Hospital Profile (Drillthrough)
* **Purpose:** Answers *"What is the detailed performance of a specific hospital?"*
* **Features:** Configured as a Drillthrough destination based on `facility_name`. Features a dynamic title that updates based on the selected hospital, detailed facility-level metrics, and a "Back" button for seamless user navigation.

### Navigation & UX
* Integrated a **Page Navigator** for smooth transitions between the Executive Overview and Hospital Comparison pages.
* Maintained strict design standards including consistent color palettes, typography, and clean alignment to prevent visual clutter.

## Tools Used
* **Power BI Desktop:** Report authoring, dashboard design, and interactive UX (Bookmarks, Drillthrough, Page Navigation).
* **Power Query (M):** Web data extraction and conditional formatting.
* **DAX:** Advanced measure creation, benchmarking, and variance calculations.
