# Banking Analytics End-to-End Project

A comprehensive data analytics project focused on banking customer analysis, featuring exploratory data analysis using Python and interactive dashboard visualization with Power BI.

## 📊 Project Overview

This end-to-end banking analytics project demonstrates the complete data science workflow from raw data exploration to business intelligence visualization. The project analyzes banking customer data to uncover insights about customer demographics, financial behaviors, risk patterns, and loyalty classifications using statistical analysis and interactive dashboards.

## 🗂️ Repository Structure

```
Banking-Case-End-to-End-Project/
├── Banking Case.ipynb           # Main Python analysis notebook
├── Banking.csv                  # Primary banking customer dataset
├── clients.csv                  # Gender lookup table (GenderId mapping)
├── Banking Dashboard (2025).pbix # Power BI dashboard file
└── README.md                    # Project documentation
```

## 📈 Data Analysis Features

### Dataset Overview:
- **Sample Size**: 3,000 banking customers
- **Features**: 25 columns including demographics, financial metrics, and risk indicators
- **Data Types**: Mixed (numerical, categorical, and temporal data)

### Key Metrics Analyzed:
- **Customer Demographics**: Age, nationality, gender, occupation analysis
- **Financial Metrics**: Income bands, credit card usage, loan patterns
- **Account Analysis**: Deposits, savings, checking accounts, foreign currency
- **Risk Assessment**: Risk weighting, property ownership, business lending
- **Loyalty Segmentation**: Customer loyalty classifications (Jade, Gold, Silver, Platinum)

### Advanced Analytics Techniques:
- **Income Segmentation**: Custom income banding (Low: <$100K, Mid: $100K-$300K, High: >$300K)
- **Correlation Analysis**: Relationship mapping between financial variables
- **Distribution Analysis**: Statistical distribution of numerical features
- **Categorical Analysis**: Frequency analysis of customer segments

## 🛠️ Technologies & Tools Used

### **Data Analysis Stack**:
- **Python**: Primary analysis language
- **Pandas**: Data manipulation and analysis
- **NumPy**: Numerical computing
- **Matplotlib**: Statistical visualizations
- **Seaborn**: Advanced statistical plots

### **Database & Connectivity**:
- **MySQL**: Database storage and queries
- **mysql-connector-python**: Database connectivity

### **Business Intelligence**:
- **Power BI**: Interactive dashboard creation
- **CSV**: Data exchange format

## 🔍 Key Analysis Insights

### Customer Demographics:
- **Nationality Distribution**: European (44%), Asian (25%), American (17%)
- **Gender Distribution**: Balanced gender representation (Female: 50.4%, Male: 49.6%)
- **Income Segments**: Mid-income customers dominate (50.6%), followed by Low-income (34.2%)

### Financial Behavior Patterns:
- **Credit Card Usage**: Most customers hold 1 credit card (64.1%)
- **Property Ownership**: Average 1-2 properties per customer
- **Fee Structure**: High-fee customers represent 49.2% of the customer base

### Loyalty Classifications:
- **Jade Level**: Highest segment (44.4% of customers)
- **Silver Level**: Second largest (25.6%)
- **Gold Level**: Premium segment (19.5%)
- **Platinum Level**: Elite segment (10.6%)

### Risk Assessment:
- **Risk Weighting**: Most customers classified as moderate risk (Risk Level 2: 40.7%)
- **Business Lending**: Strong correlation with income levels and property ownership

## 📋 Analysis Workflow

### 1. **Data Connection & Loading**
```python
# MySQL database connection
cnx = mysql.connector.connect(
    host="127.0.0.1",
    port=3306,
    user="root",
    password="422123"
)
df = pd.read_sql("SELECT * FROM banking_case.customers", cnx)
```

### 2. **Data Preprocessing**
- Income band categorization using `pd.cut()`
- Data type validation and missing value analysis
- Feature engineering for analytical insights

### 3. **Exploratory Data Analysis (EDA)**

**Univariate Analysis**:
- Distribution analysis of individual variables
- Frequency counts for categorical variables
- Statistical summaries for numerical features

**Bivariate Analysis**:
- Cross-tabulation analysis by nationality
- Correlation matrix for financial variables
- Relationship analysis between customer segments

**Numerical Analysis**:
- Histogram distributions with KDE curves
- Correlation heatmap for financial metrics
- Statistical relationship identification

### 4. **Visualization & Insights**
- Count plots for categorical distributions
- Histogram analysis for numerical variables
- Correlation heatmaps for relationship mapping
- Power BI dashboard for business intelligence

## 🚀 Getting Started

### Prerequisites
- **Python 3.7+** with data science libraries
- **MySQL Server** for database operations
- **Power BI Desktop** for dashboard viewing
- **Jupyter Notebook** environment

