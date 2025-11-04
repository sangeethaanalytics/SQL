Welcome to my **SQL Practice Repository!**  
This repo contains my hands-on SQL exercises for learning and improving database skills.  
Each task includes the **scenario**, **SQL query**, and **expected output**.
## 📋 Table of Contents
1. [SQL Question 1 – CREATE TABLE](#sql-question-1--create-table)
SQL Question 1: CREATE Table
Scenario:
 You are a data analyst at City Hospital. Management wants to create a new table to store patient details.
Task:
 Write a SQL command to create a table named Patients with fields (PatientID, PatientName, Age, Gender, AdmissionDate).
Expected Output:**


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

