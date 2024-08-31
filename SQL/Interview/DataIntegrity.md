**Data Integrity** refers to the accuracy, consistency, and reliability of data throughout its lifecycle. It ensures that data is accurate, complete, and maintained correctly across various stages, such as during storage, retrieval, and processing. Data integrity is crucial for maintaining trustworthiness and quality in databases and information systems.

### **Types of Data Integrity**

1. **Physical Integrity**:
   - **Definition**: Ensures that the physical storage of data is protected from corruption due to hardware failures, malfunctions, or other physical issues.
   - **Example**: Using RAID (Redundant Array of Independent Disks) to protect against disk failures.

2. **Logical Integrity**:
   - **Definition**: Ensures that the data is accurate and conforms to the rules and constraints defined by the database schema. It includes various subtypes:
     - **Entity Integrity**: Ensures that each entity (e.g., a row in a table) can be uniquely identified.
     - **Referential Integrity**: Ensures that relationships between tables are consistent and that foreign keys correctly reference primary keys.
     - **Domain Integrity**: Ensures that data values fall within a specified domain or range.
     - **User-Defined Integrity**: Enforces business rules or constraints defined by the user, beyond the built-in constraints.

### **Examples of Data Integrity**

1. **Entity Integrity**:
   - **Definition**: Ensures that each row in a table has a unique identifier (primary key).
   - **Example**: In an `employees` table, each employee record must have a unique `employee_id`. The `employee_id` is defined as the primary key.
     ```sql
     CREATE TABLE employees (
         employee_id INT PRIMARY KEY,
         name VARCHAR(100),
         position VARCHAR(50),
         salary DECIMAL(10, 2)
     );
     ```

2. **Referential Integrity**:
   - **Definition**: Ensures that foreign key values in one table match primary key values in another table.
   - **Example**: In an `orders` table, the `customer_id` field must reference a valid `customer_id` in the `customers` table.
     ```sql
     CREATE TABLE customers (
         customer_id INT PRIMARY KEY,
         name VARCHAR(100)
     );

     CREATE TABLE orders (
         order_id INT PRIMARY KEY,
         customer_id INT,
         order_date DATE,
         FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
     );
     ```

3. **Domain Integrity**:
   - **Definition**: Ensures that data values fall within a defined range or set of allowable values.
   - **Example**: The `salary` field in the `employees` table should only accept positive decimal values.
     ```sql
     CREATE TABLE employees (
         employee_id INT PRIMARY KEY,
         name VARCHAR(100),
         salary DECIMAL(10, 2) CHECK (salary > 0)
     );
     ```

4. **User-Defined Integrity**:
   - **Definition**: Enforces business rules or constraints defined by the user.
   - **Example**: An employee's `hire_date` should not be later than today's date.
     ```sql
     CREATE TABLE employees (
         employee_id INT PRIMARY KEY,
         name VARCHAR(100),
         hire_date DATE CHECK (hire_date <= CURRENT_DATE)
     );
     ```
