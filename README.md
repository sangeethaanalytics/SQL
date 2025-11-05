Welcome to my **SQL Practice Repository!**  
This repo contains my hands-on SQL exercises for learning and improving database skills.  
Each task includes the **scenario**, **SQL query**, and **expected output**.
## 📋 Table of Contents

## 🏥 SQL Question 1 – CREATE TABLE

**Scenario:**  
You are a data analyst at **City Hospital**.  
Management wants to create a new table to store patient details.

**Task:**  
Write a SQL command to create a table named **`Patients`** with the following fields:  
- `PatientID`  
- `PatientName`  
- `Age`  
- `Gender`  
- `AdmissionDate`

**SQL Query:**

```sql
CREATE TABLE Patients (
    PatientID INT PRIMARY KEY,
    PatientName VARCHAR(100) NOT NULL,
    Age INT,
    Gender CHAR(1),
    AdmissionDate DATE
);
Expected Output:
table 'Patients' created successfully.

## 🩺 SQL Question 2 – ALTER TABLE (Add Column)

**Scenario:**  
Later, the hospital decides to store the doctor assigned to each patient.

**Task:**  
Write a SQL command to add a new column `DoctorAssigned` (data type `VARCHAR(50)`) to the `Patients` table.

**SQL Query:**
```sql
ALTER TABLE Patients
ADD DoctorAssigned VARCHAR(50);


# 📚 SQL Question 3 – PRIMARY KEY & FOREIGN KEY

**Scenario:**  
You are creating a database for an **online bookstore**.  
The system needs two tables:  
- `Books` → to store book details  
- `Orders` → to store order details  

**Task:**  
Define:
- A **Primary Key** for `Books(BookID)`  
- A **Foreign Key** in `Orders(BookID)` referencing `Books(BookID)`

---

**SQL Query:**
```sql
-- Creating Books table with PRIMARY KEY
CREATE TABLE Books (
    BookID INT PRIMARY KEY,
    Title VARCHAR(100),
    Author VARCHAR(100),
    Price DECIMAL(10,2)
);

-- Creating Orders table with FOREIGN KEY
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    OrderDate DATE,
    BookID INT,
    Quantity INT,
    FOREIGN KEY (BookID) REFERENCES Books(BookID)
);

## 📘 SQL Question 4 – UNIQUE Constraint

**Scenario:**  
Each book in the **Books** table must have a unique ISBN number to prevent duplicates.

**Task:**  
Add a `UNIQUE` constraint to the `ISBN` column in the `Books` table.

---

**SQL Query:**
```sql
-- Step 1: Add a new column for ISBN (if not already present)
ALTER TABLE Books
ADD ISBN VARCHAR(20);

-- Step 2: Apply UNIQUE constraint to ensure no duplicate ISBNs
ALTER TABLE Books
ADD CONSTRAINT unique_isbn UNIQUE (ISBN);


# 🗑️ SQL Question 5 – DELETE vs TRUNCATE

**Scenario:**  
The bookstore wants to remove *test orders* from the `Orders` table.  
Sometimes, they only want to delete **specific rows**, while other times, they want to clear **all data** but keep the table structure.

---

**Task:**  
Demonstrate:
1. `DELETE` with a `WHERE` clause — to remove selected rows.  
2. `TRUNCATE` — to remove all rows quickly.

---

