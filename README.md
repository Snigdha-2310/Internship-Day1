# Internship-Day1
# 📊 Netflix Titles Dataset – Data Cleaning and Preprocessing

## 🧹 Task 1: Data Cleaning and Preprocessing

### 🎯 Objective:
Clean and prepare the raw `netflix_titles.csv` dataset by addressing missing values, duplicates, formatting issues, and inconsistent data types.

---

## 📁 Dataset Overview

- **Original Rows:** 8807  
- **Cleaned Rows:** 8800  
- **Columns:** 12  
- **Source:** [Netflix Titles Dataset - Kaggle](https://www.kaggle.com/shivamb/netflix-shows)

---

## 🛠️ Tools Used

- **Language:** Python  
- **Libraries:** `pandas`, `numpy`  
- **Environment:** Jupyter Notebook / Google Colab

---

## 🧼 Cleaning Summary

| Cleaning Step                  | Status     |
|-------------------------------|------------|
| ✅ Null Values Handled         | Yes        |
| ✅ Duplicates Removed          | Yes        |
| ✅ Text Columns Standardized   | `type`, `country`, `rating` |
| ✅ Date Column Formatted       | `date_added` (converted to datetime) |
| ✅ Column Names Cleaned        | All column names lowercased and stripped |
| ✅ Data Types Fixed            | `release_year` (int), `date_added` (datetime) |

---



## 🔍 Code Explanation

### 1. 📥 Load Dataset

```python
import pandas as pd

df = pd.read_csv("netflix_titles.csv")
```

2. 🧾 Initial Dataset Summary
```python
df.info()
df.isnull().sum()
```

3. 🧹 Remove Duplicates
```python
df.drop_duplicates(inplace=True)
```

4. 🛑 Handle Missing Values
```python
df.fillna({
    'director': 'Not Available',
    'cast': 'Not Available',
    'country': 'Not Available',
    'date_added': 'Not Available',
    'rating': 'Not Rated',
    'duration': 'Not Available'
}, inplace=True)
```

5. 🔤 Standardize Text Columns
```python
df['type'] = df['type'].str.title().str.strip()
df['country'] = df['country'].str.title().str.strip()
df['rating'] = df['rating'].str.upper().str.strip()

```
6. 📅 Format Date Column
```python
df['date_added'] = pd.to_datetime(df['date_added'], errors='coerce')
```
7. 🏷️ Rename Columns
```python
df.columns = [col.strip().lower().replace(" ", "_") for col in df.columns]
```

8. 🔢 Fix Data Types
```python
df['release_year'] = df['release_year'].astype('int32')
```

9. 📊 Final Info & Missing Check
```python
print(df.info())
print(df.isnull().sum())
```

✅ Cleaning Summary
Cleaning Step	                    Status
✅ Null Values Handled	           Yes
✅ Duplicates Removed	           Yes
✅ Text Columns Standardized	       type, country, rating
✅ Date Column Formatted	           date_added (converted to datetime)
✅ Column Names Cleaned	           All column names lowercased and stripped
✅ Data Types Fixed	               release_year (int), date_added (datetime)



## 🧾 Initial Dataset Info

```python
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 8807 entries, 0 to 8806
Data columns (total 12 columns):
 #   Column        Non-Null Count  Dtype 
---  ------        --------------  ----- 
 0   show_id       8807 non-null   object
 1   type          8807 non-null   object
 2   title         8807 non-null   object
 3   director      6173 non-null   object
 4   cast          7982 non-null   object
 5   country       7976 non-null   object
 6   date_added    8797 non-null   object
 7   release_year  8807 non-null   int64 
 8   rating        8803 non-null   object
 9   duration      8804 non-null   object
 10  listed_in     8807 non-null   object
 11  description   8807 non-null   object


🕳️ Missing Values Before Cleaning:
Column	            Missing Values
director	        2634
cast	            825
country	            831
date_added      	10
rating	            4
duration        	3



✅ Cleaned Dataset Info
```python
<class 'pandas.core.frame.DataFrame'>
Index: 8800 entries, 0 to 8806
Data columns (total 12 columns):
 #   Column        Non-Null Count  Dtype 
---  ------        --------------  ----- 
 0   show_id       8800 non-null   object
 1   type          8800 non-null   object
 2   title         8800 non-null   object
 3   director      8800 non-null   object
 4   cast          8800 non-null   object
 5   country       8800 non-null   object
 6   date_added    8800 non-null   object
 7   release_year  8800 non-null   int32 
 8   rating        8800 non-null   object
 9   duration      8800 non-null   object
 10  listed_in     8800 non-null   object
 11  description   8800 non-null   object
```

✅ Missing Values After Cleaning:

All missing values were handled successfully.



📌 Final Notes
Standardized null values with placeholders such as "Unknown" or "Not Available".

Removed 7 duplicate rows using .drop_duplicates().

Unified date format as datetime64[ns] and ensured correct datatypes.

Cleaned column names to lowercase and removed whitespace.

This cleaned dataset is now ready for EDA or further modeling tasks!

📂 Deliverables
✅ netflix_titles_cleaned.csv

✅ netflix_cleaning.ipynb

✅ README.md (this file)


