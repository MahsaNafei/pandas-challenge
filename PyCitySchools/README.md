# PyCity Schools Analysis
The PyCity Schools Analysis provides a thorough analysis of many elements influencing academic achievement in the made-up PyCity school system. This research includes summaries at the district level, school level information, grade level score insights, per-student costs, school size implications, and school type effects. Finding connections between these variables and providing insight into the district's broader educational landscape are the objectives.

## Data Source

The analysis is based on two CSV files:

- `schools_complete.csv`: Contains information about schools in PyCity, including their names, budgets, and types.
- `students_complete.csv`: Contains information about students in PyCity, including their names, grades, and test scores.

## District Summary

### Calculation
- **Total Schools:** Calculated by finding the number of unique school names in the merged dataset (`school_data_complete`).
- **Total Students:** Obtained by summing the "size" column from the `school_data` table, which represents the number of students in each school.
- **Total Budget:** Calculated by summing the "budget" column from the `school_data` table, representing the budget of each school.
- **Average Math Score:** Calculated as the mean of the "math_score" column in the `school_data_complete` table.
- **Average Reading Score:** Calculated as the mean of the "reading_score" column in the `school_data_complete` table.
- **% Passing Math:** Calculated by counting the number of students with math scores greater than or equal to 70 and dividing it by the total number of students.
- **% Passing Reading:** Calculated by counting the number of students with reading scores greater than or equal to 70 and dividing it by the total number of students.
- **% Overall Passing:** Calculated by counting the number of students passing both math and reading (scores >= 70 for both) and dividing it by the total number of students.

### Data Extraction
- The calculations are performed using pandas DataFrame operations on the `school_data_complete` and `school_data` DataFrames.

## School Summary

### Calculation per school
- **School Type:** Extracted from the "type" column of the `school_data` DataFrame.
- **Total Students:** Extracted from the "size" column of the `school_data` DataFrame.
- **Total School Budget:** Extracted from the "budget" column of the `school_data` DataFrame.
- **Per Student Budget:** Calculated by dividing the school budget by the number of students in each school.
- **Average Math Score:** Calculated as the mean of math scores grouped by school.
- **Average Reading Score:** Calculated as the mean of reading scores grouped by school.
- **% Passing Math:** Calculated by counting the number of students passing math (score >= 70) for each school and dividing it by the total number of students in that school.
- **% Passing Reading:** Calculated by counting the number of students passing reading (score >= 70) for each school and dividing it by the total number of students in that school.
- **% Overall Passing:** Calculated by counting the number of students passing both math and reading (scores >= 70 for both) for each school and dividing it by the total number of students in that school.

### Data Extraction
- The calculations are performed using pandas DataFrame operations on the `school_data` and `school_data_complete` DataFrames.

## Highest-Performing and Lowest-Performing Schools

### Data Extraction
- Schools are sorted by `% Overall Passing` in descending order (`top_schools`) and ascending order (`bottom_schools`) using the `sort_values` method on the `per_school_summary` DataFrame.

## Math Scores by Grade

### Calculation
- Separate DataFrames are created for each grade (9th, 10th, 11th, 12th) using boolean indexing based on the "grade" column.
- The average math scores for each grade at each school are calculated using the `groupby` and `mean` functions.

### Data Extraction
- Math scores by grade are stored in the `math_scores_by_grade` DataFrame.

## Reading Scores by Grade

### Calculation
- Separate DataFrames are created for each grade (9th, 10th, 11th, 12th) using boolean indexing based on the "grade" column.
- The average reading scores for each grade at each school are calculated using the `groupby` and `mean` functions.

### Data Extraction
- Reading scores by grade are stored in the `reading_scores_by_grade` DataFrame.

## Scores by School Spending

### Calculation
- Spending ranges are established using the `spending_bins` and `labels`.
- The `per_school_summary` DataFrame is used to categorize schools based on per-student budget and assign them to the corresponding spending range.
- Various metrics, such as average math and reading scores, as well as the percentages of students passing math, reading, and both, are calculated for each spending range using `groupby` and `mean` functions.

### Data Extraction
- Metrics for each spending range are stored in the `spending_summary` DataFrame.

## Scores by School Size

### Calculation
- Schools are categorized into small, medium, and large based on the `size_bins` and `labels`.
- The `per_school_summary` DataFrame is used to categorize schools based on their total student count and assign them to the corresponding size category.
- Metrics such as average math and reading scores, as well as the percentages of students passing math, reading, and both, are calculated for each size category using `groupby` and `mean` functions.

### Data Extraction
- Metrics for each size category are stored in the `size_summary` DataFrame.

## Scores by School Type

### Calculation
- Schools are grouped by type (Charter or District) using the `groupby` function on the `per_school_summary` DataFrame.
- Metrics such as average math and reading scores, as well as the percentages of students passing math, reading, and both, are calculated for each school type using `mean` functions.

### Data Extraction
- Metrics for each school type are stored in the `type_summary` DataFrame.

The analysis results are calculated by applying various data manipulation techniques using the pandas library in Python. The calculations are performed on the provided data tables to derive insightful metrics and summaries about school and student performance in the PyCity school district.

# Instructions

To use this script:

1. Ensure you have the following CSV files in the `Resources` directory:
   - `schools_complete.csv`
   - `students_complete.csv`

2. Run the script using Python.

3. The analysis results will be displayed in the console, including summary tables and key metrics.