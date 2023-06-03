---
title: Python Sqlite3 Db API
---

- Sample Data
  ```python
  student = {'name': 'John', 'age': 25, 'courses': ['Math', 'CompSci']}

  class SampleData(BaseModel):
    name: str
    field2: str
  ```

- # Create Connection and Cursor
  ```python
  con = sqlite3.connect("tutorial.db", check_same_thread=False)
  cur = con.cursor()
  ```
- # Create Table with PrimaryKey
  ```python
  cur.execute("CREATE TABLE StudentMetadata(first_name text NOT NULL, last_name text NOT NULL, PRIMARY KEY (first_name))")
  con.commit()
  ```
- # Create Table with Composite Primary Key
  ```python
  cur.execute("CREATE TABLE StudentMetadata(first_name text NOT NULL, last_name text NOT NULL, PRIMARY KEY (first_name, last_name))")
  con.commit()
  ```
- # Insert Query
  ```python
  cur.execute("CREATE TABLE StudentMetadata(first_name text NOT NULL, last_name text NOT NULL)")
  con.commit()
  
  cur.execute('insert into StudentMetadata values(?,?)', ('John', 'Mento'))
  con.commit()
  ```
- # Insert Query with JSON column
  ```python
  cur.execute("CREATE TABLE StudentMetadata(first_name text NOT NULL, app_data JSON NOT NULL)")
  con.commit()
  
  cur.execute('insert into StudentMetadata values(?,?)', ('test', student.json()))
  con.commit()
  ```
- # Insert Multiple Query
  ```python
  cur.execute("CREATE TABLE StudentMetadata(first_name text NOT NULL, app_data JSON NOT NULL)")
  con.commit()
  
  values = []
  for i in range(0, 100):
      dt1 = SampleData(name=f'test-{i}', field2=f'field2-{i}').dict()
      values.append(tuple([dt1[x] for x in dt1.keys()]))
  cur.executemany('insert into StudentMetadata values(?,?)', values)
  con.commit()
  ```
   