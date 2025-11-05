# SQL Data Filtering for Cybersecurity

## Project Description
This project demonstrates my ability to filter data using SQL in a cybersecurity context. As part of a hands-on lab in the Google Cybersecurity Certificate program, I worked with a simulated MariaDB database containing employee and login activity data. My objective was to investigate potential security incidents and support system updates by writing SQL queries that use AND, OR, and NOT operators. These queries reflect real-world tasks such as identifying failed logins, isolating department-specific users, and filtering by time, date, and location.

## Task 1: Retrieve After-Hours Failed Login Attempts
To identify failed login attempts that occurred after business hours (after 18:00), I used the AND operator. The success column stores Boolean values, where 0 represents a failed attempt. This query helps isolate potentially unauthorized access attempts.

```sql
SELECT * FROM log_in_attempts WHERE login_time > '18:00:00' AND success = 0;
```

## Task 2: Retrieve Login Attempts on Specific Dates
To investigate a suspicious event on May 9, 2022, I retrieved all login attempts from that day and the day before. I used the OR operator to filter for both dates.

```sql
SELECT * FROM log_in_attempts WHERE login_date = '2022-05-09' OR login_date = '2022-05-08';
```

## Task 3: Retrieve Login Attempts Outside of Mexico
To exclude login attempts originating from Mexico, I used the NOT and LIKE operators. I filtered out any values starting with "MEX".

```sql
SELECT * FROM log_in_attempts WHERE NOT country LIKE 'MEX%';
```

## Task 4: Retrieve Employees in Marketing
To find employees in the Marketing department in the East building, I used AND and LIKE to match offices starting with "East". This helps target specific employees for machine updates.

```sql
SELECT * FROM employees WHERE department = 'Marketing' AND office LIKE 'East-%';
```

## Task 5: Retrieve Employees in Finance or Sales
To retrieve employees in either the Finance or Sales departments, I used the OR operator.

```sql
SELECT * FROM employees WHERE department = 'Finance' OR department = 'Sales';
```

## Task 6: Retrieve All Employees Not in IT
To find all employees not in the Information Technology department, I used the NOT operator. This is a practical step in staged rollouts.

```sql
SELECT * FROM employees WHERE NOT department = 'Information Technology';
```

## Summary
This lab gave me practical experience in writing SQL queries that filter data based on multiple conditions. I used AND, OR, and NOT operators to retrieve failed login attempts, filter by date and time, and isolate employee records. These queries reflect real-world tasks in cybersecurity investigations, including threat detection, access auditing, and asset management.