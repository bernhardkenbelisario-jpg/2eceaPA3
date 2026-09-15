## Intended Learning Outcomes

* **Load Data:** Read structured CSV datasets into a Pandas DataFrame without altering original files.
* **Positional & Label Indexing:** Extract subsets of rows and columns using `.iloc[]` and label array indexing.
* **Boolean Filtering:** Search and query specific records based on column conditions using conditional statements and `.isin()`.
* **Data Subset Extraction:** Generate targeted DataFrames while preserving source data integrity and row order.

## Dataset Overview

The dataset used is `cars.csv` (based on the classic `mtcars` dataset), which contains 32 rows and 12 attributes describing automobile specifications.

| Key Columns | Description |
| --- | --- |
| `Model` | Car make and model name |
| `mpg` | Miles per US gallon |
| `cyl` | Number of cylinders |
| `hp` | Gross horsepower |
| `wt` | Weight (1000 lbs) |
| `gear` | Number of forward gears |

## Code Breakdown & Solutions

### A. Positional and Label-Based Slicing

Demonstrates how to inspect dataset dimensions and perform combination slicing using `.iloc[]` for row indices and column labels for feature selection.

import pandas as pd

# Load dataset
cars = pd.read_csv('cars.csv')

# 1. Display DataFrame shape and column list
print("Shape of cars DataFrame:", cars.shape)
print("Column names:", cars.columns)

# 2. Slice rows 6 through 10 (1-based index) using positional slicing (.iloc)
cars6to10 = cars.iloc[6:11]

# 3. Display selected columns using label indexing
display(cars6to10[['Model', 'mpg', 'cyl', 'hp', 'gear']])

### B. Model Lookup

Uses Boolean indexing to locate specific rows by values in the `Model` column without relying on hard-coded row positions.

```python
# 1. Complete record lookup for Toyota Corolla
toyota = cars[cars['Model'] == 'Toyota Corolla']
display(toyota)

# 2. Specific feature lookup for Pontiac Firebird using .loc[]
pontiac = cars.loc[cars['Model'] == 'Pontiac Firebird', ['Model', 'mpg', 'hp', 'wt']]
display(pontiac)

```

---

### C. Multi-Model Subsetting

Extracts a targeted subset containing multiple car models and a specific subset of features using `.isin()` conditional logic.

```python
# Define target models and required columns
models = ['Datsun 710', 'Lotus Europa', 'Ferrari Dino']
cols = ['Model', 'mpg', 'cyl', 'hp', 'gear']

# Filter DataFrame by model list and column subset
selected_cars = cars.loc[cars['Model'].isin(models), cols]

# Display results and verify dimensions (Expected shape: 3, 5)
display(selected_cars)
print("Shape of selected_cars:", selected_cars.shape)

```

---

## Requirements

* Python 3.x
* Pandas
* Jupyter Notebook / JupyterLab

## How to Run

1. Clone this repository.
2. Ensure `cars.csv` is located in the working directory (or specify the local file path).
3. Open `solution.ipynb` in Jupyter Notebook and execute all cells sequentially.
