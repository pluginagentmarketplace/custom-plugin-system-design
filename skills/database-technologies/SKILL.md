---
name: database-technologies
description: Master database technologies including SQL, PostgreSQL, MongoDB, Redis, and data modeling. Use when designing databases, writing queries, or optimizing database performance.
sasmp_version: "1.3.0"
bonded_agent: 01-frontend-web-development
bond_type: PRIMARY_BOND
---

# Database Technologies

## Quick Start

### SQL Fundamentals
```sql
-- Create table
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    email VARCHAR(255) UNIQUE NOT NULL,
    name VARCHAR(255),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Insert data
INSERT INTO users (email, name) VALUES ('john@example.com', 'John Doe');

-- Select data
SELECT * FROM users WHERE id = 1;

-- Update
UPDATE users SET name = 'Jane Doe' WHERE id = 1;

-- Delete
DELETE FROM users WHERE id = 1;
```

### PostgreSQL Advanced
```sql
-- JSON support
CREATE TABLE products (
    id SERIAL PRIMARY KEY,
    data JSONB
);

INSERT INTO products VALUES (1, '{"name": "Product", "price": 99.99}');
SELECT data->>'name' FROM products;

-- Window functions
SELECT
    name,
    salary,
    AVG(salary) OVER (PARTITION BY department) as avg_dept_salary
FROM employees;

-- CTE (Common Table Expressions)
WITH high_earners AS (
    SELECT * FROM employees WHERE salary > 100000
)
SELECT * FROM high_earners ORDER BY salary DESC;

-- Indexes
CREATE INDEX idx_users_email ON users(email);
CREATE INDEX idx_products_price ON products((data->>'price'));
```

### MongoDB Document Model
```javascript
// Insert documents
db.users.insertOne({
    _id: ObjectId(),
    email: "john@example.com",
    name: "John Doe",
    profile: {
        age: 30,
        location: "New York"
    },
    tags: ["developer", "python"],
    createdAt: new Date()
});

// Find documents
db.users.find({ email: "john@example.com" });
db.users.find({ "profile.age": { $gt: 25 } });

// Update documents
db.users.updateOne(
    { _id: ObjectId() },
    { $set: { "profile.age": 31 } }
);

// Aggregation pipeline
db.users.aggregate([
    { $match: { tags: "developer" } },
    { $group: { _id: null, count: { $sum: 1 } } },
    { $sort: { count: -1 } }
]);
```

### Redis Operations
```python
import redis

r = redis.Redis(host='localhost', port=6379)

# String operations
r.set('key', 'value')
r.get('key')
r.incr('counter')

# List operations
r.lpush('queue', 'task1', 'task2')
r.rpop('queue')

# Set operations
r.sadd('tags', 'python', 'database')
r.smembers('tags')

# Hash operations
r.hset('user:1', mapping={'name': 'John', 'email': 'john@example.com'})
r.hgetall('user:1')

# Sorted set operations
r.zadd('leaderboard', {'player1': 100, 'player2': 200})
r.zrevrange('leaderboard', 0, -1, withscores=True)

# Expiry
r.setex('temp_key', 3600, 'value')  # Expires in 1 hour
```

## Relational Databases (SQL)

### Data Types
- **Numeric**: INTEGER, DECIMAL, FLOAT
- **Text**: VARCHAR, TEXT, CHAR
- **Date/Time**: DATE, TIME, TIMESTAMP
- **Boolean**: BOOLEAN
- **Binary**: BYTEA, BLOB
- **Special**: UUID, JSON, ARRAY

### Relationships
```sql
-- One-to-Many
CREATE TABLE departments (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100)
);

CREATE TABLE employees (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    department_id INTEGER REFERENCES departments(id)
);

-- Many-to-Many
CREATE TABLE students (id SERIAL PRIMARY KEY);
CREATE TABLE courses (id SERIAL PRIMARY KEY);

CREATE TABLE enrollments (
    student_id INTEGER REFERENCES students(id),
    course_id INTEGER REFERENCES courses(id),
    PRIMARY KEY (student_id, course_id)
);

-- One-to-One
CREATE TABLE users_profiles (
    user_id INTEGER PRIMARY KEY REFERENCES users(id),
    bio TEXT,
    avatar_url VARCHAR(255)
);
```

### Advanced Features
- **Transactions**: ACID compliance
- **Views**: Virtual tables
- **Stored Procedures**: Reusable SQL code
- **Triggers**: Automated actions
- **Constraints**: PRIMARY KEY, UNIQUE, CHECK, DEFAULT

## NoSQL Databases

### MongoDB
- **Document-Oriented**: Flexible schema
- **Collections**: Tables equivalent
- **Documents**: JSON-like objects
- **Aggregation Pipeline**: Complex queries
- **Indexing**: Field-level indexing
- **Transactions**: Multi-document ACID transactions
- **Replication**: Replica sets for HA

### Redis
- **In-Memory**: Ultra-fast data access
- **Data Structures**: Strings, Lists, Sets, Hashes, Sorted Sets
- **Persistence**: RDB snapshots, AOF logging
- **Pub/Sub**: Message publishing/subscribing
- **Clustering**: Distributed Redis
- **Caching**: Session storage, cache layer
- **Lua Scripting**: Server-side scripts

## Query Optimization

### Indexing Strategies
```sql
-- Single column index
CREATE INDEX idx_users_email ON users(email);

-- Composite index (PostgreSQL)
CREATE INDEX idx_orders_user_date ON orders(user_id, created_at);

-- Partial index
CREATE INDEX idx_active_users ON users(id) WHERE status = 'active';

-- Full-text search index
CREATE INDEX idx_posts_text ON posts USING gin(to_tsvector('english', content));
```

### Query Analysis
```sql
-- Explain plan
EXPLAIN ANALYZE SELECT * FROM users WHERE email = 'john@example.com';

-- Find missing indexes
SELECT schemaname, tablename FROM pg_tables
WHERE tablename NOT IN (SELECT tablename FROM pg_indexes);
```

## Scaling Databases

### Replication
- **Master-Slave**: Read replicas
- **Multi-Master**: Active-active replication
- **PostgreSQL Streaming**: Real-time replication
- **MongoDB Replica Sets**: Built-in replication

### Sharding
```python
# Hash-based sharding
def get_shard(user_id, num_shards):
    return hash(user_id) % num_shards

# Range-based sharding
def get_shard_by_range(user_id):
    if user_id < 1000:
        return 'shard1'
    elif user_id < 2000:
        return 'shard2'
    else:
        return 'shard3'
```

### Caching Strategies
- **Cache-Aside**: Check cache, then DB
- **Write-Through**: Update cache and DB simultaneously
- **Write-Behind**: Update cache first, then DB
- **Refresh-Ahead**: Proactively refresh cache

## Backup & Disaster Recovery

### PostgreSQL Backup
```bash
# Full backup
pg_dump -U user -d database > backup.sql

# Binary backup
pg_basebackup -D /path/to/backup -U replication_user

# Restore
psql -U user -d database < backup.sql
```

### Replication Setup
- **WAL Archiving**: Write-ahead logging
- **Point-in-Time Recovery**: Recovery to specific time
- **Standby Servers**: Hot standby replicas
- **Failover**: Automatic or manual promotion

## Resources

- **PostgreSQL Docs**: https://www.postgresql.org/docs/
- **MongoDB Docs**: https://docs.mongodb.com/
- **Redis Docs**: https://redis.io/documentation
- **SQL Tutorial**: https://www.w3schools.com/sql/
- **Database Design**: https://www.guru99.com/database-design.html

---

**See Also**: backend-frameworks, system-design, cloud-devops
