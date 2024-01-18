# [Master SQL for Data Science](https://www.linkedin.com/learning/paths/master-sql-for-data-science)

## Module 1 - SQL: Data Reporting and Analysis

### Working with DB in Python Environment

```python
# Import necessary libraries
!pip install sqlalchemy
import sqlite3
import pandas as pd

# Connecting with SQLite3
con = sqlite3.connect('database_path.db')

# Show all tables in the database
tables_query = "SELECT name FROM sqlite_master WHERE type='table';"
tables = pd.read_sql(tables_query, con)
tables

# Show table schema for table
schema_query = "PRAGMA table_info('table');"
schema = pd.read_sql(schema_query, con)
schema

# Using SELECT statement
sql_query = ''' SELECT * FROM customer '''
df = pd.read_sql(sql_query, con)
```

### Another Method

```bash
!pip install ipython-sql
%load_ext sql
%sql sqlite:///path_to_your_database.db

%%sql
SELECT * FROM customer;
```

- Have to mention`%%sql` before the Query

To convert the **result into a DataFrame**

```python
results = %sql SELECT * FROM customer;
results.DataFrame()
```

- Wont be able to write comments in the python way instead we can use SQL comments starting with '--'

### [Wild Cards](https://www.w3schools.com/sql/sql_wildcards.asp)

% -> Represents zero or more characters

_ -> Represents a single character

[] -> Represents any single character within the brackets \*

^ -> Represents any character not in the brackets \*

\- -> Represents any single character within the specified range \*

{} -> Represents any escaped character \*\*

? -> Represents any character

\* Not supported in PostgreSQL and MySQL databases.
\*\* Supported only in Oracle databases.

***Cannot use `IN` and `LIKE` together***

```sql
SELECT *
FROM actor
WHERE first_name IN ('PENELOP%', 'N_CK', 'ED?') ;
```

- It runs successfully but wont return anything cause we didnn\'t explicitly mentioned `LIKE`
