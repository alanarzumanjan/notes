#### 👤 Connecting to PostgreSQL

```bash
# Login as postgres superuser
sudo -u postgres psql

# Login as your user to specific database
psql -U username -d database_name -h localhost

# Login with password prompt
psql -U username -d database_name -h localhost -W
```

#### 📊 Basic psql Commands

```sql
-- List all databases
\l

-- Connect to database
\c database_name

-- List all tables in current database
\dt

-- Describe table structure
\d table_name

-- List all users
\du

-- List all schemas
\dn

-- Exit psql
\q

-- Help with SQL commands
\h

-- Help with psql commands
\?

-- Show current database and user
\conninfo

-- Toggle query execution time display
\timing
```

#### 👥 User Management

```sql
-- Create new user
CREATE USER username WITH PASSWORD 'password';

-- Create user with superuser privileges
CREATE USER username WITH PASSWORD 'password' SUPERUSER;

-- Change user password
ALTER USER username WITH PASSWORD 'new_password';

-- Grant superuser privileges
ALTER USER username WITH SUPERUSER;

-- Revoke superuser privileges
ALTER USER username WITH NOSUPERUSER;

-- Delete user
DROP USER username;

-- Rename user
ALTER USER old_name RENAME TO new_name;
```

#### 🗄️ Database Management

```sql
-- Create new database
CREATE DATABASE dbname;

-- Create database with owner
CREATE DATABASE dbname OWNER username;

-- Create database with encoding
CREATE DATABASE dbname ENCODING 'UTF8';

-- Delete database
DROP DATABASE dbname;

-- Rename database
ALTER DATABASE old_name RENAME TO new_name;
```

#### 🔐 Permission Management

```sql
-- Grant all privileges on database to user
GRANT ALL PRIVILEGES ON DATABASE dbname TO username;

-- Grant privileges on all tables in schema
GRANT ALL PRIVILEGES ON ALL TABLES IN SCHEMA public TO username;

-- Grant privileges on specific table
GRANT SELECT, INSERT, UPDATE, DELETE ON table_name TO username;

-- Grant read-only access
GRANT SELECT ON table_name TO username;

-- Revoke all privileges
REVOKE ALL PRIVILEGES ON DATABASE dbname FROM username;

-- View table access privileges
\dp table_name
```

#### 📋 Table Operations

```sql
-- Create table
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    username VARCHAR(50) UNIQUE NOT NULL,
    email VARCHAR(100) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Drop table
DROP TABLE table_name;

-- Drop table if exists
DROP TABLE IF EXISTS table_name;

-- Clear all data from table
TRUNCATE TABLE table_name;

-- Rename table
ALTER TABLE old_name RENAME TO new_name;

-- Add column
ALTER TABLE table_name ADD COLUMN column_name VARCHAR(100);

-- Drop column
ALTER TABLE table_name DROP COLUMN column_name;

-- Change column type
ALTER TABLE table_name ALTER COLUMN column_name TYPE INTEGER;

-- Rename column
ALTER TABLE table_name RENAME COLUMN old_name TO new_name;
```

#### 🔍 Basic SQL Queries

```sql
-- Select all records
SELECT * FROM table_name;

-- Select with condition
SELECT * FROM table_name WHERE id = 1;

-- Select with sorting
SELECT * FROM table_name ORDER BY created_at DESC;

-- Select with limit
SELECT * FROM table_name LIMIT 10;

-- Insert data
INSERT INTO table_name (column1, column2) VALUES ('value1', 'value2');

-- Update data
UPDATE table_name SET column1 = 'new_value' WHERE id = 1;

-- Delete data
DELETE FROM table_name WHERE id = 1;

-- Count records
SELECT COUNT(*) FROM table_name;

-- Group by
SELECT category, COUNT(*) FROM table_name GROUP BY category;
```

#### 📤 Data Export and Import

```bash
# Export entire database to file
pg_dump -U username dbname > backup.sql

# Export specific table
pg_dump -U username -t table_name dbname > table_backup.sql

# Import from file
psql -U username dbname < backup.sql

# Export all databases
pg_dumpall -U postgres > all_databases.sql
```

