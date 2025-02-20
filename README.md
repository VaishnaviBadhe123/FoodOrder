
# Food Order System (Like Zomato)

## Overview

This project implements a food ordering system, similar to popular platforms like Zomato or UberEats, which allows customers to browse through various restaurants, place orders, provide reviews, and track deliveries—all in one centralized system. The system offers an efficient platform for customers to explore, order, and interact with restaurants and delivery personnel.

## Problem Statement

Traditional food ordering systems often face the following challenges:

* *Limited options for customers:* Consumers often struggle to explore diverse restaurant choices on a single platform.
* *Errors in phone-based orders:* Miscommunication during phone-based orders often results in incorrect orders.
* *Lack of real-time tracking:* Customers lack real-time updates on the status of their orders and deliveries.
* *Inefficient payments:* Customers find it hard to track payments, and restaurants often don't have a seamless way to handle them.
* *Scattered reviews:* Reviews for dishes and restaurants are scattered, making it hard for customers to make informed decisions.

## *Features*

* *Restaurant Browsing:* Browse a variety of restaurants along with cuisine details, ratings, and locations.
* *Menu Display:* View detailed restaurant menus with dish descriptions, prices, and images.
* *Order Placement:* Place an order with multiple dishes in a single transaction.
* *Order Tracking:* Track order status (Pending, Confirmed, Shipped, Delivered) and delivery progress.
* *User Reviews:* Customers can leave ratings and comments for restaurants and dishes.
* *Admin Panel:* Admins can manage restaurants, dishes, users, and orders from a centralized dashboard.
* *Online Payment:* A seamless online payment system with transaction tracking.
* *Delivery Management:* Track and manage delivery personnel and their assignments.
* *Notifications:* Alerts for order status updates, payment confirmations, etc.

## *Database Schema (MySQL)*

This food order system uses a MySQL database with the following tables:

* *Restaurants*: Stores information about restaurants such as name, address, cuisine type, and ratings.
* *Users*: Contains user information including username, password, email, phone, and address.
* *Dishes*: Stores dish details such as name, description, price, and the associated restaurant.
* *Orders*: Details of each order, including the user, restaurant, order time, total amount, status, payment ID, and delivery ID.
* *Order_Items*: Represents the items ordered (dishes) in each order.
* *Reviews*: Reviews left by users for dishes and restaurants, including rating and comments.
* *Payment*: Contains payment information for the orders, such as payment method and transaction ID.
* *Delivery_Personnel*: Stores details of delivery personnel (name, phone, vehicle type).
* *Delivery*: Stores information about the delivery, including the order ID, delivery person, delivery status, and delivery time.
* *Admins*: Admin user details, such as their username, password, email, and phone.



## *Setup Instructions*

1. *Install MySQL*: Make sure MySQL is installed and running on your machine or server.
2. *Create a Database*: Create a new database for the food order system.
   sql
   CREATE DATABASE FoodOrderSystem;
   
3. *Import the Schema*: Execute the provided SQL schema script to create the necessary tables.
4. *Insert Sample Data*: Use the provided SQL INSERT queries to populate the database with sample data.
5. *Configure Your Application*: (If creating a web application) Configure the database connection settings in your application to connect to the database.
6. *Run the Application*: Launch the application and use the food order system for restaurant browsing, placing orders, payment, and delivery tracking.

## *Example Queries (MySQL)*

* *View Restaurant Menu*:
   This query lists all dishes offered by a restaurant.
   sql
   SELECT Dishes.name, Dishes.description, Dishes.price
   FROM Dishes
   WHERE Dishes.restaurant_id = 1;
   

* *View Orders for a User*:
   This query shows all orders placed by a user.
   sql
   SELECT Orders.order_id, Restaurants.name, Orders.total_amount, Orders.status
   FROM Orders
   JOIN Restaurants ON Orders.restaurant_id = Restaurants.restaurant_id
   WHERE Orders.user_id = 1;
   

* *View Reviews for a Restaurant*:
   This query displays reviews left by users for a specific restaurant.
   sql
   SELECT Users.username, Reviews.rating, Reviews.comment
   FROM Reviews
   JOIN Users ON Reviews.user_id = Users.user_id
   WHERE Reviews.restaurant_id = 1;
   

* *Top Rated Restaurants*:
   This query finds the top-rated restaurants based on their average review ratings.
   sql
   SELECT r.name, r.cuisine, AVG(rev.rating) AS average_rating
   FROM Restaurants r
   JOIN Reviews rev ON r.restaurant_id = rev.restaurant_id
   GROUP BY r.restaurant_id, r.name, r.cuisine
   ORDER BY average_rating DESC;
   

* *Most Popular Dishes*:
   This query shows the top 10 most ordered dishes based on order counts.
   sql
   SELECT d.name, COUNT(*) AS order_count
   FROM Dishes d
   JOIN Order_Items oi ON d.dish_id = oi.dish_id
   GROUP BY d.dish_id, d.name
   ORDER BY order_count DESC
   LIMIT 10;
   

## *Contributing*

Contributions to the system are welcome! Here's how you can contribute:

1. *Fork the Repository*: Create a fork of the project on GitHub to make changes.
2. *Submit a Pull Request*: After making improvements or fixing bugs, submit a pull request to the main repository.
3. *Bug Reports*: If you encounter any bugs or have feature requests, feel free to open an issue on the GitHub repository.
4. *Testing*: If you’re adding new features or making significant changes, please ensure that the system is thoroughly tested, especially the payment and delivery tracking features.

---

### *Conclusion*
The *Food Order System* provides a robust platform for customers, restaurants, and admins to efficiently manage orders, payments, reviews, and deliveries in a user-friendly interface. By utilizing a well-structured database and SQL queries, the system ensures a seamless user experience, while allowing admins to manage restaurant listings, orders, and user interactions.
