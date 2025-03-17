# **Amazon Sales Data Analysis - Buyer Preferences**

## **📌 Project Overview**

This beginner-friendly Python data analysis project aims to analyze Amazon sales data to determine **buyers' preferred choices** in sales. The analysis will focus on identifying the most purchased **categories, products, brands, and price ranges** to gain insights into customer behavior.

## **📊 Features & Goals**

- Analyze the **most popular product categories**.
- Identify **best-selling products**.
- Find **top brands by sales volume**.
- Determine the **preferred price range of buyers**.
- Use **data visualization** to present insights.

## **📂 Dataset**

### **1. Sample Data Structure** (CSV Format)

| Order ID | Product Name | Category    | Brand   | Price | Quantity | Rating | Purchase Date |
| -------- | ------------ | ----------- | ------- | ----- | -------- | ------ | ------------- |
| 101      | iPhone 13    | Electronics | Apple   | 999   | 2        | 4.8    | 2024-01-12    |
| 102      | Nike Shoes   | Fashion     | Nike    | 120   | 1        | 4.5    | 2024-01-13    |
| 103      | Samsung TV   | Electronics | Samsung | 799   | 1        | 4.6    | 2024-01-15    |

### **2. Data Source**

- Download a dataset from [Kaggle](https://www.kaggle.com/) or [Data.world](https://data.world/).
- Use **web scraping** (BeautifulSoup/Selenium) to collect real-time Amazon data (optional).

## **🛠️ Tech Stack & Libraries**

- **Python**
- **Pandas** - Data manipulation
- **NumPy** - Numerical operations
- **Matplotlib** & **Seaborn** - Data visualization

## **🚀 Installation & Setup**

### **1. Install Dependencies**

```bash
pip install pandas numpy matplotlib seaborn
```

### **2. Load & Explore Data**

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Load dataset
df = pd.read_csv("amazon_sales.csv")
print(df.head())  # View first few rows
```

## **🔍 Data Cleaning & Preprocessing**

```python
# Remove missing values
df.dropna(inplace=True)

# Convert Purchase Date to datetime format
df['Purchase Date'] = pd.to_datetime(df['Purchase Date'])
```

## **📊 Data Analysis & Visualization**

### **1. Most Purchased Categories**

```python
top_categories = df['Category'].value_counts().head(5)
sns.barplot(x=top_categories.index, y=top_categories.values, palette="viridis")
plt.title("Top 5 Best-Selling Categories")
plt.xlabel("Category")
plt.ylabel("Number of Purchases")
plt.show()
```

### **2. Best-Selling Products**

```python
top_products = df.groupby('Product Name')['Quantity'].sum().sort_values(ascending=False).head(5)
sns.barplot(x=top_products.index, y=top_products.values, palette="coolwarm")
plt.xticks(rotation=45)
plt.title("Top 5 Best-Selling Products")
plt.xlabel("Product Name")
plt.ylabel("Total Quantity Sold")
plt.show()
```

### **3. Top Brands by Sales**

```python
top_brands = df.groupby('Brand')['Quantity'].sum().sort_values(ascending=False).head(5)
sns.barplot(x=top_brands.index, y=top_brands.values, palette="magma")
plt.title("Top 5 Brands by Sales")
plt.xlabel("Brand")
plt.ylabel("Total Quantity Sold")
plt.show()
```

### **4. Buyer’s Preferred Price Range**

```python
sns.histplot(df['Price'], bins=20, kde=True, color='blue')
plt.title("Distribution of Product Prices")
plt.xlabel("Price ($)")
plt.ylabel("Number of Purchases")
plt.show()
```

## **📢 Insights & Recommendations**

- **Electronics** is the most purchased category.
- **Apple & Samsung** dominate the best-selling brands.
- Most purchases fall within the **\$100-\$500** price range.
- Business can focus on **discounts & promotions** for high-demand categories.

## **💾 Save Cleaned Data**

```python
df.to_csv("cleaned_amazon_sales.csv", index=False)
```

## **📌 Future Enhancements**

- Implement **machine learning** to predict future sales trends.
- Use **web scraping** to fetch live Amazon sales data.
- Build an **interactive dashboard** using Streamlit or Tableau.

Happy Coding! 😊

