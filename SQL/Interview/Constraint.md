
### **Types of Constraints in SQL**

| **Constraint Type**   | **Description**                                                                                             | **Usage**                                                   | **Example**                                                                                     |
|-----------------------|-------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------|
| **PRIMARY KEY**       | Uniquely identifies each record in a table. Ensures the column(s) used are unique and not NULL.            | Enforces unique identification of rows.                   | `CREATE TABLE Users (user_id INT PRIMARY KEY, name VARCHAR(100));`                             |
| **FOREIGN KEY**       | Enforces referential integrity by linking columns in one table to the primary key of another table.          | Maintains relationships between tables.                    | `CREATE TABLE Orders (order_id INT PRIMARY KEY, user_id INT, FOREIGN KEY (user_id) REFERENCES Users(user_id));` |
| **UNIQUE**            | Ensures all values in a column or a set of columns are unique across the table.                             | Prevents duplicate values in specified columns.             | `CREATE TABLE Employees (email VARCHAR(100) UNIQUE);`                                           |
| **CHECK**             | Ensures that all values in a column satisfy a specific condition or expression.                             | Validates data based on conditions.                         | `CREATE TABLE Products (price DECIMAL CHECK (price > 0));`                                      |
| **NOT NULL**          | Ensures that a column cannot have NULL values.                                                               | Guarantees that a column must always contain a value.       | `CREATE TABLE Customers (name VARCHAR(100) NOT NULL);`                                          |
| **DEFAULT**           | Provides a default value for a column when no value is specified during an insert operation.                | Sets a default value if none is provided.                   | `CREATE TABLE Orders (status VARCHAR(20) DEFAULT 'Pending');`                                   |

### **Detailed Explanation and Examples**

#### **1. PRIMARY KEY**

- **Definition**: A column or set of columns that uniquely identifies each row in a table. 
- **Characteristics**:
  - Ensures uniqueness for the key column(s).
  - Cannot contain NULL values.
- **Example**:
  ```sql
  CREATE TABLE Customers (
      customer_id INT PRIMARY KEY,  -- Primary key
      name VARCHAR(100)
  );
  ```

#### **2. FOREIGN KEY**

- **Definition**: A column or set of columns in one table that refers to the primary key of another table.
- **Characteristics**:
  - Enforces referential integrity between tables.
  - Can contain NULL values if the relationship allows.
- **Example**:
  ```sql
  CREATE TABLE Orders (
      order_id INT PRIMARY KEY,
      customer_id INT,
      FOREIGN KEY (customer_id) REFERENCES Customers(customer_id)  -- Foreign key
  );
  ```

#### **3. UNIQUE**

- **Definition**: Ensures that all values in a column or a set of columns are unique across the table.
- **Characteristics**:
  - Allows NULL values unless explicitly restricted.
  - Enforces uniqueness but does not create a primary key.
- **Example**:
  ```sql
  CREATE TABLE Employees (
      email VARCHAR(100) UNIQUE  -- Unique constraint
  );
  ```

#### **4. CHECK**

- **Definition**: Ensures that all values in a column satisfy a specific condition or expression.
- **Characteristics**:
  - Validates data based on logical expressions.
- **Example**:
  ```sql
  CREATE TABLE Products (
      price DECIMAL CHECK (price > 0)  -- Check constraint
  );
  ```

#### **5. NOT NULL**

- **Definition**: Ensures that a column cannot have NULL values.
- **Characteristics**:
  - Guarantees that the column will always contain a value.
- **Example**:
  ```sql
  CREATE TABLE Customers (
      name VARCHAR(100) NOT NULL  -- Not NULL constraint
  );
  ```

#### **6. DEFAULT**

- **Definition**: Provides a default value for a column when no value is specified during an insert operation.
- **Characteristics**:
  - Automatically assigns a default value to the column if none is provided.
- **Example**:
  ```sql
  CREATE TABLE Orders (
      status VARCHAR(20) DEFAULT 'Pending'  -- Default value
  );
  ```