**SQL Query:**
```sql
-- 1️⃣ Delete only specific rows (e.g., test orders)
DELETE FROM Orders
WHERE OrderID = 101;

-- 2️⃣ Remove all rows but keep table structure
TRUNCATE TABLE Orders;
Expected Output:

sql

DELETE: 1 row deleted successfully.
TRUNCATE: Table 'Orders' emptied successfully.

Example:

Before DELETE:

OrderID	OrderDate	BookID	Quantity
101	2023-09-15	1	2
102	2023-09-17	2	1

After DELETE WHERE OrderID = 101
→ Only Order 101 is deleted.

After TRUNCATE TABLE Orders
→ Table is empty, but columns and structure remain intact.

📤 Result:

DELETE → removes selected data.

TRUNCATE → clears all data, preserving the table structure.


## 🎓 SQL Question 6 – DISTINCT & WHERE

**Scenario:**  
In a **university database**, you want to list all **unique department names** from the `Departments` table.  
You may also want to filter based on a condition later using `WHERE`.

---

**Task:**  
Write a SQL query to return **distinct** department names.

---

**SQL Query:**
```sql
SELECT DISTINCT DepartmentName
FROM Departments;

## 📧 SQL Question 7 – IS NULL & NOT NULL

**Scenario:**  
In the **Students** table, some students don’t have their email addresses recorded yet.  
You need to identify which students **have** and **don’t have** email addresses.

---

**Task:**  
Write two queries:
1. Find students **with NULL emails** (not recorded).  
2. Find students **with NOT NULL emails** (email provided).

---

**SQL Query:**
```sql
-- 1️⃣ Students with no email recorded
SELECT StudentID, StudentName
FROM Students
WHERE Email IS NULL;

-- 2️⃣ Students with an email address
SELECT StudentID, StudentName, Email
FROM Students
WHERE Email IS NOT NULL;

## 🎯 SQL Question 8 – IN, BETWEEN, and NOT BETWEEN

**Scenario:**  
In the **Students** table, you want to filter students:
- Enrolled in specific courses  
- Or within certain GPA ranges  

You’ll use `IN`, `BETWEEN`, and `NOT BETWEEN` operators to fetch the correct subsets.

---

**Task:**  
Write SQL queries that:
1. Return students enrolled in selected courses using `IN`  
2. Return students with GPA between 7.0 and 9.0 using `BETWEEN`  
3. Return students with GPA outside that range using `NOT BETWEEN`

---

**SQL Query:**
```sql
-- 1️⃣ Students enrolled in specific courses
SELECT StudentID, StudentName, Course
FROM Students
WHERE Course IN ('Data Science', 'AI', 'SQL');

-- 2️⃣ Students with GPA between 7 and 9
SELECT StudentID, StudentName, GPA
FROM Students
WHERE GPA BETWEEN 7.0 AND 9.0;

-- 3️⃣ Students with GPA outside 7–9 range
SELECT StudentID, StudentName, GPA
FROM Students
WHERE GPA NOT BETWEEN 7.0 AND 9.0;


## 🛒 SQL Question 9 – ORDER BY & LIMIT

**Scenario:**  
In an **e-commerce system**, management wants to see the **top 3 highest-priced products** from the `Products` table.

---

**Task:**  
Write a SQL query using `ORDER BY` and `LIMIT` to display the top 3 products by price.

---

**SQL Query:**
```sql
SELECT ProductID, ProductName, Price
FROM Products
ORDER BY Price DESC
LIMIT 3;

## 💰 SQL Question 10 – Aggregate Functions (COUNT, SUM, AVG, MAX, MIN)

**Scenario:**  
In the **Sales** table, management wants to see key **statistics** — like total sales, average sales, highest and lowest sales values, and number of transactions.

---

**Task:**  
Write SQL queries using **COUNT**, **SUM**, **AVG**, **MAX**, and **MIN** functions to calculate these statistics.

---

**SQL Query:**
```sql
-- 1️⃣ Total number of sales transactions
SELECT COUNT(SaleID) AS Total_Transactions
FROM Sales;

-- 2️⃣ Total sales amount
SELECT SUM(SaleAmount) AS Total_Sales
FROM Sales;

-- 3️⃣ Average sale amount
SELECT AVG(SaleAmount) AS Average_Sale
FROM Sales;

-- 4️⃣ Highest sale amount
SELECT MAX(SaleAmount) AS Highest_Sale
FROM Sales;

