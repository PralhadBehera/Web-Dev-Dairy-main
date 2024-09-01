
### **Key Types in SQL**

| **Key Type**       | **Definition**                                                                                     | **Characteristics**                                                                                           | **Example**                                                                                                           |
|--------------------|----------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
| **Candidate Key**  | A column or set of columns that can uniquely identify a row in a table.                           | - Potential to be a primary key.<br>- Must be unique.<br>- Can be a single column or multiple columns.       | ```sql CREATE TABLE Employees (employee_id INT, email VARCHAR(100), PRIMARY KEY (employee_id), UNIQUE (email)); ``` |
| **Primary Key**    | A specific candidate key chosen to uniquely identify each row in a table.                        | - Must be unique.<br>- Cannot contain NULL values.<br>- Only one primary key per table.                      | ```sql CREATE TABLE Customers (customer_id INT PRIMARY KEY, name VARCHAR(100)); ```                                 |
| **Super Key**      | A set of one or more columns that uniquely identifies a row in a table.                          | - Includes primary keys and any additional columns that ensure uniqueness.<br>- May contain extra columns.     | ```sql CREATE TABLE Projects (project_id INT, project_name VARCHAR(100), project_code VARCHAR(50), PRIMARY KEY (project_id)); ``` |
| **Alternate Key**  | A candidate key that is not chosen as the primary key.                                             | - Provides an alternative unique identifier.<br>- Must be unique, but not used as the primary key.            | ```sql CREATE TABLE Users (user_id INT PRIMARY KEY, email VARCHAR(100) UNIQUE); ```                                 |
| **Foreign Key**    | A column or set of columns in one table that references the primary key of another table.         | - Enforces referential integrity.<br>- Can contain NULL values.<br>- Establishes relationships between tables. | ```sql CREATE TABLE Orders (order_id INT PRIMARY KEY, customer_id INT, FOREIGN KEY (customer_id) REFERENCES Customers(customer_id)); ``` |
| **Composite Key**  | A primary key that consists of two or more columns.                                               | - Ensures uniqueness across a combination of columns.<br>- Useful when a single column cannot uniquely identify a row. | ```sql CREATE TABLE Enrollment (student_id INT, course_id INT, enrollment_date DATE, PRIMARY KEY (student_id, course_id)); ``` |

### **Detailed Explanation and Examples**

#### **Candidate Key**

- **Definition**: A candidate key is a column or a set of columns that can uniquely identify a row in a table. Any candidate key can potentially serve as the primary key.
- **Characteristics**:
  - Uniqueness: Each value in the candidate key must be unique across the table.
  - Can be a single column or a combination of columns.
- **Example**:
  ```sql
  CREATE TABLE Employees (
      employee_id INT,           -- Candidate key
      email VARCHAR(100),        -- Candidate key
      PRIMARY KEY (employee_id), -- Primary key
      UNIQUE (email)             -- Alternate key (candidate key not used as primary key)
  );
  ```

#### **Primary Key**

- **Definition**: The primary key is a unique identifier for each record in a table. It is selected from the candidate keys and is used to ensure the uniqueness of records.
- **Characteristics**:
  - Must be unique and not NULL.
  - Each table can have only one primary key.
- **Example**:
  ```sql
  CREATE TABLE Customers (
      customer_id INT PRIMARY KEY,  -- Primary key
      name VARCHAR(100)
  );
  ```

#### **Super Key**

- **Definition**: A super key is a set of one or more columns that can uniquely identify a row in a table. It includes the primary key and any additional columns that ensure uniqueness.
- **Characteristics**:
  - May include extra columns beyond what is needed for uniqueness.
  - Can be more complex than a candidate key.
- **Example**:
  ```sql
  CREATE TABLE Projects (
      project_id INT,             -- Part of super key
      project_name VARCHAR(100),  -- Part of super key
      project_code VARCHAR(50),   -- Part of super key
      PRIMARY KEY (project_id),   -- Primary key (subset of super key)
      UNIQUE (project_code)       -- Unique constraint (part of super key)
  );
  ```

#### **Alternate Key**

- **Definition**: An alternate key is a candidate key that is not chosen as the primary key. It provides an alternative unique identifier for records.
- **Characteristics**:
  - Must be unique across the table.
  - Serves as a backup to the primary key.
- **Example**:
  ```sql
  CREATE TABLE Users (
      user_id INT PRIMARY KEY,    -- Primary key
      email VARCHAR(100) UNIQUE   -- Alternate key
  );
  ```

#### **Foreign Key**

- **Definition**: A foreign key is a column or set of columns in one table that references the primary key of another table. It establishes and enforces a link between the tables.
- **Characteristics**:
  - Ensures referential integrity between tables.
  - Can contain NULL values (if allowed by the schema).
- **Example**:
  ```sql
  CREATE TABLE Orders (
      order_id INT PRIMARY KEY,
      customer_id INT,
      FOREIGN KEY (customer_id) REFERENCES Customers(customer_id)
  );
  ```

#### **Composite Key**

- **Definition**: A composite key is a primary key that consists of two or more columns used together to uniquely identify a row in a table.
- **Characteristics**:
  - Ensures uniqueness across multiple columns.
  - Useful when no single column can uniquely identify a row.
- **Example**:
  ```sql
  CREATE TABLE Enrollment (
      student_id INT,
      course_id INT,
      enrollment_date DATE,
      PRIMARY KEY (student_id, course_id)  -- Composite key
  );
  ```

### **Summary**

- **Candidate Key**: Potential primary key; unique identifiers.
- **Primary Key**: Chosen candidate key for unique row identification.
- **Super Key**: Any key or set of columns that ensures uniqueness.
- **Alternate Key**: Candidate key not chosen as the primary key.
- **Foreign Key**: References the primary key of another table, ensuring referential integrity.
- **Composite Key**: Multiple columns combined to form a primary key, ensuring uniqueness.