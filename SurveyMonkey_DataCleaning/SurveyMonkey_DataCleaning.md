Project Documentation: Data Cleaning for Visualizations in BI Tools

Objective:
The purpose of this project is to prepare the dataset for effective visualization in Business Intelligence (BI) tools.
The focus is on obtaining insights by analyzing the number of respondents per question and identifying instances where respondents provided the same answer for a given question.


Data Cleaning Steps:

1. Importing Dataset
Imported the dataset for analysis.

2. Creating a Backup
Created a copy of the original dataset as a precautionary measure to facilitate a revert back to the initial state if necessary.

3. Dropping Unnecessary Columns
Identified and removed columns deemed unnecessary for the visualization analysis.

4. Unpivoting Dataframe
Transformed the dataset from a wide format to a long format using the melting/unpivoting technique.

5. Calculating Respondents per Question
Created a separate column containing the questions to facilitate analysis on a per-question basis.
Determined the number of respondents for each question.

6. Calculating Answers per Question
Identified the number of respondents who provided the same answer for a specific question.
Filled NaN values in the "Same Answer" column with 0 to facilitate further analysis.

7. Renaming Column Headers
Modified column headers for clarity and consistency.

8. Combining Division Columns
Combined "Division Primary" and "Division Secondary" columns for a more comprehensive view.

9. Cross-Checking Data
Ensured data integrity by cross-checking specific scenarios, such as two people answering as "other(specify)" being equal to 2.
Verified that the total number of questions and subquestions equaled 86.

10. Exporting Cleaned Data
Exported the cleaned dataset to an Excel file for utilization in BI tools.


Summary:
The dataset has undergone a comprehensive cleaning process to ensure its suitability for visualization in BI tools. The steps taken include importing the dataset,
creating a backup, dropping unnecessary columns, unpivoting the dataframe, calculating respondents and answers per question, renaming column headers, combining division columns,
and cross-checking data integrity. The cleaned dataset is now ready for further analysis and visualization.




