# Adult Income Analysis 📊

This project analyzes the "Adult Census Income" dataset to uncover key factors that influence whether an individual earns more or less than $50,000 per year. The analysis uses Python with Pandas for data manipulation and Seaborn/Matplotlib for visualization.
<br>

## 🚀 Built With

This project relies on the following open-source Python libraries:

* ![Pandas](https://img.shields.io/badge/Pandas-2.2.2-150458?style=for-the-badge&logo=pandas)
* ![Seaborn](https://img.shields.io/badge/Seaborn-0.13.2-0272B2?style=for-the-badge&logo=seaborn)
* ![Matplotlib](https://img.shields.io/badge/Matplotlib-3.9.0-891823?style=for-the-badge&logo=matplotlib)
* ![Python](https://img.shields.io/badge/Python-3.11-3776AB?style=for-the-badge&logo=python)

<br>

## ⚙️ Getting Started

To get a local copy up and running, follow these simple steps.

### Prerequisites

You need to have Python and `pip` installed on your system. You can install the required libraries using the following command:

```sh
pip install pandas seaborn matplotlib
```

### Installation

1.  Clone this repository to your local machine (or simply download the files).
2.  Make sure the `adult.csv` dataset is in the same directory as your Python script.

<br>

## 📈 Usage

To generate the analysis and visualizations, run the main Python script from your terminal.

```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

# Load and clean the dataset
df = pd.read_csv('adult.csv')
df = df.apply(lambda x: x.str.strip() if x.dtype == "object" else x)
df.replace('?', pd.NA, inplace=True)
df.dropna(inplace=True)

# Create a figure with multiple subplots
fig, axes = plt.subplots(2, 2, figsize=(18, 14))
fig.suptitle('Comprehensive Analysis of Adult Income Dataset', fontsize=22, weight='bold')

# Plot 1: Age Distribution by Income
sns.histplot(data=df, x='age', hue='income', multiple='stack', ax=axes[0, 0], bins=30, palette="viridis")
axes[0, 0].set_title('Age Distribution by Income Level', fontsize=16)

# Plot 2: Income by Marital Status
sns.countplot(data=df, y='marital-status', hue='income', ax=axes[0, 1], palette="viridis")
axes[0, 1].set_title('Income Level by Marital Status', fontsize=16)

# Plot 3: Hours Per Week by Income
sns.violinplot(data=df, x='income', y='hours-per-week', ax=axes[1, 0], palette="viridis")
axes[1, 0].set_title('Distribution of Hours Worked Per Week', fontsize=16)

# Plot 4: High Earners by Gender
high_earners = df[df['income'] == '>50K']['gender'].value_counts()
axes[1, 1].pie(high_earners, labels=high_earners.index, autopct='%1.1f%%', startangle=140)
axes[1, 1].set_title('Proportion of High Earners by Gender (>50K)', fontsize=16)

plt.tight_layout(rect=[0, 0, 1, 0.96])
plt.show()

```

<br>

## 🔍 Key Findings & Visualizations

The analysis revealed several strong correlations between demographics and income levels.

### 1. Income Tends to Increase with Age
The `>50K` income group is most concentrated in the 35-55 age range, suggesting that experience gained over a career is a major factor in higher earnings.
<img width="830" height="634" alt="image" src="https://github.com/user-attachments/assets/b81f4533-c093-4db1-ade9-3ba8c4be051e" />

---

### 2. Marital Status is a Strong Predictor
Individuals who are 'Married-civ-spouse' are far more likely to be high earners compared to any other group. This could be due to factors like dual-income households and increased financial stability.
<img width="935" height="648" alt="image" src="https://github.com/user-attachments/assets/563bc440-76a7-4e7f-951d-1ac95a53653e" />

---

### 3. High Earners Work Longer Hours
While 40 hours is the standard work week for both income groups, those earning `>50K` are much more likely to work 40-60 hours per week.
<img width="841" height="638" alt="image" src="https://github.com/user-attachments/assets/6a769c48-745f-4c22-bcff-956ad153e121" />

---

### 4. A Significant Gender Gap Exists Among Top Earners
Within the high-income bracket (`>50K`), there is a clear gender disparity. Men constitute a vast majority (85%) of the high earners in this dataset.
<img width="596" height="578" alt="image" src="https://github.com/user-attachments/assets/83b37282-f333-48b7-9326-a7f8c331bf3f" />
