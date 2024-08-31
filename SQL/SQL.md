

```markdown
# SQL Pattern Matching

## 1. `LIKE` Operator

- **Purpose**: Performs simple pattern matching within string columns.
- **Syntax**:
  ```sql
  SELECT column_names
  FROM table_name
  WHERE column_name LIKE pattern;
  ```
- **Wildcards**:
  - `%` (percent sign): Matches zero or more characters.
  - `_` (underscore): Matches exactly one character.

**Examples**:
- **Find all names starting with 'A'**:
  ```sql
  SELECT * FROM employees
  WHERE name LIKE 'A%';
  ```
- **Find all email addresses ending with 'example.com'**:
  ```sql
  SELECT * FROM users
  WHERE email LIKE '%example.com';
  ```

## 2. `NOT LIKE` Operator

- **Purpose**: Finds records where the column value does not match the specified pattern.
- **Syntax**:
  ```sql
  SELECT column_names
  FROM table_name
  WHERE column_name NOT LIKE pattern;
  ```

**Examples**:
- **Find all names that do not start with 'A'**:
  ```sql
  SELECT * FROM employees
  WHERE name NOT LIKE 'A%';
  ```
- **Find all email addresses not containing 'example'**:
  ```sql
  SELECT * FROM users
  WHERE email NOT LIKE '%example%';
  ```

## 3. `SIMILAR TO` Operator (PostgreSQL Specific)

- **Purpose**: Combines SQL standard regular expression patterns with SQL `LIKE` functionality.
- **Syntax**:
  ```sql
  SELECT column_names
  FROM table_name
  WHERE column_name SIMILAR TO 'pattern';
  ```

**Pattern Syntax**:
- `[...]` defines a character class.
- `|` separates alternatives.
- `*` matches zero or more occurrences of the previous element.
- `+` matches one or more occurrences of the previous element.
- `?` matches zero or one occurrence of the previous element.

**Examples**:
- **Find all names starting with 'A' or 'B'**:
  ```sql
  SELECT * FROM employees
  WHERE name SIMILAR TO '[AB]%';
  ```
- **Find all names with 'son' anywhere in the middle**:
  ```sql
  SELECT * FROM employees
  WHERE name SIMILAR TO '%son%';
  ```

## 4. Regular Expressions

- **Purpose**: Allows advanced pattern matching using regex syntax.
- **Supported Databases**:
  - **PostgreSQL**: Uses `~` (case-sensitive) and `~*` (case-insensitive).
  - **MySQL**: Uses `REGEXP` or `RLIKE`.
  - **Oracle**: Uses `REGEXP_LIKE`.

**Syntax**:
- **PostgreSQL**:
  ```sql
  SELECT column_names
  FROM table_name
  WHERE column_name ~ 'pattern';
  ```

- **MySQL**:
  ```sql
  SELECT column_names
  FROM table_name
  WHERE column_name REGEXP 'pattern';
  ```

- **Oracle**:
  ```sql
  SELECT column_names
  FROM table_name
  WHERE REGEXP_LIKE(column_name, 'pattern');
  ```

**Examples**:
- **PostgreSQL: Find all email addresses containing 'example' (case-insensitive)**:
  ```sql
  SELECT * FROM users
  WHERE email ~* 'example';
  ```

- **MySQL: Find all phone numbers with a format of three digits followed by a hyphen**:
  ```sql
  SELECT * FROM contacts
  WHERE phone REGEXP '^[0-9]{3}-';
  ```

- **Oracle: Find names starting with 'J' or 'j' and followed by any characters**:
  ```sql
  SELECT * FROM employees
  WHERE REGEXP_LIKE(name, '^[Jj]');
  ```

## 5. `CHARINDEX` and `PATINDEX` Functions (SQL Server Specific)

- **Purpose**: Finds the position of a substring within a string, useful for locating patterns.
- **Functions**:
  - **`CHARINDEX`**: Returns the starting position of a substring.
  - **`PATINDEX`**: Returns the starting position of a pattern.

**Syntax**:
- **`CHARINDEX`**:
  ```sql
  SELECT column_names
  FROM table_name
  WHERE CHARINDEX('substring', column_name) > 0;
  ```

- **`PATINDEX`**:
  ```sql
  SELECT column_names
  FROM table_name
  WHERE PATINDEX('pattern', column_name) > 0;
  ```

**Examples**:
- **SQL Server: Find names containing 'Smith'**:
  ```sql
  SELECT * FROM employees
  WHERE CHARINDEX('Smith', name) > 0;
  ```

- **SQL Server: Find names starting with 'S'**:
  ```sql
  SELECT * FROM employees
  WHERE PATINDEX('S%', name) > 0;
  ```

## Key Points

- **`LIKE`**: Best for simple, straightforward pattern matching.
- **`NOT LIKE`**: Filters out records that match the pattern.
- **`SIMILAR TO`**: Provides more complex pattern matching using SQL-like regex syntax, available in PostgreSQL.
- **Regular Expressions**: Offers advanced pattern matching capabilities and is supported in PostgreSQL, MySQL, and Oracle.
- **`CHARINDEX` and `PATINDEX`**: Useful for locating substrings or patterns in SQL Server.

Each SQL database has its own syntax and capabilities for pattern matching, so refer to your specific database’s documentation for precise details and additional options.
```

You can copy and paste this markdown into a Git repository README file or any other markdown-supported document to maintain a structured reference for SQL pattern matching.