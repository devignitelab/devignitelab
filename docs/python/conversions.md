---
title: Python Conversions
---

- Sample Data
  ```python
  student = {'name': 'John', 'age': 25, 'courses': ['Math', 'CompSci']}
  ```

- Dict to tuple
  ```python
  print( tuple(student.values()) )
  ```
- Dict to JSON string
  ```python
  print( json.dumps(student) )
  ```
- Dict to List of tuples
  ```python
  print( list(student.items()) )
  ```
  