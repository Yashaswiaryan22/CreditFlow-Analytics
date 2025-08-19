# 💳 CreditFlow Analytics
### Real-Time Credit Card Financial Intelligence Dashboard

[![Power BI](https://img.shields.io/badge/Power_BI-Dashboard-yellow.svg)](https://powerbi.microsoft.com/)
[![SQL](https://img.shields.io/badge/SQL-PostgreSQL-blue.svg)](https://www.postgresql.org/)
[![Python](https://img.shields.io/badge/Python-Data_Processing-green.svg)](https://www.python.org/)
[![DAX](https://img.shields.io/badge/DAX-Analytics-orange.svg)](https://docs.microsoft.com/en-us/dax/)

## 🎯 Project Overview

**CreditFlow Analytics** is a comprehensive credit card financial intelligence platform that transforms raw transaction data into actionable business insights. Built for financial institutions, analysts, and decision-makers, this dashboard provides real-time monitoring of credit card operations, customer behavior patterns, and revenue optimization opportunities.

## ✨ Key Features

- **📊 Real-Time Dashboard**: Weekly automated reporting with instant KPI updates
- **🔍 Customer Intelligence**: Deep-dive analytics on customer demographics and behavior
- **💰 Revenue Optimization**: Transaction analysis with profitability insights
- **🎯 Risk Management**: Delinquency tracking and activation rate monitoring
- **📈 Trend Analysis**: Year-over-year and week-over-week performance comparison
- **🌍 Geographic Insights**: State-wise revenue and customer distribution analysis

## 🏗️ Architecture

```
📁 Credit Card Data Sources
    ├── 📊 Customer Demographics (cust_detail)
    ├── 📊 Credit Card (csv_detail)
    ├── 💳 Transaction Records (cc_detail)
    └── 🔄 Weekly Updates (automated)
           ↓
    🗄️  PostgreSQL Database
           ↓
    ⚡ DAX Processing & Calculations
           ↓
    📈 Power BI Interactive Dashboard
```

## 📈 Dashboard Highlights

### 📊 Customer Analytics Dashboard
- **Customer Segmentation**: Age groups, income brackets, education levels
- **Geographic Distribution**: Top performing states (TX, NY, CA, FL, NJ)
- **Demographics Analysis**: Gender-based revenue patterns
- **Satisfaction Metrics**: Customer satisfaction score tracking

### 💳 Transaction Intelligence Dashboard
- **Revenue Streams**: $55.4M total revenue with detailed breakdowns
- **Transaction Analysis**: 657K+ transactions across multiple categories
- **Payment Behavior**: Chip vs Swipe vs Online usage patterns
- **Category Performance**: Bills, Entertainment, Fuel, Grocery, Food, Travel

## 🔧 Technical Implementation

### Database Schema
```sql
-- Customer Details Table
CREATE TABLE cust_detail (
    Client_Num INT,
    Customer_Age INT,
    Gender VARCHAR(5),
    Education_Level VARCHAR(50),
    Income INT,
    -- ... additional fields
);

-- Credit Card Details Table
CREATE TABLE cc_detail (
    Client_Num INT,
    Card_Category VARCHAR(20),
    Total_Trans_Amt INT,
    Interest_Earned DECIMAL(10,3),
    -- ... additional fields
);
```

### Key DAX Calculations
```dax
-- Revenue Calculation
Revenue = 'cc_detail'[annual_fees] + 'cc_detail'[total_trans_amt] + 'cc_detail'[interest_earned]

-- Week-over-Week Growth
Current_week_Revenue = CALCULATE(
    SUM('cc_detail'[Revenue]),
    FILTER(ALL('cc_detail'), 'cc_detail'[week_num2] = MAX('cc_detail'[week_num2]))
)

-- Customer Segmentation
AgeGroup = SWITCH(
    TRUE(),
    'cust_detail'[customer_age] < 30, "20-30",
    'cust_detail'[customer_age] < 40, "30-40",
    'cust_detail'[customer_age] < 50, "40-50",
    'cust_detail'[customer_age] < 60, "50-60",
    "60+"
)
```

## 🚀 Getting Started

### Prerequisites
- PostgreSQL Database
- Power BI Desktop
- Python (for data processing)

### Installation Steps

1. **Database Setup**
```bash
# Create database
CREATE DATABASE ccdb;

# Run SQL scripts
psql -d ccdb -f "SQL Query - Financial Dashboard Data.sql"
```

2. **Data Import**
```bash
# Import customer data
COPY cust_detail FROM 'customer.csv' DELIMITER ',' CSV HEADER;

# Import credit card data  
COPY cc_detail FROM 'credit_card.csv' DELIMITER ',' CSV HEADER;

# Import additional weekly data
COPY cc_detail FROM 'cc_add.csv' DELIMITER ',' CSV HEADER;
COPY cust_detail FROM 'cust_add.csv' DELIMITER ',' CSV HEADER;
```

3. **Power BI Configuration**
- Connect Power BI to PostgreSQL database
- Import DAX calculations
- Configure dashboard layouts
- Set up automated refresh

## 📊 Key Performance Insights

### Week 53 (Dec 31, 2023) Performance:
- **Revenue Growth**: +28.8% Week-over-Week
- **Total Revenue**: $55.4M YTD
- **Interest Earned**: $7.9M
- **Transaction Volume**: $46M
- **Customer Distribution**: Male customers contribute 55% ($31M) vs Female 45% ($26M)

### Card Category Performance:
- **Blue Cards**: 93% of total transactions (dominant segment)
- **Silver Cards**: Secondary growth driver
- **Gold/Platinum**: Premium segment with higher revenue per customer

### Geographic Insights:
- **Top 3 States**: TX, NY, CA contribute 68% of total revenue
- **Activation Rate**: 57.5% overall
- **Delinquency Rate**: 6.06% (within acceptable range)

## 🎯 Business Applications

### 💼 For Financial Executives
- **Strategic Planning**: Revenue trend analysis for quarterly planning
- **Risk Assessment**: Delinquency and activation rate monitoring
- **Market Expansion**: Geographic performance analysis for new market entry

### 📈 For Marketing Teams
- **Customer Segmentation**: Targeted campaigns based on demographics
- **Product Development**: Card category performance insights
- **Retention Strategies**: Customer satisfaction and behavior analysis

### 🔍 For Data Analysts
- **Advanced Analytics**: Custom DAX calculations for complex metrics
- **Trend Analysis**: Historical data patterns and forecasting
- **Operational Intelligence**: Real-time monitoring and alerting

## 📁 Repository Structure

```
CreditFlow-Analytics/
├── 📊 data/
│   ├── cc_add.csv                    # Weekly transaction updates
│   ├── cust_add.csv                  # Weekly customer updates
│   └── dataset_documentation/
├── 🗄️ database/
│   └── SQL Query - Financial Dashboard Data.sql
├── 📈 dashboards/
│   ├── Credit Card Financial Dashboard-Customer.pdf
│   ├── Credit Card Financial Dashboard-Transaction.pdf
│   └── Credit Card Financial Weekly Dashboard Report.pdf
├── 📝 documentation/
└── 🔧 scripts/
    └── data_processing_utilities/
```

## 🚀 Advanced Features

### Real-Time Updates
- **Automated Data Refresh**: Weekly data pipeline
- **Live Dashboard**: Real-time KPI monitoring
- **Alert System**: Threshold-based notifications

### Custom Analytics
- **Cohort Analysis**: Customer lifetime value tracking
- **Predictive Modeling**: Churn prediction and revenue forecasting
- **Seasonality Analysis**: Quarterly and monthly trend identification

## 🤝 Contributing

We welcome contributions to enhance CreditFlow Analytics! Areas for contribution:

- **New Visualizations**: Additional chart types and interactive elements
- **Advanced Analytics**: Machine learning integration
- **Performance Optimization**: Query and dashboard performance improvements
- **Documentation**: Enhanced user guides and tutorials

### How to Contribute
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/EnhancedAnalytics`)
3. Commit your changes (`git commit -m 'Add customer churn prediction'`)
4. Push to the branch (`git push origin feature/EnhancedAnalytics`)
5. Open a Pull Request

## 📚 Resources & References

- **Power BI Documentation**: [Microsoft Power BI Learning Path](https://docs.microsoft.com/en-us/power-bi/)
- **DAX Reference**: [DAX Function Reference](https://docs.microsoft.com/en-us/dax/)
- **SQL Best Practices**: [PostgreSQL Documentation](https://www.postgresql.org/docs/)

## 📄 License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.

## 🎖️ Resume Addition

```
Credit Card Financial Intelligence Dashboard:
• Developed an interactive Power BI dashboard analyzing 657K+ credit card transactions 
  and customer data, delivering real-time insights for $55.4M revenue tracking
• Implemented automated ETL pipeline with PostgreSQL and DAX calculations, reducing 
  manual reporting time by 80% and enabling weekly stakeholder updates  
• Created customer segmentation analysis across demographics, geography, and behavior 
  patterns, supporting targeted marketing campaigns and risk management strategies
• Delivered actionable insights resulting in 28.8% week-over-week revenue growth 
  tracking and improved activation rate monitoring
```

---

**Transform your credit card data into competitive advantage with CreditFlow Analytics!** 🚀

*Built with ❤️ for the financial analytics community*
