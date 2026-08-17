# scania-aps-data-cleaning
Data cleaning and preprocessing of industrial APS operational data from Scania trucks

# Scania APS Failure Data Cleaning

## Project overview

This project performs data cleaning and preprocessing on industrial
operational data collected from heavy Scania trucks.

The system under investigation is the Air Pressure System (APS), which
provides pressurized air for functions such as braking and gear changing.

## Dataset source

The original dataset was downloaded from the UCI Machine Learning Repository:

https://archive.ics.uci.edu/dataset/421/aps+failure+at+scania+trucks

The raw dataset was preserved without modification in:

`data/raw/aps_failure_training_set.csv.zip`

## Dataset dimensions before preprocessing

- Rows: 60,000
- Columns: 171

## Problems identified

- Missing values represented by `na`
- Features containing excessive missing data
- Potential duplicate records
- Constant or non-informative columns
- Extreme numerical values and outliers
- Categorical target labels represented as `neg` and `pos`
- Numerical features with substantially different scales
- Anonymized column names

## Preprocessing techniques

1. Standardized column-name formatting
2. Converted operational features to numerical data types
3. Detected and removed exact duplicate rows
4. Removed features containing more than 40% missing values
5. Removed constant features
6. Filled remaining missing numerical values using the median
7. Encoded `neg` as 0 and `pos` as 1
8. Detected outliers using the IQR method
9. Treated extreme values using IQR capping
10. Standardized numerical features using StandardScaler
11. Performed final checks for missing values, duplicates, and data types

## Dataset dimensions after preprocessing

- Rows: [COPY FINAL ROW COUNT FROM cleaning_summary.csv]
- Columns: [COPY FINAL COLUMN COUNT FROM cleaning_summary.csv]

## Repository structure

- `data/raw/aps_failure_training_set.csv.zip`: original dataset
- `data/cleaned/aps_failure_cleaned.csv.gz`: cleaned dataset and preprocessing parameters
- `Scania_APS_Data_Cleaning.ipynb`: complete preprocessing code
- `requirements.txt`: required Python libraries

## Final cleaned dataset

The final cleaned dataset is available as:

`data/cleaned/aps_failure_cleaned.csv.gz`

The file is compressed because the uncompressed CSV is large. It can be
loaded directly with pandas:

```python
import pandas as pd

df = pd.read_csv(
    "data/cleaned/aps_failure_cleaned.csv.gz",
    compression="gzip"
)
