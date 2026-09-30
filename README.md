# Automated Data Cleaning & Analytics Engine 🧹

A clean, modular, and reusable data preprocessing engine implemented in Python using Object-Oriented Programming (OOP) paradigms.

---

## 📌 Project Overview
Manual data preprocessing can be fragmented and error-prone. This project packages the core data preparation cycle into three isolated, highly maintainable classes:
- **`DataLoader`**: Safely loads datasets from CSV files with built-in exception handling.
- **`DataCleaner`**: Automatically removes duplicates and imputes missing values based on data types (numeric vs categorical).
- **`DataReporter`**: Generates high-level data health reports and summary statistics.

---

## 🚀 Architecture & Key Features

### 1. `DataLoader`
- Handles file ingestion with `try-except` blocks to prevent pipeline crashes during I/O failures.

### 2. `DataCleaner`
- **Duplicate Removal:** Identifies and drops duplicate records.
- **Smart Imputation:**
  - **Numerical Columns:** Automatically computes and imputes missing values using column **Median**.
  - **Categorical Columns:** Handles missing values by imputing with `'Unknown'`.

### 3. `DataReporter`
- Generates a **Data Health Report** containing:
  - Total row counts
  - Missing value audits per column
  - Descriptive summary statistics (`.describe()`)

---

## 🛠️ Tech Stack
- **Language:** Python
- **Core Libraries:** Pandas, NumPy
- **Environment:** Jupyter Notebook

---

## 💻 Code Structure & Usage Example

```python
import numpy as np
import pandas as pd

# 1. Load Data
loader = DataLoader("sample_unclean_data.csv")
df = loader.load_csv()

# 2. Clean Data
cleaner = DataCleaner(df)
cleaner.remove_duplicates()
clean_df = cleaner.handle_missing_values()

# 3. Generate Summary Report
reporter = DataReporter(clean_df)
reporter.generate_summary()
