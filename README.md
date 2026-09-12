# 📊 Customer Churn Analysis

## 📌 Overview

This project performs an **Exploratory Data Analysis (EDA)** on customer churn to understand the factors associated with customers leaving a service.

The analysis focuses on customer demographics, tenure, contract type, payment method, internet services, and other subscribed services to identify patterns in customer churn.

The main objective is to transform raw customer data into meaningful insights that can help businesses understand **which customer segments are more likely to churn** and where retention efforts should be focused.

---

## 🎯 Objectives

The key objectives of this project are:

* Analyze the overall customer churn rate.
* Understand churn patterns across different customer segments.
* Compare churn between different contract types.
* Analyze the relationship between payment methods and churn.
* Study how customer tenure affects churn.
* Investigate churn among senior citizens.
* Explore the relationship between internet/service subscriptions and churn.
* Visualize important patterns using charts and graphs.
* Derive actionable recommendations for improving customer retention.

---

## 📂 Dataset

The dataset contains **7,043 customer records** and **21 columns**.

Important features include:

| Feature            | Description                              |
| ------------------ | ---------------------------------------- |
| `customerID`       | Unique customer identifier               |
| `gender`           | Customer gender                          |
| `SeniorCitizen`    | Whether the customer is a senior citizen |
| `Partner`          | Whether the customer has a partner       |
| `Dependents`       | Whether the customer has dependents      |
| `tenure`           | Number of months the customer has stayed |
| `PhoneService`     | Whether phone service is subscribed      |
| `MultipleLines`    | Multiple phone lines subscription        |
| `InternetService`  | Type of internet service                 |
| `OnlineSecurity`   | Online security subscription             |
| `OnlineBackup`     | Online backup subscription               |
| `DeviceProtection` | Device protection subscription           |
| `TechSupport`      | Technical support subscription           |
| `StreamingTV`      | Streaming TV subscription                |
| `StreamingMovies`  | Streaming movies subscription            |
| `Contract`         | Contract type                            |
| `PaperlessBilling` | Paperless billing status                 |
| `PaymentMethod`    | Customer's payment method                |
| `MonthlyCharges`   | Monthly customer charges                 |
| `TotalCharges`     | Total charges accumulated                |
| `Churn`            | Whether the customer left the service    |

The notebook confirms that the dataset contains 7,043 rows and 21 columns.

---

## 🛠️ Technologies & Libraries

The project is implemented in Python using:

* **Python**
* **Pandas** – Data manipulation and analysis
* **NumPy** – Numerical operations
* **Matplotlib** – Data visualization
* **Seaborn** – Statistical visualization
* **Jupyter Notebook** – Interactive analysis environment

The notebook imports Pandas, NumPy, Matplotlib, and Seaborn for the analysis.

---

## 🔍 Analysis Workflow

The project follows these major steps:

### 1. Data Loading

The customer churn dataset is loaded into a Pandas DataFrame.

```python
df = pd.read_csv('Customer Churn.csv')
```

The initial dataset is explored using `head()` and `info()`.

---

### 2. Data Inspection

The dataset structure, data types, number of records, and columns are examined.

The analysis identifies:

* 7,043 customers
* 21 features
* Numerical and categorical variables
* `TotalCharges` initially stored as an object

---

### 3. Data Cleaning

The `TotalCharges` column contains blank values for customers whose tenure is zero.

These blank values are replaced with `0`, after which the column is converted to a numeric data type.

```python
df["TotalCharges"] = df["TotalCharges"].replace(" ", "0")
df["TotalCharges"] = df["TotalCharges"].astype("float")
```

After cleaning, `TotalCharges` becomes a numerical column.

The notebook also checks for missing values and finds **0 missing values** after preprocessing.

---

### 4. Duplicate Check

Customer IDs are checked for duplicate records.

```python
df["customerID"].duplicated().sum()
```

The analysis found **0 duplicated customer IDs**.

---

### 5. Feature Transformation

The `SeniorCitizen` feature is originally represented as:

* `0` → Non-senior citizen
* `1` → Senior citizen

It is converted into more readable `yes` / `no` values for visualization and interpretation.

---

# 📈 Key Findings

## 1. Overall Churn

The analysis shows that approximately **26.54% of customers have churned**.

This means roughly one out of every four customers in the dataset has left the service.

The notebook visualizes the distribution using both a count plot and a percentage-based pie chart.

---

## 2. Churn by Contract Type

Contract type is one of the strongest patterns observed in the analysis.

| Contract Type  | Churn Rate |
| -------------- | ---------: |
| Month-to-month |    **42%** |
| One year       |    **11%** |
| Two year       |     **3%** |

Customers with month-to-month contracts have a substantially higher churn rate than customers committed to one-year or two-year contracts.

### Insight

Longer-term contracts are strongly associated with lower churn.

However, this analysis identifies an **association**, not proof that longer contracts directly cause customers to stay.

---

## 3. Churn by Payment Method

Payment method also shows a notable difference in churn.

| Payment Method   | Approx. Churn |
| ---------------- | ------------: |
| Electronic check |       **45%** |
| Credit card      |      **~15%** |
| Bank transfer    |   **~15–18%** |
| Mailed check     |   **~15–18%** |

Customers using electronic checks have the highest observed churn rate at approximately **45%**.

### Insight

Electronic-check users appear to be a high-risk customer segment.

The analysis suggests that payment convenience, security, or trust could potentially be contributing factors, but additional investigation would be required to establish the actual reason.

---

## 4. Churn by Customer Tenure

Customer tenure shows a clear declining pattern in churn.

| Tenure            | Approx. Churn |
| ----------------- | ------------: |
| Less than 1 year  |       **50%** |
| 1–3 years         |       **35%** |
| More than 3 years |       **15%** |

