Creating an empty table with the same structure as another table can be done in various SQL databases using specific SQL commands. Here’s how you can achieve this across different SQL systems:

### 1. **Using `CREATE TABLE AS` with `WHERE 1=0`**

This method works in many SQL databases and creates a new table with the same structure as the existing table, but without copying any data.

```sql
CREATE TABLE new_table AS
SELECT * FROM existing_table
WHERE 1=0;
```

- **Explanation**: The `WHERE 1=0` condition ensures that no rows are copied, resulting in an empty table with the same structure.

### 2. **Using `CREATE TABLE ... LIKE`**

- **MySQL** and **MariaDB**:
  ```sql
  CREATE TABLE new_table LIKE existing_table;
  ```

- **PostgreSQL**:
  ```sql
  CREATE TABLE new_table (LIKE existing_table INCLUDING ALL);
  ```

- **Oracle**:
  ```sql
  CREATE TABLE new_table AS SELECT * FROM existing_table WHERE 1=0;
  ```

- **SQL Server**:
  ```sql
  SELECT *
  INTO new_table
  FROM existing_table
  WHERE 1 = 0;
  ```