#### 🔧 Configuration and Settings

```bash
# Main PostgreSQL config
sudo nano /var/lib/postgres/data/postgresql.conf

# Access settings (pg_hba.conf)
sudo nano /var/lib/postgres/data/pg_hba.conf

# View current settings
sudo -u postgres psql -c "SHOW config_file;"
sudo -u postgres psql -c "SHOW hba_file;"

# View specific parameter
sudo -u postgres psql -c "SHOW port;"
sudo -u postgres psql -c "SHOW max_connections;"
```

#### 🔍 Diagnostics and Monitoring

```sql
-- View active connections
SELECT * FROM pg_stat_activity;

-- Size of all databases
SELECT 
    datname AS database_name,
    pg_size_pretty(pg_database_size(datname)) AS size
FROM pg_database
ORDER BY pg_database_size(datname) DESC;

-- Size of tables
SELECT 
    tablename,
    pg_size_pretty(pg_total_relation_size(schemaname||'.'||tablename)) AS size
FROM pg_tables
WHERE schemaname = 'public'
ORDER BY pg_total_relation_size(schemaname||'.'||tablename) DESC;

-- Current PostgreSQL version
SELECT version();

-- Show all settings
SHOW ALL;
```

#### 🚨 Troubleshooting

```bash
# View PostgreSQL logs
sudo journalctl -xeu postgresql.service --no-pager | tail -50

# Check if port is occupied
sudo lsof -i :5432

# Reinitialize database (WILL DELETE ALL DATA!)
sudo rm -rf /var/lib/postgres/data/*
sudo -u postgres initdb -D /var/lib/postgres/data --locale=en_US.UTF-8

# Check access permissions
sudo ls -la /var/lib/postgres/data/

# Fix access permissions
sudo chown -R postgres:postgres /var/lib/postgres/data
sudo chmod 700 /var/lib/postgres/data
```

#### 🔌 Connecting to DBeaver

**Connection settings:**
- **Host:** `localhost`
- **Port:** `5432`
- **Database:** your database name
- **Username:** your username
- **Password:** your password

**Test connection from terminal:**
```bash
psql -U username -d database_name -h localhost
```

#### 💡 Useful Examples

```sql
-- Create user and database for project
CREATE USER myapp WITH PASSWORD 'secure_password';
CREATE DATABASE myapp_db OWNER myapp;
GRANT ALL PRIVILEGES ON DATABASE myapp_db TO myapp;

-- Create table with foreign key
CREATE TABLE posts (
    id SERIAL PRIMARY KEY,
    user_id INTEGER REFERENCES users(id) ON DELETE CASCADE,
    title VARCHAR(200) NOT NULL,
    content TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Create index for faster search
CREATE INDEX idx_users_email ON users(email);

-- Search by partial string
SELECT * FROM users WHERE username LIKE '%john%';

-- Join tables
SELECT u.username, p.title 
FROM users u 
JOIN posts p ON u.id = p.user_id;
```

#### 🎯 Quick Start for New Project

```bash
# 1. Create user and database
sudo -u postgres psql

CREATE USER projectname WITH PASSWORD 'secure_password';
CREATE DATABASE projectname_db OWNER projectname;
GRANT ALL PRIVILEGES ON DATABASE projectname_db TO projectname;
\q

# 2. Connect to new database
psql -U projectname -d projectname_db -h localhost

# 3. Create tables
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    username VARCHAR(50) UNIQUE NOT NULL,
    email VARCHAR(100) NOT NULL,
    password_hash VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

# 4. Done! Now you can connect from code or DBeaver
```

---

## 📚 Useful Links

- [Official PostgreSQL Documentation](https://www.postgresql.org/docs/)
- [PostgreSQL Tutorial](https://www.postgresqltutorial.com/)
- [pgAdmin - GUI for PostgreSQL](https://www.pgadmin.org/)

---

**Last updated:** 30.11.2025
