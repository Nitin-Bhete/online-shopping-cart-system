Online Shopping Cart System
A full-stack Java web application built from scratch using the MVC (Model-View-Controller) architecture. It handles user authentication, product catalog browsing, session-based cart management, and order placement connected to a MySQL backend.

Overview
This project was built to practice core enterprise Java web development without relying on high-level frameworks like Spring Boot. It uses native Java Servlets to route traffic, JSP with JSTL for view rendering, and raw JDBC via the DAO pattern to talk directly to MySQL.

Tech Stack
Language: Java (JDK 17)

Backend: Java Servlets, JSP, JSTL

Database: MySQL

Connectivity: JDBC with PreparedStatement

Server: Apache Tomcat v9.0

Build Tool: Apache Maven

Frontend: HTML5, CSS3, Bootstrap 4, JavaScript

Architecture & Project Structure
The project follows a standard 3-tier MVC pattern:

Plaintext
src/main/java
 ├── com.ecommerce.connection   # DB connection singleton (DbCon.java)
 ├── com.ecommerce.dao          # Data Access Objects (UserDao, ProductDao, OrderDao)
 ├── com.ecommerce.model        # Plain Java models / Beans (User, Product, Order, Cart)
 └── com.ecommerce.servlet      # HTTP controllers (LoginServlet, CartServlet, CheckoutServlet, etc.)
src/main/webapp
 ├── index.jsp                  # Main product catalog
 ├── cart.jsp                   # Active shopping cart view
 ├── orders.jsp                 # Order history page
 ├── login.jsp / register.jsp   # Authentication forms
 └── includes/                  # Reusable navbars, headers, and footer components
Model: Handles entity states and data encapsulation.

View: JSP pages styled with Bootstrap, rendering data sent from the servlets.

Controller: Servlets intercepting HTTP GET/POST requests, updating sessions, and redirecting or forwarding requests.

Key Features
User Authentication: Login and registration forms with credential checks against the MySQL database.

Session Cart: Uses the native HTTPSession API to track a user's cart across page reloads without requiring an account login right away.

Product Catalog: Displays products dynamically with prices, categories, and inventory statuses.

Order Processing: Validates cart contents, calculates final amounts, creates order records, and clears the cart session upon successful checkout.

Security: All database queries use parameterized SQL via PreparedStatement to guard against SQL injection.

Database Setup
Open your MySQL client (e.g., MySQL Workbench or MySQL CLI).

Create the database:

SQL
CREATE DATABASE shopping_cart;
USE shopping_cart;
Run your table creation scripts for users, products, orders, and order_items.

Update your local credentials in src/main/java/com/ecommerce/connection/DbCon.java:

Java
String url = "jdbc:mysql://localhost:3306/shopping_cart";
String user = "root";
String password = "your_mysql_password";
How to Run Locally
Prerequisites
JDK 17 installed and configured (JAVA_HOME set in environment variables)

Apache Maven

Apache Tomcat v9.0

MySQL Server running on port 3306

Steps
Clone the repository:

Bash
git clone https://github.com/Nitin-Bhete/online-shopping-cart-system.git
cd online-shopping-cart-system
Build the WAR file with Maven:

Bash
mvn clean package
This generates shopping-cart.war inside the target/ directory.

Deploy to Tomcat:

Via Eclipse / IntelliJ: Import as an Existing Maven Project, add Apache Tomcat 9.0 as a Server runtime, right-click the project, and select Run As > Run on Server.

Via Standalone Tomcat: Copy the generated .war file into Tomcat's webapps/ folder, then run bin/startup.bat (Windows) or bin/startup.sh (Linux/Mac).

Access the application:
Open your browser and navigate to:

Plaintext
http://localhost:8080/shopping-cart/

Author

Nitin Bhete
