# datafun-06-eda
CC6.1: Start a New Project (w/Local Project Virtual Env)

# 📊 Exploratory Data Analysis (EDA) on Seaborn's Exercise Dataset

##  Project Overview
**Author:** Kersha Broussard  
**Date:** February 12, 2025  
**Dataset:** Seaborn's `exercise` dataset  

## 🔍 Purpose of the Project
This project focuses on Exploratory Data Analysis (EDA) using **Python, Pandas, and Seaborn**. The goal is to understand the relationships between different exercise activities, heart rate, and diet.

### **Project Objectives:**
- Load and explore the dataset (shape, structure, and data types)
- Perform initial descriptive analysis (summary statistics, missing values)
- Visualize distributions of numerical and categorical variables
- Examine trends and relationships between key variables
- Transform data and engineer new features where necessary
- Summarize findings with meaningful insights

---
## Setup Instructions
### **1️. Create & Activate a Virtual Environment
Run the following commands in your project directory:

#### On Windows (PowerShell)
```powershell

python -m venv venv
venv\Scripts\activate
```

#### On macOS/Linux
```bash

python3 -m venv venv
source venv/bin/activate
```
##  Getting Started
### **1️. Install Required Libraries**
Ensure you have the required libraries installed. Run the following in your terminal:
```bash
pip install pandas seaborn matplotlib jupyter
```

### **2️. Open Jupyter Notebook**
Launch Jupyter Notebook from your project folder:
```bash
jupyter notebook
```
Open `exercise_eda.ipynb` to follow the analysis.

### **3️. Load the Dataset**
The dataset is loaded directly from Seaborn:
```python
import seaborn as sns
import pandas as pd
import matplotlib.pyplot as plt

# Load dataset
df = sns.load_dataset("exercise")

# Drop unwanted column
df.drop(columns=["Unnamed: 0"], inplace=True)
```

---

##  **Data Exploration & Cleaning**
### **1️. Check Data Structure**
```python
print(df.head(10))  # First 10 rows
print(df.shape)      # Dataset dimensions
print(df.dtypes)     # Column data types
print(df.describe()) # Summary statistics
```

### **2️. Handling Categorical & Numerical Data**
- **Convert time column to numeric:**
```python
df["time_numeric"] = df["time"].str.extract(r"(\d+)").astype(float)
```
- **Rename pulse column for clarity:**
```python
df.rename(columns={"pulse": "heart_rate"}, inplace=True)
```
- **Create a new activity level column:**
```python
df["activity_level"] = df["time_numeric"].apply(lambda x: "Short" if x == 1 else ("Moderate" if x == 15 else "Long"))

```
### **Run the Notebook** 
* Each section contains Markdown explanations and Python code for:

Data loading & cleaning
Descriptive statistics
Data visualization
Key insights & conclusions
To execute, run each cell in order.
---

## 📊 **Visualizations & Insights**
### **1️. Distribution of Exercise Durations**
```python
sns.histplot(df["time_numeric"], bins=3, kde=True)
plt.xlabel("Time (minutes)")
plt.title("Distribution of Exercise Duration")
plt.show()
```

### **2️. Heart Rate Distribution by Exercise Type**
```python
sns.boxplot(x="kind", y="heart_rate", data=df)
plt.title("Heart Rate Distribution by Exercise Type")
plt.xlabel("Exercise Type")
plt.ylabel("Heart Rate (bpm)")
plt.show()
```

### **3️. Heart Rate Trends Over Time by Exercise Type**
```python
plt.figure(figsize=(10,6))
sns.lineplot(x="time_numeric", y="heart_rate", hue="kind", marker="o", data=df)
plt.title("Heart Rate Trend Over Exercise Duration")
plt.xlabel("Exercise Duration (minutes)")
plt.ylabel("Heart Rate")
plt.legend(title="Exercise Type")
plt.show()
```

###  Version Control (Git & GitHub Commands)
**1️.  Initialize Git & Connect to GitHub** 
```bash

git init
git remote add origin https://github.com/kersha0530/exercise-eda.git
```
**2️. Add & Commit Changes**
```bash

git add .
git commit -m "Added EDA notebook, README, and visualizations"
```
**3️. Push Changes to GitHub**
```bash

git push origin main
```

🔗 Verify Your Work on GitHub
1️⃣ Push your changes using the Git commands above
2️⃣ Take a screenshot of your updated repository on GitHub
3️⃣ Provide a clickable link to your GitHub project:
🔗 https://github.com/kersha0530/datafun-06-eda 




---

##  **Key Takeaways:**
- **Heart rate increases** with longer exercise durations.
- **Running** has the highest heart rate on average.
- **People on a low-fat diet** tend to have a slightly lower heart rate during exercise.

### **Why This Matters?**
Understanding exercise trends helps in making better fitness and health decisions. This analysis can assist in:
- Identifying patterns in heart rate during exercises.
- Observing the impact of diet on exercise performance.
- Understanding activity levels over time.



