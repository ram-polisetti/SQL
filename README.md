# [Master SQL for Data Science](https://www.linkedin.com/learning/paths/master-sql-for-data-science)

## Working with DB in Python Environment

```python
# Import necessary libraries
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

## Another Method

```bash
!pip install ipython-sql
%load_ext sql
%sql sqlite:///path_to_your_database.db

%%sql
SELECT * FROM customer;

```

- Have to mention %%sql before the Query