-- 5️⃣ Lowest sale amount
SELECT MIN(SaleAmount) AS Lowest_Sale
FROM Sales;

## 🏢 SQL Question 11 – GROUP BY & HAVING

**Scenario:**  
In the **Employees** table, management wants to identify **departments that have more than 10 employees**.

---

**Task:**  
Write a SQL query using `GROUP BY` and `HAVING` to find departments with employee count greater than 10.

---

**SQL Query:**
```sql
SELECT DepartmentID, COUNT(EmployeeID) AS Total_Employees
FROM Employees
GROUP BY DepartmentID
HAVING COUNT(EmployeeID) > 10;

## 🎓 SQL Question 12 – INNER JOIN

**Scenario:**  
In a university database, you want to display **students along with the names of the courses** they are enrolled in.

There are two tables:  
- `Students(StudentID, StudentName, CourseID)`  
- `Courses(CourseID, CourseName)`

---

**Task:**  
Write a SQL query to join both tables and show students with their course names.

---

**SQL Query:**
```sql
SELECT 
    s.StudentID, 
    s.StudentName, 
    c.CourseName
FROM Students s
INNER JOIN Courses c
    ON s.CourseID = c.CourseID;

## 🧩 SQL Question 13 – LEFT JOIN & RIGHT JOIN

**Scenario:**  
In a university database, you need to list **all students and their enrolled courses**, including those who haven’t enrolled yet — and also show **all courses**, even those that have no students.

There are two tables:  
- `Students(StudentID, StudentName, CourseID)`  
- `Enrollments(CourseID, CourseName)`

---

**Task:**  
Use `LEFT JOIN` and `RIGHT JOIN` between `Students` and `Enrollments` to show:
- All students (even if they don’t have a course)  
- All courses (even if no students are enrolled)

---

**SQL Query:**
```sql
-- 1️⃣ LEFT JOIN – Shows all students (even without a course)
SELECT 
    s.StudentID,
    s.StudentName,
    e.CourseName
FROM Students s
LEFT JOIN Enrollments e
    ON s.CourseID = e.CourseID;

-- 2️⃣ RIGHT JOIN – Shows all courses (even without enrolled students)
SELECT 
    s.StudentID,
    s.StudentName,
    e.CourseName
FROM Students s
RIGHT JOIN Enrollments e
    ON s.CourseID = e.CourseID;

## 👥 SQL Question 3 – UNION vs UNION ALL

**Scenario:**  
In a company database, you have two tables:
- `CurrentEmployees(EmployeeID, EmployeeName)`
- `PastEmployees(EmployeeID, EmployeeName)

**Task:**  
Write SQL queries demonstrating the difference between `UNION` and `UNION ALL`.

---

**SQL Query:**
```sql
-- 1️⃣ Using UNION (removes duplicates)
SELECT EmployeeName FROM CurrentEmployees
UNION
SELECT EmployeeName FROM PastEmployees;

-- 2️⃣ Using UNION ALL (keeps duplicates)
SELECT EmployeeName FROM CurrentEmployees
UNION ALL
SELECT EmployeeName FROM PastEmployees;

## 🧾 SQL Question 1 – String Functions (UPPER, LOWER, SUBSTRING, CONCAT)

**Scenario:**  
In the **Employees** table, management wants to clean up and format employee names properly for reports.

---

**Task:**  
Write SQL queries using string functions:
- `UPPER()` – convert text to uppercase  
- `LOWER()` – convert text to lowercase  
- `SUBSTRING()` – extract part of a string  
- `CONCAT()` – combine multiple strings  

---

**SQL Query:**
```sql
-- 1️⃣ Convert all employee names to uppercase
SELECT UPPER(EmployeeName) AS Uppercase_Name
FROM Employees;

-- 2️⃣ Convert all employee names to lowercase
SELECT LOWER(EmployeeName) AS Lowercase_Name
FROM Employees;
-- 3️⃣ Extract first 3 letters of each employee name
SELECT SUBSTRING(EmployeeName, 1, 3) AS ShortName
FROM Employees;

