CREATE DATABASE ECommerceSite ; 
USE ECommerceSite;

CREATE TABLE Users (
    id UUID Primary Key,
    name Varchar(200) NOT NULL,
    email Varchar(200) NOT NULL UNIQUE,
    password TEXT NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
)

CREATE TABLE Products(
    id UUID Primary Key,
    name Varchar(100) NOT NULL ,
    price int NOT NULL ,
    description TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
)

CREATE TABLE Orders(
    id UUID Primary Key,
    user_id UUID REFERENCES Users(id),
    product_id UUID REFERENCES Products(id),
    quantity int NOT NULL,
    total_price int NOT NULL,
    order_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP
)

CREATE TABLE Order_Items(
    id UUID Primary Key,
    order_id UUID REFERENCES Orders(id),
    product_id UUID REFERENCES Products(id),
    quantity int NOT NULL,
    price int NOT NULL,
)

FOREIGN KEY (user_id) REFERENCES Users(id),
FOREIGN KEY (product_id) REFERENCES Products(id),
FOREIGN KEY (order_id) REFERENCES Orders(id),
FOREIGN KEY (product_id) REFERENCES Products(id)   

// List all orders with customer names

SELECT Orders.id, Users.name
FROM Orders
JOIN Users ON Orders.user_id = Users.id;

// List products in each order.

SELECT Orders.id , Products.name 
FROM Order_Items
JOIN Products ON Order_Items.product_id = Products.id; 

// Show the total number of orders placed by each customer.

SELECT Users.name, COUNT(Orders.id) AS total-orders
FROM Users
LEFT JOIN Orders ON Users.id = Orders.user_id
GROUP BY Users.name;


