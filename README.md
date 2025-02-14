This project processes employee data stored in a CSV file and performs a series of analyses. The analyses include checking for missing values, detecting duplicate entries, identifying outliers in salary data, calculating average salary, finding the highest salary, counting employees per department, and identifying the employee with the highest salary. All results are saved in a new file named results.txt.

How to Run the Code:

Prerequisites:
1. Python 3.x must be installed on your machine.
2. The project requires an input CSV file (emp_data_v2.csv), which should be structured with at least the following columns:
Employee Name (Column 2, index 1)
Department (Column 3, index 2)
Salary (Column 4, index 3)
4. The results will be written to a new text file called results.txt.

Steps to Run the Code:
1. Clone or download the repository to your local machine.
2. Ensure the emp_data_v2.csv file is available in the same directory as the Python script, or adjust the file path in the script.
3. Open a terminal and navigate to the project directory.
4. Run the script with the following command:  python employee_data_analysis.py
5. After running the script, check the results.txt file for the generated results.

Assumptions:
1. CSV File Format:
The CSV file has a header row, and data starts from the second row (index 1).
Employee Name is in column 2 (index 1).
Salary is in column 4 (index 3).
Department is in column 3 (index 2).
Missing or empty salary values are excluded from calculations, and they are not treated as valid data.
2. Numerical Columns:
The salary column is assumed to contain valid numeric data or be empty. Non-numeric values are ignored during calculations.
3. Outlier Detection:
Outliers are identified using the Interquartile Range (IQR) method, where values below Q1 - 1.5IQR or above Q3 + 1.5IQR are considered outliers.

Design Decisions
1. Data Structures:
I used a list to store all rows from the CSV file (data), which makes it easy to access and process each row.
A dictionary (department_count) is used to count the number of employees in each department, as dictionaries provide an efficient way to store and update counts.
2. Processing Approach:
The script processes the data without any external libraries like pandas or numpy, which keeps the code simple and beginner-friendly.
The steps are broken down into logical chunks, and each step is performed independently:
-Missing Values: Checked row by row.
-Duplicates: Checked by storing previously seen rows in a set.
-Outliers: Checked using IQR for salary data.
-Average Salary: Calculated by summing up valid salary values and dividing by the count.
-Highest Salary: Determined by finding the maximum salary in the dataset.
-Department Counts: Counted by iterating through each employee's department.
3. Output:
The results are written to results.txt for persistence and easy review.

Challenges and How They Were Resolved:
1. Handling Missing or Invalid Data:
Challenge: The presence of missing or non-numeric data could interfere with calculations like average salary, highest salary, and outlier detection.
Resolution: I implemented checks to ensure that only valid data is processed. If salary data is missing or invalid, it's skipped during calculations, and outlier detection only uses valid numbers.
2. Outlier Detection:
Challenge: Implementing the IQR method manually without relying on libraries like pandas or numpy.
Resolution: I sorted the salary values, calculated Q1 and Q3, and computed the IQR to identify outliers. This was done with basic Python built-in methods like sorted() and simple list slicing.
3. Efficiency in Large Datasets:
Challenge: The program needed to be efficient while processing large datasets.
Resolution: I kept the program simple by using basic Python data structures (lists and dictionaries) and processed the data in one pass for each task, ensuring the code could scale with reasonably large datasets without consuming excessive memory.
4. Writing Results to File:
Challenge: Writing formatted results to a text file required handling string formatting and ensuring correct output.
Resolution: I accumulated results in a list and used the writelines() method to write them to results.txt. This ensured the file was generated correctly with the desired results.