Customers with shorter tenure are considerably more likely to churn, while customers who remain with the company for longer periods show much lower churn.

### Insight

The first year of the customer lifecycle appears to be particularly important.

This suggests that onboarding, early engagement, customer support, and loyalty initiatives could be important areas for retention efforts.

---

## 5. Churn by Internet Service

The analysis also compares churn between internet service types.

| Internet Service | Approx. Churn |
| ---------------- | ------------: |
| Fiber optic      |       **30%** |
| DSL              |       **20%** |

Fiber-optic customers show a higher churn rate than DSL customers in the analysis.

### Insight

The difference may warrant further investigation into:

* Service quality
* Pricing
* Customer expectations
* Competition
* Network reliability
* Customer satisfaction

The current analysis identifies the pattern but does not establish its underlying cause.

---

## 6. Senior Citizens and Churn

The analysis compares senior citizens with non-senior customers.

| Customer Segment    | Churn Rate |
| ------------------- | ---------: |
| Senior citizens     |    **41%** |
| Non-senior citizens |    **26%** |

Senior citizens show a noticeably higher churn rate in the analyzed dataset.

### Insight

This segment may benefit from targeted customer support, simplified service experiences, and personalized retention initiatives.

---

## 7. Additional Service-Level Patterns

The notebook also examines churn across:

* Phone Service
* Multiple Lines
* Internet Service
* Online Security
* Online Backup
* Device Protection
* Tech Support
* Streaming TV
* Streaming Movies

The visualizations indicate differences in churn patterns depending on whether customers use or do not use particular services.

The analysis particularly notes that customers who do not use certain additional services such as online backup, technical support, and streaming services can show higher churn in some segments.

---

# 📊 Visualizations

The notebook uses several visualization techniques to identify churn patterns:

### Count Plots

Used to compare the number of churned and non-churned customers across categories.

### Pie Chart

Used to display the overall percentage distribution of churn.

### Histograms

Used to examine the relationship between customer tenure and churn.

### Stacked Bar Charts

Used to compare churn percentages between customer groups such as senior and non-senior customers.

### Multi-Category Service Analysis

Multiple service features are visualized together to compare churn behavior across different subscribed services.

---

# 💡 Business Recommendations

Based on the observed patterns, the following strategies could help improve customer retention:

### 1. Encourage Long-Term Contracts

Offer suitable incentives for customers to move from month-to-month contracts to longer-term plans.

The large difference between month-to-month churn (**42%**) and two-year contract churn (**3%**) makes contract type an important retention area.

### 2. Investigate Electronic Check Users

Customers paying through electronic checks show approximately **45% churn**.

Businesses could investigate payment-related customer experience and consider encouraging customers to adopt alternative payment methods.

### 3. Focus on the First Year

Since customers with less than one year of tenure show approximately **50% churn**, early-stage customer engagement should be a major retention priority.

Possible strategies include:

* Better onboarding
* Early customer feedback
* Proactive support
* Personalized offers
* Loyalty programs

### 4. Develop Targeted Senior-Customer Support

Senior citizens show approximately **41% churn** compared with **26%** among non-senior customers.

Targeted support and simpler customer service experiences may help address this segment's needs.

### 5. Investigate Fiber-Optic Churn

Fiber-optic customers show approximately **30% churn**, compared with **20%** for DSL customers.

Further analysis should examine whether pricing, service quality, reliability, or customer expectations explain this difference.

---

# 📌 Important Note About the Analysis

This project is primarily an **Exploratory Data Analysis (EDA)** project.

The percentages represent patterns observed in the dataset. They should not automatically be interpreted as causal relationships.

For example:

> A higher churn rate among electronic-check users does not necessarily mean that electronic checks cause customers to leave.

Further statistical analysis or machine-learning modeling would be required to determine predictive relationships and potential causal factors.

---

# 🚀 How to Run the Project

### 1. Clone the repository

```bash
git clone <your-repository-url>
cd <repository-folder>
```

### 2. Install dependencies

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### 3. Start Jupyter Notebook

```bash
jupyter notebook
```

### 4. Open the notebook

Open:

```text
Total_churn_Analysis.ipynb
```

### 5. Make sure the dataset is available

Place the required CSV file in the same directory as the notebook:

```text
Customer Churn.csv
```

---

# 📁 Project Structure

```text
Customer-Churn-Analysis/
│
├── Customer Churn.csv
├── Total_churn_Analysis.ipynb
├── Customer Churn Analysys.pdf
└── README.md
```

---

# 🔮 Future Improvements

This project can be extended beyond exploratory analysis by adding:

* Correlation analysis
* Statistical hypothesis testing
* Feature engineering
* Customer segmentation
* Churn prediction using Machine Learning
* Logistic Regression
* Decision Trees
* Random Forest
* XGBoost
* Model evaluation using Accuracy, Precision, Recall, F1-score and ROC-AUC
* Feature importance analysis
* Interactive dashboards using Power BI, Tableau, or Plotly
* Customer-level churn prediction

---

# 🏁 Conclusion

The analysis demonstrates that customer churn is not evenly distributed across the customer base.

The strongest observed patterns include:

* **Month-to-month customers:** ~42% churn
* **Electronic check users:** ~45% churn
* **Customers with less than one year tenure:** ~50% churn
* **Fiber-optic customers:** ~30% churn
* **Senior citizens:** ~41% churn

Overall, the findings suggest that **early customer engagement, contract structure, payment-method experience, and targeted customer retention strategies** deserve particular attention.

The project provides a foundation for moving from descriptive analytics toward **predictive customer churn modeling**.
