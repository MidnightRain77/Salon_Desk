# Salon Desk DBMS Project

## Overview

**Salon Desk** is a Database Management System (DBMS) designed to manage the operations of a salon, including handling appointments, inventory, services, employees, and client information. It uses a relational database structure with a well-defined ERD and schema.

---

## Schema

The database consists of **15 interconnected tables**:

| Table               | Description                                               |
|--------------------|-----------------------------------------------------------|
| `Products`          | Stores product info used or sold in the salon            |
| `Inventory_Transaction` | Logs all inventory movements (inward/outward)         |
| `Cumulative_Product` | Tracks total stock of products per branch               |
| `Owner`             | Information about salon branch owners                    |
| `Branch`            | Details of salon branches, linked to owners and managers |
| `Client`            | Stores client contact information                        |
| `Appointment`       | Appointment records including time, status, etc.         |
| `Employees`         | Employee data, salaries, roles, and contact              |
| `Manager`           | Manager info, linked to employees and branches           |
| `Salaries`          | Monthly salary, bonus, increment info                    |
| `Invoices`          | Invoices generated per appointment                       |
| `Leave`             | Tracks employee leaves                                   |
| `Provides`          | Links employees to services they can perform             |
| `Services`          | Salon services with duration and price                   |
| `Booked_for`        | Services linked to specific appointments                 |

---

## 🛠️ Setup Instructions

1. **Create Schema**
    ```sql
    CREATE SCHEMA salon_desk;
    SET search_path TO salon_desk;
    ```

2. **Run Schema Script**  
    Execute the provided SQL file to create all tables:
    ```sql
    -- Example:
    CREATE TABLE Products (
        P_ID INT PRIMARY KEY,
        P_Name VARCHAR(100),
        ...
    );
    ```

3. **Insert Sample Data**  
    Populate tables with demo data for testing.

4. **Query Examples**
    ```sql
    -- Top services per month
    SELECT S_Name, COUNT(*) AS times_booked
    FROM Services S
    JOIN Booked_for B ON S.S_ID = B.S_ID
    JOIN Appointment A ON A.A_ID = B.A_ID
    GROUP BY S_Name;
    ```

---

## Sample Use Cases

- Generate invoices for clients
- Track employee salary history
- Monitor service trends and demand
- Inventory usage analysis across branches
- Manage leave records for staff

---

## 📁 Project Structure

