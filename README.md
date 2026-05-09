# zomato-restaurant-analysis
📌 Project Overview
This project analyzes 148 restaurants from the Zomato dataset to uncover insights about ratings, costs, online ordering trends, and dining types using SQL queries in Google Colab, followed by an interactive Power BI dashboard.

📊 Key Findings

148 restaurants analyzed across multiple dining types
Average Rating: 4.0 | Average Cost for Two: ₹418
Total Votes: 39K+ across all restaurants
60% of restaurants accept online orders
Dining type has the highest average cost at ₹800+
Buffet type has the lowest average cost


🛠️ Tools & Technologies
ToolPurposePython (Pandas)Data loading and cleaningSQLiteSQL querying in Google ColabMatplotlib & SeabornPython visualizationsPower BIInteractive dashboardGoogle ColabDevelopment environment

📁 Project Structure
zomato-restaurant-analysis/
│
├── Untitled22.ipynb          # Main Colab notebook
├── zomato_cleaned.csv        # Cleaned dataset
├── zomato_dashboard.pbix     # Power BI dashboard file
└── README.md

🪜 Project Workflow
Step 1 — Data Loading

Loaded Zomato CSV dataset into Google Colab
Explored shape, column names, and data types

Step 2 — Data Cleaning

Renamed messy columns: approx_cost(for two people) → cost, listed_in(type) → type
Cleaned rate column: removed /5 suffix, converted to float
Cleaned cost column: removed commas, converted to integer
Checked and handled NULL values and duplicate rows

Step 3 — SQLite Database

Created SQLite in-memory database using sqlite3
Pushed cleaned pandas DataFrame as SQL table
Verified data load with SELECT queries

Step 4 — SQL Analysis
Answered key business questions using SQL:
sql-- Top 10 restaurants by votes
SELECT name, votes FROM restaurants 
ORDER BY votes DESC LIMIT 10

-- Average cost by dining type
SELECT type, ROUND(AVG(cost), 2) AS avg_cost 
FROM restaurants GROUP BY type ORDER BY avg_cost DESC

-- Online order vs average rating
SELECT online_order, ROUND(AVG(rate), 2) AS avg_rating 
FROM restaurants GROUP BY online_order

-- Best value restaurants (high rating + low cost)
SELECT name, rate, cost FROM restaurants 
WHERE rate >= 4.0 AND cost <= 500 
ORDER BY rate DESC
Step 5 — Visualizations

Online order distribution (Pie chart)
Top 10 restaurants by votes (Bar chart)
Average cost by dining type (Bar chart)
Rating distribution (Histogram)
High rating vs low cost scatter plot

Step 6 — Power BI Dashboard

4 KPI cards: Total Restaurants, Avg Rating, Avg Cost, Total Votes
Top 10 restaurants by votes (Bar chart)
Cost vs dining type (Bar chart)
Online order distribution (Pie chart)
Interactive slicers: Online Order, Types of Restaurants


📂 Dataset
Source: Zomato Dataset — Kaggle
