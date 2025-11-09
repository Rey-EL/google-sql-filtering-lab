# google-sql-filtering-lab

This project showcases my ability to use SQL for cybersecurity investigations, a hands-on lab from the Google Cybersecurity Certificate program. The goal was to query a simulated employee database to identify security events and support system administration tasks.

---

## Objective

To investigate potential security incidents by writing SQL queries to filter a database of employee records and login attempts. This involved using `AND`, `OR`, and `NOT` operators to isolate specific data points relevant to a security analyst.

---

## Demonstrated SQL Techniques

Below are examples of the queries written during the lab, demonstrating different filtering techniques.

### 1. Filtering by Time and Status
**Goal:** Identify potentially unauthorized access by finding failed login attempts that occurred after business hours (18:00).

```sql
SELECT * FROM log_in_attempts WHERE login_time > '18:00:00' AND success = 0;
```

### 2. Filtering by Date Range
**Goal:** Investigate a security event by retrieving all login activity from a specific date and the day prior.

```sql
SELECT * FROM log_in_attempts WHERE login_date = '2022-05-09' OR login_date = '2022-05-08';
```

### 3. Excluding by Location
**Goal:** Narrow an investigation by excluding all login attempts originating from a specific country (Mexico).

```sql
SELECT * FROM log_in_attempts WHERE NOT country LIKE 'MEX%';
```

### 4. Filtering by Department and Office
**Goal:** Support a targeted system update by identifying all employees in the Marketing department who work in an "East" building office.

```sql
SELECT * FROM employees WHERE department = 'Marketing' AND office LIKE 'East-%';
```

### 5. Filtering for Multiple Departments
**Goal:** Retrieve a list of all employees working in either the Finance or Sales departments.

```sql
SELECT * FROM employees WHERE department = 'Finance' OR department = 'Sales';
```

### 6. Excluding a Department
**Goal:** Create a list of all employees *not* in the IT department, often a necessary step for planning phased software rollouts.

```sql
SELECT * FROM employees WHERE NOT department = 'Information Technology';
```

---

## Summary of Skills

This lab provided practical experience in using fundamental SQL `WHERE` clauses to support cybersecurity functions. The key skills demonstrated include:
*   **Threat Hunting:** Isolating suspicious login patterns based on time, date, and location.
*   **Data Auditing:** Retrieving specific records to verify user activity.
*   **Asset Management:** Filtering employee lists to support targeted system updates and policy enforcement.

---

## Security Considerations

While this lab focuses on using SQL for investigative purposes, it is crucial to remember that SQL databases are often targets of attacks. One of the most critical vulnerabilities is **SQL Injection**, listed in the OWASP Top 10. In real-world applications, it is vital to use parameterized queries or prepared statements to prevent SQL Injection attacks, rather than concatenating user input directly into SQL queries. This practice ensures that user input is treated as data, not executable code, thereby protecting the database from malicious manipulation.

---

## License

This project is licensed under the [MIT License](./LICENSE.md) - see the LICENSE.md file for details.

---

## Contributing

Contributions are welcome! If you have suggestions for improvements or want to enhance the lab, please feel free to open an issue or submit a pull request.
