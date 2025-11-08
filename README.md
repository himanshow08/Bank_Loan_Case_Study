# Bank Loan Exploratory Data Analysis (EDA)

This Jupyter Notebook performs an Exploratory Data Analysis (EDA) on the `application_data.csv` dataset to identify patterns and factors influencing loan repayment status. The primary goal is to clean the data, analyze distributions, identify outliers, and understand the characteristics of clients who have payment difficulties (TARGET=1) versus those who do not (TARGET=0).

## Libraries Used
The analysis utilizes the following Python libraries:
* `warnings`
* `pandas`
* `numpy`
* `matplotlib.pyplot`
* `seaborn`
* `math`

## Data Analysis Workflow

1.  **Data Loading and Inspection:**
    * The `application_data.csv` file is loaded into a pandas DataFrame.
    * Initial data inspection includes checking the dimensions (`.shape`), column data types (`.dtypes`), and statistical summaries (`.describe()`).

2.  **Data Cleaning and Missing Value Treatment:**
    * **Null Value Analysis:** The percentage of missing values is calculated for every column.
    * **Column Dropping:** Columns with over 50% missing values are dropped from the DataFrame.
    * **Imputation Analysis:** Columns with a smaller but significant percentage of missing data (e.g., the `AMT_REQ_CREDIT_BUREAU_...` series) are analyzed using boxplots and value counts. The analysis suggests that '0' is the most appropriate imputation for many of these, as it is the overwhelming mode.

3.  **Outlier Analysis:**
    * Key numerical columns are inspected for outliers using boxplots.
    * Columns analyzed include:
        * `AMT_INCOME_TOTAL`
        * `AMT_CREDIT`
        * `AMT_ANNUITY`
        * `AMT_GOODS_PRICE`
        * `FLOORSMAX_AVG`
    * The percentage of data points that are outliers is calculated to determine the significance.

4.  **Data Imbalance:**
    * The distribution of the `TARGET` variable is checked to identify data imbalance.
    * A pie chart is generated to visualize the proportion of clients with payment difficulties (Target=1) versus all other clients (Target=0).

5.  **Univariate and Bivariate Analysis:**
    * The dataset is segmented into two DataFrames: `target_0_case` (clients without payment difficulties) and `target_1_case` (clients with payment difficulties).
    * Categorical variables (e.g., `CODE_GENDER`) are analyzed against the `TARGET` variable using side-by-side bar charts to understand the relationship between client characteristics and default status.
    * The analysis continues by comparing income levels and other factors between the two target groups.
