CREATE DATABASE IF NOT EXISTS doordash;

USE doordash;

CREATE TABLE IF NOT EXISTS restaurants (
    restaurant_id INT AUTO_INCREMENT PRIMARY KEY,
    restaurant_name VARCHAR(100) NOT NULL,
    restaurant_address VARCHAR(100) NOT NULL,
    restaurant_PhoNumber VARCHAR(50) NOT NULL UNIQUE,
    restaurant_status ENUM('open', 'closed') NOT NULL
);

CREATE TABLE IF NOT EXISTS menu (
    menu_id INT AUTO_INCREMENT PRIMARY KEY,
    menu_name VARCHAR(50) NOT NULL UNIQUE,
    menu_description VARCHAR(200) NOT NULL,
    menu_price DECIMAL(10, 2) NOT NULL,
    restaurant_id INT,
    CONSTRAINT fk_menu_restaurants FOREIGN KEY (restaurant_id) REFERENCES restaurants(restaurant_id)
);

CREATE TABLE IF NOT EXISTS customer (
    customer_id INT AUTO_INCREMENT PRIMARY KEY,
    customer_name VARCHAR(60) NOT NULL,
    customer_PhoNumber VARCHAR(50) NOT NULL UNIQUE
);

CREATE TABLE IF NOT EXISTS address (
    address_id INT AUTO_INCREMENT PRIMARY KEY,
    address_delivery VARCHAR(100) NOT NULL,
    customer_id INT,
    CONSTRAINT fk_address_customer FOREIGN KEY (customer_id) REFERENCES customer(customer_id)
);

CREATE TABLE IF NOT EXISTS drivers (
    driver_id INT AUTO_INCREMENT PRIMARY KEY,
    driver_plate VARCHAR(50) NOT NULL
);

CREATE TABLE IF NOT EXISTS orders (
    order_id INT AUTO_INCREMENT PRIMARY KEY,
    status ENUM('pending', 'preparing', 'out_for_delivery', 'delivered', 'cancelled') NOT NULL DEFAULT 'pending',
    date_purchased TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    address_id INT NOT NULL,
    driver_id INT NOT NULL,
    CONSTRAINT fk_order_address FOREIGN KEY (address_id) REFERENCES address(address_id),
    CONSTRAINT fk_order_driver FOREIGN KEY (driver_id) REFERENCES drivers(driver_id)
);

CREATE TABLE IF NOT EXISTS orders_menu (
    order_id INT NOT NULL,
    menu_id INT NOT NULL,
    quantity INT NOT NULL,
    price_purchased DECIMAL(10, 2) NOT NULL,
    CONSTRAINT fk_order_menu FOREIGN KEY (menu_id) REFERENCES menu(menu_id),
    CONSTRAINT fk_order_order FOREIGN KEY (order_id) REFERENCES orders(order_id)
);