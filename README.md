# ANARIX: AI-Powered E-commerce Analytics Platform

🚀 **ANARIX** is an advanced AI-powered analytics platform that transforms e-commerce data into actionable insights through natural language queries, real-time visualizations, and intelligent data processing.

## 🌟 Overview

ANARIX leverages Google's Gemini AI to provide a conversational interface for complex e-commerce data analysis. Users can ask questions in plain English and receive comprehensive answers backed by SQL queries, visualizations, and formatted business intelligence reports.

## ✨ Key Features

### 🤖 AI-Powered Natural Language Querying
- **Conversational Interface**: Ask questions in plain English about your e-commerce data
- **Intelligent SQL Generation**: Automatically converts natural language to optimized SQL queries
- **Context-Aware Responses**: Understands business metrics like ROAS, CPC, and conversion rates
- **Fallback Mechanisms**: Manual SQL mapping for common queries when API limits are reached

### 📊 Advanced Data Visualization
- **Cost Per Click (CPC) Analysis**: Bar charts showing top-performing products
- **Return on Ad Spend (ROAS) Visualization**: Performance metrics for advertising campaigns
- **Ad Spend vs Sales Correlation**: Scatter plots revealing spending effectiveness  
- **Promotion Eligibility Distribution**: Pie charts for product categorization

### 🔄 Real-Time Streaming Capabilities
- **Live Response Streaming**: Real-time AI response generation with typing effects
- **Interactive Event Handling**: User interruption support during long operations
- **Performance Metrics**: Detailed tracking of streaming performance and response times
- **Multiple Streaming Modes**: Quick response and detailed analysis modes

### 🗄️ Robust Data Management
- **Multi-Table Support**: Handles ad sales, total sales, and product eligibility data
- **SQLite Integration**: In-memory database for fast query processing
- **Automatic Schema Generation**: Dynamic database structure creation
- **Data Validation**: Built-in error handling and data integrity checks

## 📋 Prerequisites

### Required Software
- Python 3.7+
- Google Colab (recommended) or Jupyter Notebook
- Google Gemini API access

### Required Python Packages
```bash
pip install pandas google-generativeai sqlalchemy matplotlib
```

### Data Files Required
The system expects three CSV files with specific naming conventions:
- `Product-Level Ad Sales and Metrics (mapped) - Product-Level Ad Sales and Metrics (mapped).csv`
- `Product-Level Total Sales and Metrics (mapped) - Product-Level Total Sales and Metrics (mapped).csv`  
- `Product-Level Eligibility Table (mapped) - Product-Level Eligibility Table (mapped).csv`

## 🚀 Quick Start

### 1. Setup API Access
```python
# In Google Colab, add your API key to secrets:
# Left sidebar -> Secrets -> Add 'GEMINI_API_KEY'

from google.colab import userdata
GEMINI_API_KEY = userdata.get('GEMINI_API_KEY')
genai.configure(api_key=GEMINI_API_KEY)
```

### 2. Load Your Data
Upload your three CSV files to the Colab environment. The system will automatically:
- Load data into pandas DataFrames
- Create SQLite database tables
- Generate database schema for AI context

### 3. Start Querying
```python
# Ask questions in natural language
user_question = "What is my total sales revenue?"
response = ask_ai_agent(user_question, conn, db_schema)
print(response)
```

## 💡 Example Queries

### Business Intelligence Questions
- "What is my total sales revenue?"
- "Calculate the Return on Ad Spend (ROAS)"
- "Which product had the highest Cost Per Click?"
- "Show me all products not eligible for promotions"
- "What's the average conversion rate by product category?"

### Advanced Analytics
- "Compare ad spend efficiency across product lines"
- "Identify underperforming products with high ad spend"
- "Show seasonal trends in product performance"
- "Calculate profit margins by product segment"

## 🛠️ Core Components