-- 4️⃣ Concatenate first and last name with a space
SELECT CONCAT(FirstName, ' ', LastName) AS FullName
FROM Employees;


## ⏳ SQL Question 2 – Date Functions (YEAR, DATEDIFF, NOW)

**Scenario:**  
In the **Employees** table, management wants to calculate how long each employee has been working (their **tenure in years**).

---

**Task:**  
Write SQL queries using date functions such as:
- `YEAR()` – extracts year from a date  
- `DATEDIFF()` – calculates difference between two dates  
- `NOW()` – returns the current system date  

---

**SQL Query:**
```sql
-- 1️⃣ Calculate employee tenure using DATEDIFF
SELECT 
    EmployeeName,
    HireDate,
    DATEDIFF(NOW(), HireDate) / 365 AS Tenure_Years
FROM Employees;

-- 2️⃣ Extract year of hiring
SELECT 
    EmployeeName,
    YEAR(HireDate) AS Year_Hired
FROM Employees;

-- 3️⃣ Display current date
SELECT NOW() AS Current_Date;


## 🧠 SQL Question 3 – User-Defined Function (UDF)

**Scenario:**  
In a **Students** database, you want to create a **reusable function** that returns each student's **full name** by combining their first and last names.

---

**Task:**  
Write and test a **User-Defined Function (UDF)** that concatenates `FirstName` and `LastName` to form the full name.

---

**SQL Query:**
```sql
-- 1️⃣ Create the user-defined function
DELIMITER $$

CREATE FUNCTION GetFullName(FirstName VARCHAR(50), LastName VARCHAR(50))
RETURNS VARCHAR(100)
DETERMINISTIC
BEGIN
    RETURN CONCAT(FirstName, ' ', LastName);
END$$

DELIMITER ;

-- 2️⃣ Test the function
SELECT 
    StudentID,
    GetFullName(FirstName, LastName) AS FullName
FROM Students;

Scenario:
Hr wants to quickly fetch an employees details using theri ID.

Task:
create a stored procedure that accepts an employeeid and returns that employees details

** SQL query 4 stored procedure
Delimiter
create procedure getemployeedetails(in emp_id int)
begin select employee_id,
first_name,
last_name,
department_id,
salary from employee_id= emp_id;
end;
delimiter;
call getemployeedetails(101);

SQL query 5 simple view
scenario:
management wants a view showing employee names and their department names.
Task
create a view for that
Sql query
creat view employeedepartmentviewas
select e.employee_name,
d.department_name,
from employees e
join departments d on e.department_id= d.department_id;

SQL query 6 complex view
scenario:
To create a view joining employees,departments,and salaries tables to show combined info.
Task:
write sql for a complex 
create view employeefullinfo as
select e.employee id,
e.employee_name,
d.department_name,
s.salary_amount,
s.bonus
from employees e
join departments d on e.department_id=d.department_id
join salaries s on e.employee_id=s.employee_id;

SQL Trigger
scenario: log every deletion in the orders table.
Task: write a trigger to insert deleted rows into order_history
Sql query
create trigger trg_afterorderdate after delete on orders for each row
begin
insert into order_history(orderid,customerid,orderdate,totalamount,deletedat)
values(old.orderid,old.customerid,old.orderdate,
old.totalamount,now());
end;

sql question: DCL
scenario:grant reporting access to junior analysts
Task: write sql using grant and revoke commands
sql query
---grant select permission on reports table
grant select on reports to 'junior_analyst';
revoke select on reports from 'junior_analyst';


sql question : TCL
Scenario: during a bank transfer,ensure atomicity
Task: write sql using commit,rollback,savepoint
sql query
start transcation;
update accounts
set balance= balance-5000
where accountid=101;
savepoint after_debit;
update accounts
set balance=balance+5000
where accountid=202;
rollback to after_debit;
commit;
