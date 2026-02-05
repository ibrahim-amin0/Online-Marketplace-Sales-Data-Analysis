# 🛒 Online Marketplace Sales Data Analysis

<div align="center">

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Pandas](https://img.shields.io/badge/Pandas-Latest-green.svg)
![NumPy](https://img.shields.io/badge/NumPy-Latest-orange.svg)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Latest-red.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)

**A comprehensive data cleaning and exploratory analysis project for online marketplace sales transactions**

Analyzing sales patterns, customer behavior, and revenue trends across multiple product categories and regions

</div>

---

## 📋 Table of Contents

- [Project Overview](#project-overview)
- [Key Features](#key-features)
- [Dataset](#dataset)
- [Installation](#installation)
- [Project Structure](#project-structure)
- [Methodology](#methodology)
- [Data Cleaning Process](#data-cleaning-process)
- [Analysis & Insights](#analysis--insights)
- [Visualizations](#visualizations)
- [Key Findings](#key-findings)
- [Technologies Used](#technologies-used)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

---

## 🎯 Project Overview

This project performs a comprehensive analysis of an online marketplace's sales data spanning from **January 2024 to April 2025**. The analysis focuses on:

- 🔍 **Data Quality Assessment** - Identifying and handling missing values, duplicates, and outliers
- 🧹 **Data Cleaning** - Implementing systematic cleaning procedures
- 📊 **Exploratory Data Analysis** - Uncovering patterns in sales, regions, and payment methods
- 📈 **Trend Analysis** - Examining daily, weekly, monthly, and seasonal trends
- 💡 **Business Insights** - Extracting actionable insights for decision-making

### 🎓 Learning Objectives

- Master data cleaning techniques for real-world messy datasets
- Handle missing values using statistical methods
- Detect and treat outliers appropriately
- Perform comprehensive exploratory data analysis
- Create meaningful visualizations
- Extract business insights from data

---

## ✨ Key Features

- ✅ **Comprehensive Data Cleaning Pipeline**
  - Missing value imputation using statistical methods
  - Duplicate detection and removal
  - Outlier detection using 3-sigma rule
  - Data type conversion and validation
  
- ✅ **Advanced Missing Data Handling**
  - Mode-based imputation for categorical variables
  - Calculated imputation for numerical variables
  - Group-specific imputation strategies
  
- ✅ **Robust Outlier Detection**
  - Category-specific outlier detection
  - 3-standard deviation method
  - Data integrity validation
  
- ✅ **Time-Series Analysis**
  - Daily revenue trends
  - Weekly patterns
  - Monthly aggregations
  - Seasonal analysis
  
- ✅ **Professional Visualizations**
  - Missing data heatmaps
  - Revenue trend charts
  - Category performance comparisons
  - Regional analysis plots

---

## 📊 Dataset

### Original Dataset Statistics:
- **Total Records**: 1,155 transactions
- **Date Range**: January 1, 2024 - April 23, 2025
- **Features**: 9 columns
- **Product Categories**: 6 (Electronics, Sports, Clothing, Books, Beauty Products, Home Appliances)
- **Regions**: 3 (North America, Europe, Asia)
- **Payment Methods**: 7 types

### Dataset Features:

| Column | Type | Description |
|--------|------|-------------|
| `Transaction ID` | int64 | Unique identifier for each transaction |
| `Date` | datetime | Transaction date |
| `Product Category` | object | Category of product sold |
| `Product Name` | object | Specific product name (dropped due to 80% missing) |
| `Units Sold` | float/int | Number of units in transaction |
| `Unit Price` | float | Price per unit |
| `Total Revenue` | float | Total transaction amount |
| `Region` | object | Geographic region of sale |
| `Payment Method` | object | Payment method used |

### Data Quality Issues Identified:

| Issue | Count | Percentage |
|-------|-------|------------|
| Missing Product Names | 923 | 79.9% |
| Missing Units Sold | 173 | 15.0% |
| Missing Payment Method | 172 | 14.9% |
| Missing Region | 21 | 1.8% |
| Duplicate Records | 37 | 3.2% |
| Outliers (Revenue) | Multiple | Varies by category |

---

## 🚀 Installation

### Prerequisites
```bash
Python 3.8 or higher
pip package manager
```

### Setup

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/online-marketplace-analysis.git
cd online-marketplace-analysis
```

2. **Create virtual environment** (recommended)
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

### Required Libraries
```
pandas>=1.3.0
numpy>=1.21.0
matplotlib>=3.4.0
seaborn>=0.11.0
missingno>=0.5.0
jupyter>=1.0.0
```

---

## 📁 Project Structure

```
online-marketplace-analysis/
│
├── Online_Marketplace__1_.ipynb    # Main analysis notebook
├── README.md                       # Project documentation
├── requirements.txt                # Python dependencies
│
├── data/                           # Data directory
│   ├── raw/
│   │   └── Online Sales Data.csv  # Original dataset
│   └── processed/
│       └── cleaned_sales_data.csv # Cleaned dataset
│
├── notebooks/                      # Additional notebooks
│   ├── 01_data_exploration.ipynb
│   ├── 02_data_cleaning.ipynb
│   └── 03_analysis.ipynb
│
├── src/                            # Source code
│   ├── data_cleaning.py           # Cleaning functions
│   ├── data_analysis.py           # Analysis functions
│   └── visualization.py           # Plotting functions
│
└── reports/                        # Generated reports
    ├── figures/                   # Saved visualizations
    │   ├── missing_data_heatmap.png
    │   ├── revenue_trends.png
    │   └── category_analysis.png
    └── summary_statistics.csv     # Summary metrics
```

---

## 🔬 Methodology

### Step-by-Step Process:

### 1️⃣ **Data Loading & Initial Exploration**
- Load dataset using pandas
- Inspect structure, dimensions, and data types
- Generate descriptive statistics
- Identify unique values in categorical columns

### 2️⃣ **Data Quality Assessment**
- **Missing Values Analysis**
  - Count missing values per column
  - Calculate percentage of missing data
  - Visualize missing patterns using missingno
  
- **Duplicate Detection**
  - Identify duplicate transactions
  - Analyze duplicate patterns
  - Remove based on Transaction ID

- **Data Type Validation**
  - Verify correct data types
  - Convert where necessary

### 3️⃣ **Data Cleaning Process**
Detailed cleaning procedures implemented:

#### A. **Missing Value Treatment**

**Product Name (79.9% missing)**
- Decision: **Dropped** - Too many missing values to reliably impute
- Impact: Minimal - analysis focuses on categories

**Units Sold (15% missing)**
- Method: **Calculated Imputation**
- Formula: `Units Sold = Total Revenue / Unit Price`
- Applied when: Unit Price ≠ 0 and both Revenue and Price exist

**Region (1.8% missing)**
- Method: **Mode Imputation**
- Filled with most frequent region: North America

**Payment Method (14.9% missing)**
- Method: **Group-Based Mode Imputation**
- Strategy: Fill based on mode within Region + Product Category groups
- Rationale: Payment preferences vary by region and product type

#### B. **Data Type Conversion**

```python
# Clean and convert Units Sold
df['Units Sold'] = df['Units Sold'].str.replace(r"[^0-9.]", "", regex=True).astype(float)

# Clean and convert Unit Price
df['Unit Price'] = df['Unit Price'].str.replace(r"[^0-9.]", "", regex=True).astype(float)

# Convert Date to datetime
df['Date'] = pd.to_datetime(df['Date'])

# Convert Units Sold to integer
df['Units Sold'] = df['Units Sold'].astype(int)
```

#### C. **Duplicate Removal**

- **Identified**: 37 duplicate records
- **Method**: Removed duplicates based on unique Transaction ID
- **Result**: 1,118 unique transactions retained

#### D. **Outlier Detection & Treatment**

**Strategy**: Category-specific outlier detection using 3-sigma rule

```python
def detect_outliers(group):
    mean = group['Total Revenue'].mean()
    std = group['Total Revenue'].std()
    upper = mean + 3*std
    lower = mean - 3*std
    group['outlier'] = ~group['Total Revenue'].between(lower, upper)
    return group
```

**Process**:
1. Group data by Product Category
2. Calculate mean and standard deviation for each category
3. Flag values outside 3 standard deviations
4. Remove flagged outliers
5. Filter unrealistic Units Sold (>15 units)

**Reasoning**: Different product categories have different price ranges, requiring category-specific thresholds

#### E. **Data Validation**

**Revenue Consistency Check**:
```python
# Verify: Total Revenue = Unit Price × Units Sold
df['Total'] = df['Unit Price'] * df['Units Sold']
mismatch = df[df['Total Revenue'].round(2) != df['Total'].round(2)]
```

- **Action**: Recalculated Total Revenue where mismatches found
- **Tolerance**: ±0.01 for floating-point precision

### 4️⃣ **Feature Engineering**

Created time-based features for temporal analysis:

```python
df['Date_only'] = df['Date'].dt.date
df['Weekday'] = df['Date'].dt.day_name()
df['Month'] = df['Date'].dt.to_period('M')
df['Week_of_Month'] = df['Date'].apply(lambda d: (d.day - 1) // 7 + 1)
df['Season'] = df['Date'].dt.month % 12 // 3 + 1
```

**New Features**:
- `Date_only`: Pure date without time
- `Weekday`: Day name (Monday-Sunday)
- `Month`: Monthly period
- `Week_of_Month`: Week number within month (1-5)
- `Season`: Seasonal indicator (1=Winter, 2=Spring, 3=Summer, 4=Fall)

### 5️⃣ **Aggregation & Analysis**

**Daily Sales Analysis**:
```python
daily_sales = df.groupby('Date_only').agg(
    Total_Revenue=('Total Revenue', 'sum'),
    Transaction_Count=('Transaction ID', 'count')
)
```

**Weekday Performance**:
```python
weekday_sales = df.groupby('Weekday').agg(
    Total_Revenue=('Total Revenue', 'sum'),
    Transaction_Count=('Transaction ID', 'count')
)
```

**Monthly Trends**:
```python
monthly_sales = df.groupby('Month').agg(
    Total_Revenue=('Total Revenue', 'sum'),
    Transaction_Count=('Transaction ID', 'count')
)
```

**Seasonal Patterns**:
```python
seasonal_sales = df.groupby('Season').agg(
    Total_Revenue=('Total Revenue', 'sum'),
    Transaction_Count=('Transaction ID', 'count')
)
```

---

## 🧹 Data Cleaning Process

### Summary of Cleaning Actions:

| Action | Before | After | Impact |
|--------|--------|-------|--------|
| **Records** | 1,155 | 1,080+ | Removed duplicates & outliers |
| **Missing Product Name** | 923 (79.9%) | 0 | Column dropped |
| **Missing Units Sold** | 173 (15.0%) | 0 | Calculated imputation |
| **Missing Region** | 21 (1.8%) | 0 | Mode imputation |
| **Missing Payment Method** | 172 (14.9%) | 0 | Group-based mode |
| **Duplicates** | 37 | 0 | Removed by Transaction ID |
| **Outliers** | Multiple | 0 | Category-specific removal |
| **Data Types** | Mixed | Consistent | Proper conversion |

### Quality Assurance Checks:

✅ No missing values in critical columns  
✅ No duplicate Transaction IDs  
✅ All numerical columns have correct data types  
✅ Revenue calculations are consistent  
✅ Date range is valid (2024-2025)  
✅ No negative values in revenue/price/units  
✅ Outliers removed based on statistical methods  

---

## 📈 Analysis & Insights

### Product Category Analysis

**Distribution**:
- Electronics: 202 transactions (17.5%)
- Sports: 193 transactions (16.7%)
- Clothing: 192 transactions (16.6%)
- Books: 192 transactions (16.6%)
- Beauty Products: 190 transactions (16.4%)
- Home Appliances: 186 transactions (16.1%)

**Insight**: Relatively balanced distribution across categories, with Electronics slightly leading

### Regional Performance

**Transaction Distribution**:
- North America: 384 transactions (33.9%)
- Europe: 379 transactions (33.4%)
- Asia: 371 transactions (32.7%)

**Insight**: Well-balanced global presence with slight preference for North American market

### Payment Method Preferences

**Usage Statistics**:
1. Credit Card: 478 transactions (48.6%)
2. PayPal: 286 transactions (29.1%)
3. Debit Card: 161 transactions (16.4%)
4. Cryptocurrency: 20 transactions (2.0%)
5. Mobile Payment: 15 transactions (1.5%)
6. Gift Card: 15 transactions (1.5%)
7. Bank Transfer: 8 transactions (0.8%)

**Insight**: Credit Card dominates, followed by PayPal; Digital payment methods gaining traction

### Temporal Patterns

**Key Observations**:
- Date range spans 16 months (Jan 2024 - Apr 2025)
- Daily transaction patterns available for trend analysis
- Weekday vs. weekend performance comparison
- Monthly revenue fluctuations identified
- Seasonal trends analyzed

---

## 📊 Visualizations

The project includes multiple visualization techniques:

### 1. **Missing Data Analysis**
- **Bar Chart**: Count of missing values per column
- **Matrix Plot**: Pattern of missing data across dataset
- **Heatmap**: Correlation of missing values between columns

### 2. **Revenue Trends**
- **Line Chart**: Daily revenue trends over time
- **Bar Charts**: 
  - Weekday performance (Revenue & Transaction Count)
  - Monthly revenue aggregation
  - Seasonal revenue patterns

### 3. **Category & Regional Analysis**
- Product category distribution
- Regional performance comparison
- Payment method preferences by region and category

---

## 🔍 Key Findings

### Data Quality Insights:

1. **High Missing Rate in Product Names (80%)**
   - Indicates potential data collection issues
   - Recommendation: Improve product tracking system

2. **Consistent Missing Pattern in Payment Method**
   - 15% missing across specific region-category combinations
   - Suggests systematic collection gap
   - Successfully imputed using group-based approach

3. **Outliers Present Across Categories**
   - Different categories have different price ranges
   - Category-specific treatment was essential
   - Removed extreme values that could skew analysis

4. **Data Consistency Issues**
   - Some calculated revenues didn't match recorded values
   - Required validation and correction
   - Highlights importance of automated calculation

### Business Insights:

1. **Balanced Product Portfolio**
   - No single category dominates
   - Diversified revenue streams

2. **Global Market Presence**
   - Nearly equal distribution across three major regions
   - Opportunity for targeted regional strategies

3. **Digital Payment Adoption**
   - Credit Card and PayPal account for 77% of transactions
   - Growing trend in cryptocurrency and mobile payments

4. **Temporal Patterns**
   - Analysis reveals patterns in daily, weekly, and seasonal sales
   - Can inform inventory and marketing strategies

---

## 🛠 Technologies Used

### Core Libraries:

- **Data Manipulation**: 
  - `pandas` - DataFrame operations and data cleaning
  - `numpy` - Numerical computations and array operations

- **Visualization**: 
  - `matplotlib` - Base plotting functionality
  - `seaborn` - Statistical data visualization
  - `missingno` - Missing data visualization

### Key Techniques:

#### Data Cleaning:
- ✅ Missing value imputation (mode, calculation-based)
- ✅ Regular expressions for data cleaning
- ✅ Data type conversion
- ✅ Duplicate detection and removal
- ✅ Outlier detection (3-sigma rule)
- ✅ Data validation and consistency checks

#### Analysis:
- ✅ GroupBy aggregations
- ✅ Time-series feature extraction
- ✅ Statistical methods (mean, std, mode)
- ✅ Cross-tabulation for categorical analysis
- ✅ Temporal pattern analysis

---

## 💻 Usage

### Running the Analysis

1. **Launch Jupyter Notebook**
```bash
jupyter notebook Online_Marketplace__1_.ipynb
```

2. **Run All Cells**
- Click `Kernel` → `Restart & Run All`
- Or run cells sequentially to follow the analysis step-by-step

### Using the Cleaned Data

```python
import pandas as pd

# Load cleaned dataset
df = pd.read_csv('data/processed/cleaned_sales_data.csv')

# Example: Get top 5 products by revenue
top_products = df.groupby('Product Category')['Total Revenue'].sum().sort_values(ascending=False).head()
print(top_products)

# Example: Analyze sales by region
regional_sales = df.groupby('Region').agg({
    'Total Revenue': 'sum',
    'Transaction ID': 'count'
})
print(regional_sales)
```

### Custom Analysis Examples

**Revenue Analysis by Category and Region**:
```python
category_region = df.groupby(['Product Category', 'Region'])['Total Revenue'].sum().unstack()
print(category_region)
```

**Monthly Revenue Trend**:
```python
monthly_trend = df.groupby(df['Date'].dt.to_period('M'))['Total Revenue'].sum()
monthly_trend.plot(kind='line', figsize=(12, 6), title='Monthly Revenue Trend')
```

**Payment Method by Region**:
```python
payment_region = pd.crosstab(df['Region'], df['Payment Method'], normalize='index') * 100
print(payment_region.round(2))
```

---

## 📚 Project Insights & Recommendations

### Data Collection Improvements:
1. **Implement mandatory Product Name field** to reduce 80% missing rate
2. **Automate payment method capture** to eliminate 15% missing values
3. **Add validation rules** to prevent data entry errors
4. **Implement real-time revenue calculations** to ensure consistency

### Business Recommendations:
1. **Regional Strategies**: 
   - Leverage balanced global presence for targeted campaigns
   - Analyze region-specific product preferences

2. **Payment Optimization**: 
   - Focus on Credit Card and PayPal infrastructure
   - Explore cryptocurrency integration opportunities

3. **Inventory Management**: 
   - Use temporal patterns for demand forecasting
   - Optimize stock levels based on seasonal trends

4. **Product Strategy**: 
   - Maintain balanced portfolio across categories
   - Identify cross-selling opportunities

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

### Ways to Contribute:
- 🔹 Additional analysis techniques
- 🔹 New visualizations
- 🔹 Code optimization
- 🔹 Documentation improvements
- 🔹 Bug fixes
- 🔹 Feature requests

### Contribution Process:
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---


## 📧 Contact

**Project Author**:Ibrahim Amin

- 📧 Email: 0ibrahim0amin@gmail.com
- 🐙 GitHub: @ibrahim-amin0(https://github.com/ibrahim-amin0)
- 💼 LinkedIn: Ibrahim Amin(www.linkedin.com/in/ibrahim-amin-aie0101010101)

---

## 🙏 Acknowledgments

- Dataset: Online Sales Data
- Libraries: Pandas, NumPy, Matplotlib, Seaborn, Missingno
- Community: Stack Overflow, Pandas Documentation
- Inspiration: Real-world data cleaning challenges in e-commerce

---


<div align="center">

### ⭐ If you found this project helpful, please give it a star!

**Made with ❤️ for Data Science**

</div>

---

## 🗺️ Roadmap

### Future Enhancements:

- [ ] **Predictive Modeling**: Build models to forecast future sales
- [ ] **Customer Segmentation**: Cluster analysis of purchasing patterns
- [ ] **Interactive Dashboard**: Create Streamlit/Dash dashboard
- [ ] **Automated Reporting**: Generate PDF reports automatically
- [ ] **API Integration**: Connect to live data sources
- [ ] **Advanced Visualizations**: Interactive Plotly charts
- [ ] **A/B Testing Framework**: Compare different marketing strategies
- [ ] **Recommendation Engine**: Product recommendation system

---

## 📖 Additional Resources

### Related Tutorials:
- [Pandas Documentation](https://pandas.pydata.org/docs/)
- [Data Cleaning Best Practices](https://pandas.pydata.org/docs/user_guide/missing_data.html)
- [Exploratory Data Analysis Guide](https://towardsdatascience.com/exploratory-data-analysis-8fc1cb20fd15)

### Recommended Reading:
- "Python for Data Analysis" by Wes McKinney
- "Data Science from Scratch" by Joel Grus
- "Storytelling with Data" by Cole Nussbaumer Knaflic

---

## ❓ FAQ

**Q: Why was Product Name column dropped?**  
A: With 80% missing values, imputation would be unreliable and potentially misleading. Product Category provides sufficient granularity for analysis.

**Q: How were outliers determined?**  
A: Used the 3-sigma rule within each product category, as different categories have different price distributions.

**Q: Why group-based imputation for Payment Method?**  
A: Payment preferences vary significantly by region and product type. Group-based imputation preserves these patterns.

**Q: Can this analysis be applied to other datasets?**  
A: Yes! The cleaning pipeline and analysis techniques are generalizable. Adjust thresholds and categories as needed.

**Q: How do I handle new incoming data?**  
A: Apply the same cleaning pipeline in sequence: type conversion → missing values → duplicates → outliers → validation.

---

**Happy Analyzing! 📊✨**