### Installation & Setup

1. **Clone the repository**:
   ```bash
   git clone https://github.com/maxx-2345/Banking-Case-End-to-End-Project.git
   cd Banking-Case-End-to-End-Project
   ```

2. **Install required packages**:
   ```bash
   pip install pandas numpy matplotlib seaborn mysql-connector-python
   ```

3. **Database setup**:
   - Import `Banking.csv` into MySQL as `banking_case.customers` table
   - Configure database connection parameters in the notebook

4. **Run the analysis**:
   - Open `Banking Case.ipynb` in Jupyter Notebook
   - Execute cells sequentially for complete analysis
   - Review generated visualizations and insights

5. **View dashboard**:
   - Open `Banking Dashboard (2025).pbix` in Power BI Desktop
   - Explore interactive visualizations and KPIs

## 📊 Sample Analysis Code

### Income Band Creation:
```python
# Define income band boundaries
bins = [0, 100000, 300000, float('inf')]
labels = ['Low', 'Mid', 'High']

# Create Income Band column
df['Income Band'] = pd.cut(df['Estimated Income'], 
                          bins=bins, 
                          labels=labels, 
                          include_lowest=True)
```

### Correlation Analysis:
```python
numerical_cols = ['Estimated Income', 'Superannuation Savings', 
                 'Credit Card Balance', 'Bank Loans', 'Bank Deposits']
                 
correlation_matrix = df[numerical_cols].corr()
sns.heatmap(correlation_matrix, annot=True, cmap='crest', fmt='.2f')
```

### Customer Segmentation Analysis:
```python
# Analyze customer distribution by loyalty and nationality
sns.countplot(data=df, x='Loyalty Classification', hue='Nationality')
plt.title('Customer Loyalty by Nationality')
plt.show()
```

## 📈 Business Impact & Applications

### **Customer Insights**:
- **Segmentation Strategy**: Data-driven customer categorization for targeted marketing
- **Risk Management**: Comprehensive risk assessment based on financial behavior
- **Product Recommendations**: Personalized banking product suggestions

### **Operational Benefits**:
- **Resource Allocation**: Optimize branch resources based on customer demographics
- **Pricing Strategy**: Fee structure optimization based on customer value analysis
- **Retention Programs**: Loyalty-based customer retention initiatives

### **Strategic Decision Support**:
- **Market Expansion**: Geographic expansion based on nationality patterns
- **Product Development**: New product development based on customer needs analysis
- **Regulatory Compliance**: Risk-based compliance monitoring and reporting

## 🎯 Key Performance Indicators (KPIs)

- **Customer Acquisition**: New customer onboarding trends
- **Revenue per Customer**: Average revenue generated by customer segment
- **Risk Exposure**: Portfolio risk distribution analysis
- **Loyalty Metrics**: Customer retention and loyalty progression
- **Product Penetration**: Cross-selling and up-selling opportunities

## 📊 Dashboard Features

The Power BI dashboard includes:
- **Executive Summary**: High-level KPIs and metrics
- **Customer Demographics**: Interactive demographic analysis
- **Financial Performance**: Revenue and profitability analysis
- **Risk Assessment**: Portfolio risk monitoring
- **Loyalty Analysis**: Customer loyalty trend analysis

## 📝 Future Enhancements

- **Machine Learning Models**: Predictive modeling for customer churn and credit scoring
- **Real-time Analytics**: Live dashboard updates with streaming data
- **Advanced Segmentation**: K-means clustering for sophisticated customer grouping
- **Sentiment Analysis**: Customer feedback analysis integration
- **Regulatory Reporting**: Automated compliance reporting features

## 🤝 Contributing

This project is part of a data analytics portfolio demonstrating end-to-end analytical capabilities. Contributions, suggestions, and improvements are welcome!

### Areas for Contribution:
- Advanced statistical analysis techniques
- Additional visualization methods
- Machine learning model integration
- Dashboard enhancement suggestions

## 📧 Contact & Support

**GitHub**: [@maxx-2345](https://github.com/maxx-2345)
**Project Type**: Banking Domain Data Analytics
**Skill Level**: Intermediate to Advanced

## 🏷️ Project Tags

`#DataAnalytics` `#Python` `#PowerBI` `#Banking` `#EDA` `#BusinessIntelligence` `#CustomerAnalytics` `#MySQL` `#DataVisualization` `#FinancialAnalysis`

---

## 🔗 Related Projects

- [COVID-19 Data Analysis](https://github.com/maxx-2345/Covid_19_Analysis) - SQL-based pandemic analysis
- *Additional portfolio projects coming soon*

---

*Last Updated: September 2025*

**Project Status**: ✅ Complete | **Documentation**: ✅ Comprehensive | **Deployment**: 🚀 Ready
