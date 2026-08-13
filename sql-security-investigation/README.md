# SQL Security Investigation & Data Filtering

## Project Overview

This project demonstrates the use of SQL queries and filtering techniques to perform security-related investigations and retrieve specific information from organizational data.

The investigation focused on login attempts and employee information using the `log_in_attempts` and `employees` tables.

## Objective

The objective was to use SQL filtering techniques to investigate potential security issues, identify suspicious login activity, and retrieve employee information required for security updates.

## Investigations Performed

### 1. Failed Login Attempts After Business Hours

Investigated failed login attempts that occurred after 18:00.

**SQL techniques used:**

* `WHERE`
* `AND`
* Comparison operators
* Boolean filtering

The query filtered login attempts where the login time was after 18:00 and the login attempt was unsuccessful.

### 2. Login Attempts on Specific Dates

Investigated login activity that occurred on May 9, 2022, and May 8, 2022.

**SQL techniques used:**

* `WHERE`
* `OR`
* Date filtering

The query returned login attempts occurring on either of the specified dates.

### 3. Login Attempts Outside Mexico

Investigated login attempts originating from countries other than Mexico.

**SQL techniques used:**

* `WHERE`
* `NOT`
* `LIKE`
* `%` wildcard

The `LIKE` operator and `%` wildcard were used because the dataset represented Mexico using values beginning with `MEX`, including `MEX` and `MEXICO`.

### 4. Employees in Marketing

Retrieved information about employees in the Marketing department located in the East building.

**SQL techniques used:**

* `WHERE`
* `AND`
* `LIKE`
* `%` wildcard

The query filtered employees based on both department and office location.

### 5. Employees in Finance or Sales

Retrieved information about employees belonging to either the Finance or Sales department.

**SQL techniques used:**

* `WHERE`
* `OR`

The `OR` operator was used because employees from either department were required.

### 6. Employees Outside IT

Retrieved information about employees who were not part of the Information Technology department.

**SQL techniques used:**

* `WHERE`
* `NOT`

The query filtered the employee data to exclude members of the IT department.

## SQL Concepts Demonstrated

* `SELECT`
* `WHERE`
* `AND`
* `OR`
* `NOT`
* `LIKE`
* `%` wildcard
* Date filtering
* Boolean filtering
* Comparison operators

## Security Relevance

SQL filtering can help security teams narrow large datasets and identify information relevant to security investigations.

In this project, SQL was used to investigate failed login attempts, examine activity around suspicious dates, identify login attempts outside an expected location, and retrieve employee information needed for security updates.

## Key Takeaways

This project strengthened my understanding of how SQL filtering can be applied to security-related tasks and investigations.

It also provided practical experience working with multiple conditions, patterns, dates, Boolean values, and different SQL operators.
