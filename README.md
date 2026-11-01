Customer Shopping Behavior Analysis

An end-to-end data analytics project that explores how customers shop, using Python, PostgreSQL, Power BI and Gamma. It covers the full workflow: data loading, EDA, cleaning, SQL analysis, dashboarding, reporting and presentation.

Overview

Retailers need to understand who their customers are, what they buy and what drives spending. This project analyzes 3,900 customer transactions to answer questions such as:

Which customer groups generate the most revenue?
Do subscribers or discount users spend more?
Which products and categories perform best?
How loyal is the customer base?

Key numbers: 3,900 customers | $233,081 total revenue | $59.76 average purchase | 3.75 average review rating

Dataset
Source file: customer_shopping_behavior.csv
Size: 3,900 rows × 18 columns
Type	Columns
Customer	Customer ID, Age, Gender, Location, Subscription Status
Product	Item Purchased, Category, Size, Color, Season
Purchase	Purchase Amount (USD), Discount Applied, Promo Code Used, Payment Method, Shipping Type
Behavior	Review Rating, Previous Purchases, Frequency of Purchases
Tools & Technologies
Purpose	Tool
Data loading, EDA, cleaning	Python (Pandas) in Jupyter Notebook
Database	PostgreSQL (via SQLAlchemy, psycopg2)
Visualization	Power BI Desktop
Reporting	Microsoft Word
Presentation	Gamma (AI presentation tool)
Project Steps
Load data: read the CSV into a Pandas DataFrame.
EDA: inspected the data with head(), info(), describe() and null counts.
Clean data:
Filled 37 missing Review Ratings with the median rating of each category.
Standardized column names (lowercase, underscores).
Dropped promo_code_used because it was identical to discount_applied.
Feature engineering:
age_group: 4 quartile-based groups (Young Adult, Adult, Middle-age, Senior).
purchase_frequency_days: converted frequency labels to days.
Load into PostgreSQL: wrote the cleaned data to a customer table.
SQL analysis: answered 10 business questions (see below).
Dashboard: built an interactive Power BI dashboard.
Report and presentation: wrote a full project report and created slides with Gamma.
SQL Business Questions
#	Question
1	Revenue by gender
2	Discount users who still spent above average
3	Top 5 products by average rating
4	Average spend: Standard vs. Express shipping
5	Subscribers vs. non-subscribers (spend and revenue)
6	Top 5 products by discount rate
7	Customer segmentation (New / Returning / Loyal)
8	Top 3 products in each category
9	Are repeat buyers more likely to subscribe?
10	Revenue by age group

SQL techniques used: aggregations, GROUP BY, subqueries, CTEs, CASE WHEN, window functions (ROW_NUMBER).

Dashboard

An interactive Power BI dashboard with:

KPI cards: number of customers, average review rating, average purchase amount
Charts: subscription share, revenue and sales by category, revenue and sales by age group
Slicers: subscription status, gender, category, shipping type

Dashboard

Results
Clothing leads revenue ($104K, about 45%), followed by Accessories (about 32%).
Male customers contribute about 68% of revenue, in line with their share of customers. Average spend per order is nearly the same for both genders.
Subscribers spend about the same as non-subscribers ($59.49 vs. $59.87), so the subscription program adds little spending value today.
80% of customers are "Loyal" (more than 10 previous purchases); only 2% are new.
Young Adults (18–31) are the top revenue group.
Express shipping customers spend about $2 more per order than Standard.
Discounts don't raise spend. Average spend is $59.28 with a discount vs. $60.13 without.
Repeat buyers are not more likely to subscribe (27.6% vs. 27% overall).
Recommendations
Prioritize Clothing and Accessories in inventory and marketing.
Redesign subscription perks to make them worthwhile.
Use discounts selectively on slow-moving items.
Launch acquisition campaigns to grow the new-customer segment.
How to Run
1. Clone the repository
bash
git clone https://github.com/<your-username>/customer-shopping-behavior.git
cd customer-shopping-behavior
2. Install requirements
bash
pip install pandas sqlalchemy psycopg2-binary jupyter
3. Run the notebook

Open Customer_Behavior.ipynb in Jupyter and run all cells. This cleans the data and loads it into PostgreSQL.

Set your own PostgreSQL credentials in the connection cell. Do not commit passwords to GitHub. Use environment variables or a .env file.

python
engine = create_engine("postgresql+psycopg2://<user>:<password>@localhost:5432/customer_behavior")
4. Run the SQL queries

Create a database named customer_behavior, then run Customer_Behavior_PostgreSQL.sql in pgAdmin or psql.

5. Open the dashboard

Open Customer_Behavior_Dashboard.pbix in Power BI Desktop. If needed, refresh the data source to point to your local PostgreSQL or the cleaned CSV.

Repository Structure
├── data/
│   └── customer_shopping_behavior.csv
├── notebooks/
│   └── Customer_Behavior.ipynb
├── sql/
│   └── Customer_Behavior_PostgreSQL.sql
├── dashboard/
│   └── Customer_Behavior_Dashboard.pbix
├── images/
│   └── dashboard.png
├── report/
│   └── Customer_Shopping_Behavior_Report.docx
├── presentation/
│   └── Customer_Shopping_Behavior_PPT (Gamma link or PDF)
└── README.md
Future Improvements
Customer clustering (K-Means) for deeper segmentation
Predictive model for subscription or high-spend customers
Live dashboard connected directly to PostgreSQL
Author

Shravan
