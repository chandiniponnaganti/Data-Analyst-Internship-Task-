SQL Queries
1️⃣ Create Table & Insert Sample Data
CREATE TABLE online_sales (
    order_id INT,
    order_date DATE,
    amount DECIMAL(10,2),
    product_id INT
);

INSERT INTO online_sales (order_id, order_date, amount, product_id) VALUES
(101, '2024-01-15', 2500.00, 1),
(102, '2024-01-18', 1800.00, 2),
(103, '2024-02-10', 2200.00, 3),
(104, '2024-02-21', 4100.00, 1),
(105, '2024-03-03', 3100.00, 4),
(106, '2024-03-29', 2800.00, 2),
(107, '2024-04-10', 5000.00, 5),
(108, '2024-04-19', 3300.00, 3),
(109, '2024-05-05', 7500.00, 2),
(110, '2024-05-22', 4200.00, 4);

2️⃣ Monthly Revenue & Order Volume
SELECT
    YEAR(order_date) AS year,
    MONTH(order_date) AS month,
    SUM(amount) AS monthly_revenue,
    COUNT(DISTINCT order_id) AS order_volume
FROM
    online_sales
GROUP BY
    YEAR(order_date),
    MONTH(order_date)
ORDER BY
    year, month;

3️⃣ Top 3 Months by Sales
SELECT
    YEAR(order_date) AS year,
    MONTH(order_date) AS month,
    SUM(amount) AS monthly_revenue
FROM
    online_sales
GROUP BY
    YEAR(order_date),
    MONTH(order_date)
ORDER BY
    monthly_revenue DESC
LIMIT 3;

📊 Sample Output
year	month	monthly_revenue	order_volume
2024	1	4300.00	2
2024	2	6300.00	2
2024	3	5900.00	2
2024	4	8300.00	2
2024	5	11700.00	2