### Database Tables
| Table | Description | Key Metrics |
|-------|-------------|-------------|
| `ad_sales_metrics` | Advertising performance data | ad_spend, ad_sales, clicks, impressions |
| `total_sales_metrics` | Overall sales performance | total_sales, revenue, conversion_rate |
| `product_eligibility` | Product promotion status | eligibility, product_category |

### Key Functions

#### `ask_ai_agent(question, db_connection, schema)`
Main AI interface that processes natural language questions and returns formatted answers.

#### `ask_ai_agent_with_fallback(question, db_connection, schema)`
Enhanced version with retry logic and manual SQL fallback for API limitations.

#### `visualize_cpc(db_connection)`
Generates horizontal bar charts for Cost Per Click analysis.

#### `visualize_sales_metrics(db_connection)`
Creates ROAS charts and ad spend correlation visualizations.

#### `enhanced_streaming_response(prompt, model)`
Provides real-time streaming responses with event handling and user interaction.

## 📈 Visualization Gallery

### Available Chart Types
- **Bar Charts**: Product performance rankings
- **Scatter Plots**: Correlation analysis between metrics
- **Pie Charts**: Category distribution and eligibility status
- **Interactive Dashboards**: Real-time metric updates

### Business Metrics Supported
- **ROAS (Return on Ad Spend)**: Revenue generated per advertising dollar
- **CPC (Cost Per Click)**: Average cost for each click on advertisements
- **Conversion Rates**: Percentage of visitors who make purchases
- **Revenue Trends**: Time-series analysis of sales performance

## 🔧 Advanced Configuration

### Streaming Settings
```python
# Configure streaming behavior
enhanced_streaming_response(
    prompt="Your question here",
    model=gemini_model,
    simulate_realtime=True,      # Enable typing effect
    enable_interruption=True     # Allow user to interrupt
)
```

### Error Handling
The system includes comprehensive error handling for:
- API rate limiting with exponential backoff
- Database connection issues
- Invalid SQL query generation
- Missing or corrupted data files

### Manual SQL Fallbacks
When API limits are reached, the system automatically falls back to pre-configured SQL queries for common business questions.

## 🎯 Use Cases

### E-commerce Analytics
- **Performance Monitoring**: Track key metrics across product lines
- **Campaign Optimization**: Identify high-performing advertising strategies
- **Inventory Management**: Analyze product eligibility and sales patterns
- **Revenue Forecasting**: Predict future sales based on historical data

### Business Intelligence
- **Executive Reporting**: Generate automated insights for leadership
- **Operational Analytics**: Monitor day-to-day business performance
- **Strategic Planning**: Data-driven decision making support
- **Competitive Analysis**: Benchmark performance against industry standards

## 🔒 Security & Best Practices

### API Key Management
- Store API keys in Google Colab secrets (never hardcode)
- Use environment variables for local development
- Implement key rotation policies for production use

### Data Privacy
- Process data in isolated environments
- Implement data anonymization where required
- Follow GDPR and other privacy regulations

## 🐛 Troubleshooting

### Common Issues

**API Rate Limiting**
- Solution: System automatically retries with exponential backoff
- Fallback: Manual SQL queries for common questions

**Data Loading Errors**
- Check CSV file names match expected format exactly
- Verify date columns are properly formatted
- Ensure no missing required columns

**Visualization Issues**
- Confirm matplotlib is properly installed
- Check for sufficient data points in queries
- Verify database connections are active

### Debug Mode
Enable detailed logging by setting:
```python
import logging
logging.basicConfig(level=logging.DEBUG)
```

## 🤝 Contributing

We welcome contributions to improve ANARIX! Please consider:
- Adding new visualization types
- Expanding the manual SQL fallback library
- Improving natural language processing capabilities  
- Enhancing error handling and user experience

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- Google Gemini AI for natural language processing
- Matplotlib for visualization capabilities
- Pandas for data manipulation and analysis
- SQLAlchemy for database operations
