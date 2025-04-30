# 📖 Proof of Concept Tutorial: Using SQLAlchemy, Pandas, and PostgreSQL

This **step-by-step tutorial** will guide you through setting up a **local PostgreSQL database**, using **SQLAlchemy** with **Pandas**, and **inserting a CSV file into the database**.

## ✅ Who is this for?
- Beginners with **minimal experience** using PostgreSQL and SQLAlchemy.  
- Anyone setting up **a fresh environment** for local development.  

## ✅ What will you learn?
1. **Install & configure PostgreSQL** on your machine.  
2. **Create a Python script** to connect to the database.  
3. **Set up SQLAlchemy & Pandas** for working with PostgreSQL.  
4. **Parse a simple CSV file** and insert the data into the database.  
5. **Verify the data** inside PostgreSQL.  

---

## 1️⃣ Install PostgreSQL

### 🔹 A. Install PostgreSQL
#### **Windows:**
1. Download and install **PostgreSQL** from [https://www.postgresql.org/download/](https://www.postgresql.org/download/).
2. During installation, set the **username** to `postgres` and choose a **password**.
3. Ensure **pgAdmin** is installed for managing the database.

#### **Mac (Homebrew Users):**
```bash
brew install postgresql
brew services start postgresql
```

#### **Linux (Debian/Ubuntu Users):**
```bash
sudo apt update
sudo apt install postgresql postgresql-contrib
sudo systemctl start postgresql
```

### 🔹 B. Verify PostgreSQL is Running
Run the following command to check if PostgreSQL is active:
```bash
pg_isready -h localhost -p 5432 -U postgres
```
If PostgreSQL is **not running**, start it:
```bash
sudo systemctl start postgresql  # Linux
brew services start postgresql   # Mac
```

---

## 2️⃣ Create a PostgreSQL Database

### 🔹 A. Open the PostgreSQL Shell
Run:
```bash
psql -U postgres
```
This opens the PostgreSQL interactive terminal.

### 🔹 B. Create a New Database
Inside `psql`, run:
```sql
CREATE DATABASE mytestdb;
```

### 🔹 C. Create a New User
```sql
CREATE USER myuser WITH ENCRYPTED PASSWORD 'mypassword';
GRANT ALL PRIVILEGES ON DATABASE mytestdb TO myuser;
```

### 🔹 D. Exit psql
Type:
```bash
\q
```
Your **PostgreSQL database** is now set up! 🎉

---

## 3️⃣ Set Up Python and Dependencies

### 🔹 A. Create a New Project Folder
```bash
mkdir sqlalchemy_demo && cd sqlalchemy_demo
```

### 🔹 B. Create a Virtual Environment
```bash
python3 -m venv venv
source venv/bin/activate  # macOS/Linux
venv\Scripts\activate      # Windows
```

### 🔹 C. Install Dependencies
```bash
pip install sqlalchemy psycopg2-binary pandas python-dotenv
```

---

## 4️⃣ Configure Database Connection in Python

### 🔹 A. Create a `.env` File
Inside your `sqlalchemy_demo` folder, create a **`.env` file**:
```
DB_NAME=mytestdb
DB_USER=myuser
DB_PASSWORD=mypassword
DB_HOST=localhost
DB_PORT=5432
```

### 🔹 B. Create a Python Script (`db_setup.py`)
```python
import os
from dotenv import load_dotenv
from sqlalchemy import create_engine

# Load environment variables
load_dotenv()

# Retrieve database credentials
DB_NAME = os.getenv("DB_NAME")
DB_USER = os.getenv("DB_USER")
DB_PASSWORD = os.getenv("DB_PASSWORD")
DB_HOST = os.getenv("DB_HOST")
DB_PORT = os.getenv("DB_PORT")

# Create the database connection
DATABASE_URL = f"postgresql://{DB_USER}:{DB_PASSWORD}@{DB_HOST}:{DB_PORT}/{DB_NAME}"
engine = create_engine(DATABASE_URL)

# Test connection
try:
    conn = engine.connect()
    print("✅ Successfully connected to PostgreSQL!")
    conn.close()
except Exception as e:
    print(f"❌ Database connection failed: {e}")
```

### 🔹 C. Run the Script
```bash
python db_setup.py
```
✅ If successful, you will see:
```
✅ Successfully connected to PostgreSQL!
```

---

## 5️⃣ Create a Table in PostgreSQL
```python
from db_setup import engine
from sqlalchemy import Table, Column, Integer, String, MetaData

# Define metadata
metadata = MetaData()

# Define table schema
users_table = Table(
    "users",
    metadata,
    Column("id", Integer, primary_key=True),
    Column("name", String(50)),
    Column("email", String(100)),
)

# Create the table in PostgreSQL
metadata.create_all(engine)

print("✅ Table 'users' created successfully!")
```

### 🔹 Run the Script
```bash
python create_table.py
```
Check in `psql`:
```sql
SELECT * FROM users;
```

---

## 6️⃣ Insert a CSV File into PostgreSQL
```python
import pandas as pd
from db_setup import engine

# Load CSV
df = pd.read_csv("users.csv")

# Insert data into PostgreSQL
df.to_sql("users", engine, if_exists="replace", index=False)

print(f"✅ Successfully inserted {len(df)} rows into 'users' table.")
```

### 🔹 Run the Script
```bash
python insert_csv.py
```

### 🔹 Verify Data in PostgreSQL
```sql
SELECT * FROM users;
```

---

## 🎯 Conclusion
✅ **You have successfully:**
1. Installed **PostgreSQL** and created a **database**.
2. Set up a **Python project** with **SQLAlchemy** and **Pandas**.
3. **Connected** to PostgreSQL using **SQLAlchemy**.
4. Created a **table** and **inserted data** from a **CSV file**.
5. Verified the **data inside PostgreSQL**.

Would you like me to create a **Docker version** of this for easy deployment? 🚀

