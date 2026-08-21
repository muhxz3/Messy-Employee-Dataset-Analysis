# Employee Dataset Analysis & Data Cleaning

## 📌 Overview

This project focuses on **cleaning and analyzing a messy employee dataset using Python and Pandas**.

The dataset contains information about employees, including their department, job title, age, gender, salary, experience, joining date, city, performance score, and work mode.

The notebook demonstrates common **data cleaning and exploratory analysis techniques** that are useful when working with real-world datasets.

## 📊 Dataset

The dataset contains **157 rows and 12 columns**.

### Columns

| Column              | Description                                    |
| ------------------- | ---------------------------------------------- |
| `Employee_ID`       | Unique identifier of an employee               |
| `Employee_Name`     | Name of the employee                           |
| `Department`        | Employee's department                          |
| `Job_Title`         | Employee's job title                           |
| `Age`               | Employee's age                                 |
| `Gender`            | Employee's gender                              |
| `Annual_Salary`     | Annual salary of the employee                  |
| `Experience_Years`  | Years of professional experience               |
| `Joining_Date`      | Date the employee joined                       |
| `City`              | Employee's city                                |
| `Performance_Score` | Employee performance score                     |
| `Work_Mode`         | Working mode such as Remote, Office, or Hybrid |

The notebook initially loads the dataset using:

```python
import pandas as pd

data = pd.read_csv("Day11_Messy_Company_Employee_Dataset.csv")
```

## 🧹 Data Cleaning

The dataset contains several data-quality issues that need to be identified and corrected.

### Missing Values

Missing values are identified using:

```python
data.isna()
```

Missing values occur in columns such as `Department`, `Experience_Years`, and `City`.

### Inconsistent Categorical Values

Some categorical columns contain values with different capitalization even though they represent the same category.

For example:

```text
Male
MALE

Female
female
```

These values can be standardized using Pandas:

```python
data.loc[data["Gender"] == "female", "Gender"] = "Female"
data.loc[data["Gender"] == "MALE", "Gender"] = "Male"
```

Similarly, inconsistent department and city names can be standardized.

For example:

```python
data.loc[data["Department"] == "ENGINEERING", "Department"] = "Engineering"
data.loc[data["Department"] == "engineering", "Department"] = "Engineering"
```

Whitespace can also be removed using:

```python
data["City"] = data["City"].str.strip()
```

## 📈 Data Analysis

After cleaning the dataset, Pandas can be used to analyze the employee data.

### Value Counts

The distribution of employees across cities can be obtained using:

```python
data["City"].value_counts()
```

Similar analysis can be performed for:

```python
data["Gender"].value_counts()
data["Department"].value_counts()
data["Work_Mode"].value_counts()
```









The cleaned dataset can subsequently be used for more advanced statistical analysis, visualization, or machine-learning applications.

