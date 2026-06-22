# GENAI-AND-AGENTICAI

# API Integration & Database Integration using Python, SQLite, and Flask

## Overview

This project demonstrates how to integrate Python applications with a SQLite database and expose database operations through Flask APIs.

The notebook covers:

* SQLite database creation
* CRUD operations (Create, Read, Update, Delete)
* Python and SQLite integration
* Flask API development
* User registration API
* Fetching user data from the database

---

## Technologies Used

* Python
* SQLite3
* Flask
* JSON

---

## Project Structure

```text
_API_Integration_Database_Integration.ipynb
demo310526.db
demo3105261.db
```

---

## Database Operations

### Create Database Connection

```python
import sqlite3

connect = sqlite3.connect("demo310526.db")
cur = connect.cursor()
```

### Create Table

```python
cur.execute("""
CREATE TABLE IF NOT EXISTS users(
    id TEXT,
    password TEXT,
    age INT
)
""")
```

### Insert Data

```python
cur.execute(
    "INSERT INTO users VALUES ('admin','test123$',25)"
)
```

### Read Data

```python
list(cur.execute("SELECT * FROM users"))
```

### Update Data

```python
cur.execute(
    "UPDATE users SET password='beta123$' WHERE id='admin'"
)
```

### Delete Data

```python
cur.execute(
    "DELETE FROM users WHERE id='admin'"
)
```

---

## Flask API Integration

### Test API

Endpoint:

```http
GET /test
```

Purpose:

* Creates database and table if not present
* Inserts sample data
* Returns user data in JSON format

Example Response:

```json
{
  "users_data": [
    ["admin", "test123$", 25]
  ]
}
```

---

## User Registration API

Endpoint:

```http
POST /register
```

### Request Body

```json
{
  "id": "admin",
  "password": "test123$",
  "age": 25
}
```

### Functionality

* Receives user information from API request
* Stores user data in SQLite database
* Returns success response

---

## How to Run

### Install Dependencies

```bash
pip install flask
```

### Start Flask Application

```bash
python app.py
```

### Access API

```text
http://localhost:5005/test
```

or

```text
http://localhost:5005/register
```

---

## Learning Outcomes

After completing this project, you will understand:

* Database connectivity using SQLite
* SQL CRUD operations in Python
* Building REST APIs with Flask
* Handling JSON requests and responses
* Integrating APIs with databases

---

## Future Improvements

* Add Login API
* Password Hashing
* JWT Authentication
* SQL Injection Prevention
* Error Handling
* Input Validation
* User Management Dashboard

---

## Author

Created as a learning project for API Integration and Database Integration using Python, SQLite, and Flask.
