# Churn-Analysis
Customer Churn analysis using python and CSV
The uploaded Jupyter Notebook titled **"Churn Analysis"** contains:

* 📄 **Total Cells:** 27
* 💻 **Code Cells:** 25
* 📝 **Markdown Cells:** 2

### Initial Insights:

* The first markdown section is titled **"Fetching Data"**.
* The first code cell includes the standard data analysis libraries:

  ```python
  import pandas as pd 
  import numpy as  np
  import matplotlib.pyplot as plt
  import seaborn as sns
  ```

Next, I’ll go through the notebook in detail to extract the workflow, important findings, and visual insights to help you write a polished GitHub README or documentation summary.


Here’s a breakdown of the **first half** of your Churn Analysis notebook. It performs typical steps in an exploratory data analysis (EDA) process for customer churn prediction.

---

### 🔍 **1. Library Imports**

```python
import pandas as pd 
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

* Common libraries used for data handling, numerical computation, and visualization.

---

### 📂 **2. Load Dataset**

```python
df = pd.read_csv('Customer Churn.csv')
df.info()
```

* Loads the dataset.
* Initial inspection shows that `TotalCharges` is read as an object (likely due to spaces or non-numeric entries).

---

### 🔧 **3. Data Cleaning**

```python
df["TotalCharges"] = df["TotalCharges"].replace(" ","0")
df["TotalCharges"] = df["TotalCharges"].astype("float")
```

* Converts `TotalCharges` from object to float after cleaning.

```python
df.isnull().sum().sum()
```

* Checks for missing values. Result: No nulls found.

```python
df["customerID"].duplicated().sum()
```

* No duplicate customer IDs found.

---

### 🔄 **4. Data Transformation**

```python
def convo(value):
    return "Yes" if value == 1 else "No"

df["SeniorCitizen"] = df["SeniorCitizen"].apply(convo)
```

* Converts binary values (0, 1) in `SeniorCitizen` to "Yes" and "No".

---

### 📊 **5. Initial Visualizations**

```python
sns.countplot(x='Churn', data=df)
```

* Bar chart showing counts of churned vs non-churned customers.

```python
plt.pie(..., labels = group_by.index, autopct = "%1.2f%%")
```

* Pie chart showing percentage of churned customers.

---

Next, I’ll analyze the remaining code to cover correlation, feature distribution, and insights that are likely used for modeling or final conclusions.


Here’s the summary of the **second half** of your Churn Analysis notebook, which dives deeper into visualizations and pattern identification.

---

### 📊 **6. Churn Distribution Insights**

* **Pie Chart**: Shows that **26.54% of customers have churned**.

---

### 🧑‍🤝‍🧑 **7. Gender & Senior Citizen Analysis**

* **Gender vs Churn (CountPlot)**:

  * Churn rate is nearly the same across genders.

* **SeniorCitizen vs Churn (Stacked Bar)**:

  * **Senior Citizens show a significantly higher churn rate**.

---

### 📅 **8. Tenure and Contract Insights**

* **Tenure Histogram (by Churn)**:

  * Churn is **highest in the first quarter (0–12 months)** of tenure.

* **Contract Type vs Churn**:

  * Month-to-month customers have the **highest churn**.
  * 2-year contracts have the **lowest churn**.

---

### 📶 **9. Service Usage Impact**

* Analyzed features like:

  * `PhoneService`, `MultipleLines`, `InternetService`, `OnlineSecurity`, `OnlineBackup`, `DeviceProtection`, `TechSupport`, `StreamingTV`, `StreamingMovies`

* **Pattern**:

  * Customers lacking online services and support (like `TechSupport` or `OnlineSecurity`) are more likely to churn.

---

### 💳 **10. Payment Method Impact**

* **Electronic check** users have a higher churn rate compared to other methods (credit card, mailed check, etc.).

---

This EDA helps identify **customer segments most likely to churn**, offering actionable insights for retention strategies.

