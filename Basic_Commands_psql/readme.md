# MySQL vs PostgreSQL: Key Differences

| Feature/Aspect          | MySQL                                            | PostgreSQL                                     |
|------------------------|--------------------------------------------------|------------------------------------------------|
| **Release Year**       | 1995                                             | 1996                                           |
| **License**            | Open Source (GPL)                                | Open Source (PostgreSQL License, similar to MIT)|
| **ACID Compliance**    | Fully ACID compliant (InnoDB engine)             | Fully ACID compliant                           |
| **SQL Compliance**     | Mostly compliant, some limitations                | Highly compliant, extensive standards support  |
| **Extensibility**      | Limited, plugins supported                        | Highly extensible (custom types, functions, etc.)|
| **Procedural Languages**| Limited (SQL/PSM, external scripting)            | Multiple built-in (PL/pgSQL, PL/Python, etc.)  |
| **JSON Support**       | Good (JSON, JSON functions)                      | Advanced (JSON, JSONB, indexing, rich functions)|
| **Indexing**           | Basic (B-Tree, Fulltext, Spatial)                 | Advanced (B-Tree, Hash, GIN, GiST, BRIN, etc.) |
| **Partitioning**       | Supported, modern improvements                    | Supported, flexible and mature                 |
| **Replication**        | Master-slave, Group Replication                   | Streaming, logical, and physical replication   |
| **Concurrency Model**  | Table-level locking (MyISAM), row-level (InnoDB)  | MVCC (Multi-Version Concurrency Control)       |
| **Foreign Keys**       | Supported (InnoDB only)                           | Fully supported                                |
| **Community & Support**| Large, backed by Oracle                           | Large, independent, strong open-source support |
| **Best For**           | Web applications, read-heavy workloads            | Complex queries, analytics, extensibility      |
| **Performance**        | Fast for simple read/write operations             | Fast for complex queries, large datasets       |
| **Data Types**         | Limited (no arrays, limited custom types)         | Rich set (arrays, custom types, hstore, etc.)  |
| **Advanced Features**  | Limited                                           | Window functions, CTEs, recursive queries, etc.|

---

**Summary:**  
- **MySQL** is popular for web applications, ease of use, and simple workloads.
- **PostgreSQL** is preferred for advanced, complex queries, extensibility, and standards compliance.

--- 

# Basic psql Commands

## 1. List all databases
```
\l
```

## 2. Connect to a database
```
\c dbname
```

## 3. List all tables in the current database
```
\dt
```

## 4. Show table schema (columns, types)
```
\d table_name
```

## 5. List all users/roles
```
\du
```

## 6. Execute SQL queries (example: select data)
```sql
SELECT * FROM table_name;
```

## 7. Get help for psql commands
```
\?
```

## 8. Get help for SQL commands
```
\h command
```
(e.g., `\h SELECT`)

## 9. Quit psql
```
\q
```

## 10. Clear the screen
```
\! clear
```
or
```
Ctrl+L
```
