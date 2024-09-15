# Mississauga Parking Tickets Analysis (2016-2023)

## Overview

This project is a comprehensive case study analyzing public parking tickets issued in Mississauga, Canada, from 2016 to 2023. The dataset consists of 8 CSV files, each representing one year of data, and has been consolidated into a single SQLite database for ease of analysis. The purpose of this case study is to identify patterns, trends, and insights that could inform policy decisions, improve enforcement strategies, and potentially guide urban planning efforts.

## Dataset Overview

### Source

The data was collected from public records available from the [City of Mississauga](https://data.mississauga.ca/search?q=parking), covering parking tickets issued between 2016 and 2023.

### Structure

The dataset consists of the following fields:

- **VIODESCRIPTION/VOIDESCRIPTION**: Description of the parking violation.
- **LOCATIONDESC1**: Location where the violation occurred.
- **ISSUEDATE**: Date the parking ticket was issued.
- **ISSUETIME**: Time the parking ticket was issued.
- **ObjectId/FID**: A unique identifier for each record in the dataset. This field serves as a primary key, ensuring that each parking violation entry can be uniquely identified and referenced. The `ObjectId/FID` values are sequential integers, which also suggest the order in which the records were entered or generated.

## Data Cleaning and Transformation

### Objectives of Data Cleaning and Transformation

The primary objectives of the data cleaning and transformation process were:

1. **Ensure Data Consistency:** Correct any inconsistencies in the dataset, such as misspelled column names, mixed-case text, and varying date and time formats.
2. **Remove Unnecessary Data:** Drop columns and rows that were not relevant to the analysis, such as redundant index columns or rows with irreparable misalignment.
3. **Handle Missing and Misaligned Data:** Identify and address any missing or misaligned data to ensure the dataset was complete and reliable for analysis.
4. **Standardize Data Formats:** Ensure that all date and time values were in a consistent format across the dataset to facilitate accurate analysis.
5. **Prepare for Analysis:** Transform the data into a structure that was ready for analysis, including renaming columns for clarity and converting text to a uniform case.

### Problems Encountered

During the data cleaning and transformation process, several issues were identified:

- **Column Name Misspelling:** The column "VIODESCRIPTION" was misspelled as "VOIDESCRIPTION" in some datasets.
- **Date and Time Formatting:** The date and time columns required standardization across the datasets.
- **Inconsistent Formatting:** The "violation_description" column contained text in both uppercase and sentence case formats, and time formats were not uniform.
- **Unnecessary Columns:** Index columns such as `ObjectId` and `FID` needed to be dropped.
- **Misaligned Data:** A total of approximately 171,000 rows were affected due to misaligned data entry errors. These issues resulted from inconsistent formatting and errors in the dataset.
- **Handling Missing Data:** Missing data in key columns further compounded the challenges, leading to a reduction in the usable data.

Overall, these issues affected approximately 171,000 rows out of the total 1,316,052 rows, representing roughly 13% of the dataset.

### Thought Process for Fixing Misaligned and Missing Data

When deciding how to handle the misaligned and missing data, I considered the following factors:

- **Data Preservation:** Given the size of the dataset, removing all rows with issues would have led to a substantial loss of data (approximately 13%). I aimed to preserve as much data as possible to maintain the dataset's richness and ensure comprehensive analysis.

- **Impact on Analysis:** I evaluated the impact that misaligned and missing data could have on the integrity of the analysis. Misaligned data, if left unaddressed, could lead to incorrect conclusions, while missing data could skew results or reduce the statistical power of the analysis.

- **Feasibility of Correction:** I determined that many of the misaligned and missing data issues had a pattern and could be corrected through programmatic solutions, such as imputing missing values based on existing data patterns. This approach allowed for the retention of valuable data without compromising the analysis.

- **Consistency and Reliability:** Ensuring consistency across the dataset was a priority. By addressing misaligned and missing data, I aimed to produce a dataset that was both reliable and easy to work with, reducing the likelihood of errors in subsequent analysis.

Given these considerations, I decided to focus on fixing the misaligned and missing data wherever possible rather than removing affected rows entirely. This approach struck a balance between data quality and data retention.

### Steps Taken to Remediate

To address the issues identified, the following steps were taken:

- **Corrected Column Names:** Fixed the misspelled column name "VOIDESCRIPTION" to "VIODESCRIPTION" and ensured consistent naming across all datasets.
- **Standardized Text Formatting:** Converted all text in the "violation_description" column to uppercase for consistency.
- **Unified Time Formats:** Standardized all time entries to a consistent format (e.g., HH:MM:SS).
- **Standardized Date and Time:** Ensured that all dates and times were formatted consistently throughout the dataset.
- **Dropped Unnecessary Columns:** Removed unnecessary index columns like `ObjectId` and `FID`.
- **Fixed Misaligned Rows:** Applied custom code to correct misaligned rows, recovering 1,090 rows and reducing data loss.
- **Corrected Misaligned Rows:** Custom scripts were developed to identify and correct misaligned rows wherever possible, successfully recovering ~1100 rows of the affected data.
- **Managed Missing Data:** Implemented strategies to handle missing data, ensuring the dataset's completeness and reliability. Specifically:
  - **Time Imputation:** If the `issue_time` field was missing, the missing time was imputed using the nearest row with the same `issue_date`. This approach leveraged the assumption that violations on the same date would likely occur around similar times.
  - **Date Imputation:** If the `issue_date` was missing, the missing date was imputed using the date from the top row, ensuring that the chronological order of entries was preserved.
  - **Location Imputation:** If the `locationdesc1` field was missing, "NO ADDRESS" was added to indicate that no location information was available.
  - **Row Removal:** In cases where neither imputation nor correction was feasible, incomplete rows were removed to maintain the dataset's integrity.

### Results

As a result of the data cleaning and transformation efforts:

- **Dataset Integrity:** Despite the significant challenges posed by misaligned and missing data, the majority of the dataset was preserved. Through a combination of programmatic and manual efforts, I was able to save ~99.99% of the original data.
- **Successful Recovery:** Through programtic and manual efforts I was able to save most of the 171,000 rows.
- **Comprehensive Dataset:** The final dataset, comprising 1,316,050 rows out of 1,316,052 rows, is both comprehensive and reliable, ready for in-depth analysis. The programmatic and manual interventions ensured that the dataset retained its richness, allowing for robust analysis without significant compromise on data quality.

These results demonstrate the effectiveness of a meticulous and methodical approach to data cleaning, balancing data preservation with the need for accuracy and consistency.

## Analysis and Findings

### Objectives of Analysis

The primary objectives of this case study are:

1. **Identify the most common types of parking violations** across the city.
2. **Analyze temporal patterns** to determine if certain times, days, or months are more prone to parking violations.
3. **Examine location-based trends** to identify hotspots where parking violations frequently occur.
4. **Investigate trends over time** to see how the frequency and type of violations have evolved from 2016 to 2023.

### Methodology

### Key Findings

### Visualizations

## Conclusion

## For the Developers

### Tools Used

## License and Terms of Use

The data used in this project is subject to the terms of use provided by the City of Mississauga. Please review the terms before using the dataset. The terms of service can be found at the following link:

[City of Mississauga Terms of Use](http://www5.mississauga.ca/research_catalogue/CityofMississauga_TermsofUse.pdf)

Alternatively, the terms of service are also included in this repository as a file named `CityofMississauga_TermsofUse.pdf`.
