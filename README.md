# FoodHub Order Data Analysis (EDA)

## 1. Business Objective
This project is an exploratory data analysis (EDA) for FoodHub, a food aggregator company in New York. The goal is to analyze 1,898 order records to understand customer behavior, restaurant performance, and operational logistics. The insights from this analysis are intended to help the company enhance customer experience and improve business operations.

## 2. Tools & Technologies
* **Data Manipulation:** `pandas`, `numpy`
* **Data Visualization:** `matplotlib`, `seaborn`
* **Environment:** Jupyter Notebook

## 3. Data Cleaning & Preparation
* **`rating` Column:** The `rating` column was loaded as an `object` type because unrated orders were marked "Not given". This was converted to `np.nan` (736 total) and the column was cast to `float`.
* **`restaurant_name` Column:** Names were standardized to lowercase to ensure accurate grouping.
* **Feature Engineering:** A new column, `total_wait_time`, was created by summing `food_preparation_time` and `delivery_time` to analyze the complete customer wait experience.

## 4. Key Findings & Insights

### Customer & Order Profile
* **High Demand:** The analysis covered **1,898** unique orders from **1,200** unique customers, indicating a healthy rate of repeat orders.
* **Top Customers:** The top 3 most frequent customers (IDs `52832`, `47440`, `83287`) placed 13, 10, and 9 orders, respectively.
* **Weekend Peak:** **71%** of all orders are placed on the **weekend**, showing a clear behavioral trend.
* **Order Cost:** **29%** of orders cost more than $20.

### Restaurant & Cuisine Performance
* **Top Restaurants (by Order Volume):**
    1.  Shake Shack (219 orders)
    2.  The Meatball Shop (132 orders)
    3.  Blue Ribbon Sushi (119 orders)
* **Most Popular Cuisine:** **American** is the most frequently ordered cuisine, followed by Japanese, Italian, and Chinese.

### Operational Metrics
* **Average Times:**
    * Food Preparation: 27.5 minutes
    * Delivery Time: 24.2 minutes
* **Revenue:** A tiered commission (25% for orders >$20, 15% for orders >$5) was calculated, resulting in a **net revenue of $6,166.30** from this dataset.
* **A Key Insight:** Delivery time was found to be **slower on weekdays (avg. 28 min)** than on weekends (avg. 22 min), despite weekends having 2.5x the order volume.
* **Service Gaps:** **10.5%** of all orders took **more than 60 minutes** from placement to delivery. Multivariate analysis showed a negative correlation between `total_wait_time` and `rating`.

## 5. Actionable Recommendations

1.  **Investigate Weekday Delivery:** The data shows that delivery, not food prep, is the bottleneck on weekdays. The company should investigate weekday delivery logistics and staffing to reduce this 6-minute delay.
2.  **Address Long Wait Times:** With 10.5% of orders taking over an hour and this wait time negatively impacting ratings, this is a key area for improvement. Focus on the restaurants and routes that contribute most to this delay.
3.  **Launch Targeted Promotions:**
    * **Restaurants:** The analysis identified four restaurants eligible for a "high-performer" promotion (rating count > 50, avg. rating > 4): **Shake Shack, The Meatball Shop, Blue Ribbon Sushi, and Blue Ribbon Fried Chicken**.
    * **Customers:** Offer loyalty rewards to the top 3 customers to encourage retention.
4.  **Improve Data Collection:** The rating system is flawed (no 1 or 2-star ratings, 39% of orders unrated). The business should implement a 1-5 star system and encourage feedback to gather more actionable data on poor experiences.
5.  **Capitalize on Strengths:** Continue to build strong partnerships with top-performing American and Japanese restaurants (like Shake Shack) that drive the most volume and revenue, especially on weekends.
