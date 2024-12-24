### **SQL**

#### **Objective**:  
Master SQL to manage databases, retrieve data efficiently, and build dynamic applications.

---

### **Step 1: Installation**

1. **Choose a SQL Database**:  
   - **MySQL** (Recommended for beginners):  
     - Download from [mysql.com](https://www.mysql.com). Install MySQL Community Edition.  
     - Install **MySQL Workbench** for GUI-based operations.  

   - **Alternatives**:  
     - PostgreSQL ([postgresql.org](https://www.postgresql.org)).  
     - SQLite (lightweight, pre-installed on Python).  

2. **Verify Installation**:  
   - Open terminal or command prompt. Run:  
     ```bash
     mysql --version
     ```

3. **Access the SQL Shell**:  
   - MySQL:  
     ```bash
     mysql -u root -p
     ```

4. **Setup a Database User**:  
   ```sql
   CREATE USER 'user'@'localhost' IDENTIFIED BY 'password';
   GRANT ALL PRIVILEGES ON *.* TO 'user'@'localhost';
   FLUSH PRIVILEGES;
   ```

---

### **Step 2: Setup and Tools**

1. **Command-Line Interface**:  
   - Use the MySQL shell: `mysql -u username -p`.  

2. **Graphical Interface**:  
   - Use **MySQL Workbench** or **pgAdmin** (for PostgreSQL).  

3. **File Structure for Scripts**:  
   - Save SQL scripts as `.sql` files. Execute using:  
     ```bash
     mysql -u user -p < script.sql
     ```

4. **Connect from Python**:  
   Install `mysql-connector-python`:  
   ```bash
   pip install mysql-connector-python
   ```

---

### **Step 3: SQL Basics**

#### 1. **Core Commands**:  
- **Create a Database**:  
   ```sql
   CREATE DATABASE my_database;
   USE my_database;
   ```

- **Create a Table**:  
   ```sql
   CREATE TABLE users (
       id INT AUTO_INCREMENT PRIMARY KEY,
       name VARCHAR(100),
       email VARCHAR(100) UNIQUE,
       created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
   );
   ```

- **Insert Data**:  
   ```sql
   INSERT INTO users (name, email) VALUES ('John Doe', 'john@example.com');
   ```

- **Select Data**:  
   ```sql
   SELECT * FROM users;
   ```

- **Update Data**:  
   ```sql
   UPDATE users SET name = 'Jane Doe' WHERE id = 1;
   ```

- **Delete Data**:  
   ```sql
   DELETE FROM users WHERE id = 1;
   ```

---

#### 2. **Data Types**:  
- **Numeric**: `INT`, `FLOAT`, `DECIMAL`.  
- **String**: `VARCHAR`, `TEXT`.  
- **Date/Time**: `DATE`, `DATETIME`, `TIMESTAMP`.  

---

#### 3. **Advanced Queries**:  
- **Filter Data**:  
   ```sql
   SELECT * FROM users WHERE name LIKE '%Doe%';
   ```

- **Sort Results**:  
   ```sql
   SELECT * FROM users ORDER BY created_at DESC;
   ```

- **Aggregate Functions**:  
   ```sql
   SELECT COUNT(*) AS user_count FROM users;
   SELECT AVG(salary) FROM employees;
   ```

- **Group Data**:  
   ```sql
   SELECT department, COUNT(*) FROM employees GROUP BY department;
   ```

- **Joins**:  
   ```sql
   SELECT orders.id, users.name, orders.total
   FROM orders
   INNER JOIN users ON orders.user_id = users.id;
   ```

- **Subqueries**:  
   ```sql
   SELECT name FROM users WHERE id = (SELECT MAX(id) FROM users);
   ```

---

### **Step 4: Data Integrity**

1. **Constraints**:  
   - `PRIMARY KEY`: Unique identifier for rows.  
   - `FOREIGN KEY`: Relate tables.  
   - `NOT NULL`: Disallow empty values.  
   - `UNIQUE`: Ensure all values in a column are unique.  

   Example:  
   ```sql
   CREATE TABLE orders (
       id INT AUTO_INCREMENT PRIMARY KEY,
       user_id INT,
       total DECIMAL(10, 2),
       FOREIGN KEY (user_id) REFERENCES users(id)
   );
   ```

2. **Indexes**:  
   Improve query performance:  
   ```sql
   CREATE INDEX idx_email ON users(email);
   ```

---

### **Step 5: Projects (Beginner to Intermediate)**

#### **Project 1: User Management System**  
**Goal**: Create a table to manage users.  
**Steps**:  
1. Create a database:  
   ```sql
   CREATE DATABASE user_management;
   USE user_management;
   ```

2. Create a `users` table:  
   ```sql
   CREATE TABLE users (
       id INT AUTO_INCREMENT PRIMARY KEY,
       name VARCHAR(100),
       email VARCHAR(100) UNIQUE,
       password VARCHAR(100),
       created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
   );
   ```

3. Insert sample users:  
   ```sql
   INSERT INTO users (name, email, password) 
   VALUES ('John Doe', 'john@example.com', 'password123');
   ```

4. Query data:  
   ```sql
   SELECT * FROM users;
   ```

---

#### **Project 2: Inventory Management**  
**Goal**: Track products in inventory.  
**Steps**:  
1. Create a `products` table:  
   ```sql
   CREATE TABLE products (
       id INT AUTO_INCREMENT PRIMARY KEY,
       name VARCHAR(100),
       quantity INT,
       price DECIMAL(10, 2),
       created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
   );
   ```

2. Add products:  
   ```sql
   INSERT INTO products (name, quantity, price)
   VALUES ('Laptop', 10, 899.99), ('Mouse', 50, 19.99);
   ```

3. Query low-stock items:  
   ```sql
   SELECT * FROM products WHERE quantity < 20;
   ```

---

#### **Project 3: Library Management System**  
**Goal**: Track books and borrowing.  
**Steps**:  
1. Create tables:  
   ```sql
   CREATE TABLE books (
       id INT AUTO_INCREMENT PRIMARY KEY,
       title VARCHAR(255),
       author VARCHAR(100),
       available INT DEFAULT 1
   );

   CREATE TABLE borrow_logs (
       id INT AUTO_INCREMENT PRIMARY KEY,
       book_id INT,
       user_id INT,
       borrow_date DATE,
       return_date DATE,
       FOREIGN KEY (book_id) REFERENCES books(id)
   );
   ```

2. Insert sample data:  
   ```sql
   INSERT INTO books (title, author) 
   VALUES ('1984', 'George Orwell'), ('To Kill a Mockingbird', 'Harper Lee');
   ```

3. Query borrowed books:  
   ```sql
   SELECT books.title, borrow_logs.borrow_date
   FROM borrow_logs
   INNER JOIN books ON books.id = borrow_logs.book_id;
   ```

---

#### **Project 4: Employee Attendance Tracker**  
**Goal**: Track attendance by day.  
**Steps**:  
1. Create a table:  
   ```sql
   CREATE TABLE attendance (
       id INT AUTO_INCREMENT PRIMARY KEY,
       employee_id INT,
       date DATE,
       status ENUM('Present', 'Absent', 'Late')
   );
   ```

2. Insert attendance records:  
   ```sql
   INSERT INTO attendance (employee_id, date, status)
   VALUES (1, '2024-01-01', 'Present');
   ```

3. Query attendance by employee:  
   ```sql
   SELECT employee_id, COUNT(*) AS days_present
   FROM attendance
   WHERE status = 'Present'
   GROUP BY employee_id;
   ```

---

#### **Project 5: Reporting Dashboard (SQL + Python)**  
**Goal**: Combine SQL with Python for data visualization.  
**Steps**:  
1. Write a SQL query:  
   ```sql
   SELECT department, COUNT(*) AS employee_count
   FROM employees
   GROUP BY department;
   ```

2. Fetch data using Python:  
   ```python
   import mysql.connector
   import pandas as pd

   conn = mysql.connector.connect(
       host="localhost", user="root", password="password", database="company"
   )
   query = "SELECT department, COUNT(*) AS employee_count FROM employees GROUP BY department"
   df = pd.read_sql(query, conn)
   print(df)
   ```

---

### **Final Notes**
1. **Master Query Optimization**: Learn indexing, `EXPLAIN`, and partitioning for faster queries.  
2. **Expand with Advanced Concepts**:  
   - Stored Procedures, Views, Triggers.  
   - Database Normalization (1NF, 2NF, 3NF).  

SQL is **indispensable** for managing structured data. Practice projects like these to build real-world applications. 
