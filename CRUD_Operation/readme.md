# CRUD Operations in PostgreSQL using psql

CRUD stands for **Create, Read, Update, and Delete**—the basic operations you perform on database data. Below are notes and examples for each operation in PostgreSQL, using the `psql` interactive terminal.

---

## 1. Create (Insert Data)

### Create a Table
```sql
CREATE TABLE students (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    age INT
);
```

### Insert Data
```sql
INSERT INTO students (name, age) VALUES ('Alice', 22);
INSERT INTO students (name, age) VALUES ('Bob', 24);
```

---

## 2. Read (Query Data)

### Select All Rows
```sql
SELECT * FROM students;
```

### Select Specific Columns
```sql
SELECT name, age FROM students;
```

### Filter Rows
```sql
SELECT * FROM students WHERE age > 22;
```

### Limit Results
```sql
SELECT * FROM students LIMIT 2;
```

---

## 3. Update (Modify Data)

### Update Existing Data
```sql
UPDATE students SET age = 23 WHERE name = 'Alice';
```

### Update Multiple Rows
```sql
UPDATE students SET age = age + 1 WHERE age < 25;
```

---

## 4. Delete (Remove Data)

### Delete Specific Row(s)
```sql
DELETE FROM students WHERE name = 'Bob';
```

### Delete All Rows
```sql
DELETE FROM students;
```

---

## Helpful psql Meta-Commands

- List tables:  
  ```
  \dt
  ```

- Describe table structure:  
  ```
  \d students
  ```

- Quit psql:  
  ```
  \q
  ```

---

**Tip:** Always end SQL commands with a semicolon (`;`) in `psql`.  
Use `SELECT * FROM students;` to confirm changes after any operation.
