1.How many pizzas were ordered?
SELECT count(order_id) as total_pizza_ordered
FROM customer_orders; 

2. How many unique customer orders were made?
SELECT COUNT(DISTINCT order_id) as unique_orders
FROM customer_orders;


3.How many successful orders were delivered by each runner?
SELECT runner_id,
       COUNT(runner_id) AS successful_orders
FROM runner_orders
WHERE cancellation IS NULL
GROUP BY runner_id

What was the maximum number of pizzas delivered in a single order?
SELECT c.order_id, 
       COUNT(c.order_id) as number_order
FROM customer_orders as c 
RIGHT JOIN runner_orders as r ON c.order_id = r.order_id
WHERE r.cancellation is NULL
GROUP BY c.order_id
ORDER BY number_order DESC
LIMIT 1;
