---
name: system-design
description: Master system design principles for building scalable, reliable, and maintainable systems. Use when designing large-scale applications, planning architecture, or preparing for system design interviews.
sasmp_version: "1.3.0"
bonded_agent: 01-frontend-web-development
bond_type: PRIMARY_BOND
---

# System Design & Architecture

## Quick Start: Designing a URL Shortener

### Requirements
- **Functional**: Shorten URLs, redirect to original URL, track usage
- **Non-functional**: Low latency, high availability, durability

### High-Level Architecture
```
Client
  ↓
Load Balancer
  ↓
API Gateway (Multiple instances)
  ↓
[Cache Layer - Redis] [Database - PostgreSQL]
  ↓
Message Queue (for async tasks)
  ↓
Analytics Service
```

### Database Schema
```sql
CREATE TABLE urls (
    id SERIAL PRIMARY KEY,
    short_code VARCHAR(8) UNIQUE,
    original_url TEXT,
    user_id INTEGER,
    created_at TIMESTAMP,
    updated_at TIMESTAMP
);

CREATE TABLE stats (
    url_id INTEGER,
    click_count INTEGER DEFAULT 0,
    last_accessed TIMESTAMP
);

CREATE INDEX idx_short_code ON urls(short_code);
```

### API Design
```
POST /api/shorten
{
    "originalUrl": "https://example.com/very/long/url"
}
→ 201 Created
{
    "shortUrl": "http://short.url/abc123"
}

GET /api/{shortCode}
→ 301 Moved Permanently
Location: https://example.com/very/long/url
```

## Core Principles

### Scalability
- **Horizontal Scaling**: Adding more servers
- **Vertical Scaling**: More powerful servers
- **Load Balancing**: Distributing traffic
- **Caching**: Reducing database load
- **Sharding**: Partitioning data
- **Microservices**: Breaking into independent services

### Reliability
- **Redundancy**: Backup components
- **Failover**: Automatic recovery
- **Monitoring**: Health checks
- **Alerting**: Notifying on issues
- **Graceful Degradation**: Partial functionality

### Availability (99.99% Uptime)
```
99.9%   = 8.77 hours downtime/year
99.99%  = 52.6 minutes downtime/year
99.999% = 5.26 minutes downtime/year
```

### Performance
- **Latency**: Time to respond
- **Throughput**: Requests per second
- **Response Time**: User-perceived performance

## Architectural Patterns

### Monolithic Architecture
```
Single Application
├── Auth Module
├── Product Module
├── Order Module
└── Payment Module
    ↓
Single Database
```

Pros: Simple deployment, easier debugging
Cons: Tight coupling, scaling difficulty

### Microservices Architecture
```
API Gateway
├── Auth Service → Auth DB
├── Product Service → Product DB
├── Order Service → Order DB
└── Payment Service → Payment DB
```

Pros: Independent scaling, tech flexibility
Cons: Complexity, distributed transactions

### Serverless Architecture
```
API Gateway → Lambda Functions
              ├── HTTP Handler
              ├── Event Handler
              └── Scheduler
                ↓
            DynamoDB, S3, SNS
```

### Event-Driven Architecture
```
Event Source → Event Broker (Kafka/RabbitMQ)
                ├── Consumer 1
                ├── Consumer 2
                └── Consumer 3
```

## Design Patterns

### Caching Patterns
```python
# Cache-Aside
def get_user(user_id):
    cached = cache.get(f'user:{user_id}')
    if cached:
        return cached
    user = db.get_user(user_id)
    cache.set(f'user:{user_id}', user, ttl=3600)
    return user

# Write-Through
def update_user(user_id, data):
    db.update_user(user_id, data)
    cache.set(f'user:{user_id}', data)
    return data
```

### Circuit Breaker Pattern
```python
class CircuitBreaker:
    def __init__(self, failure_threshold=5):
        self.failure_count = 0
        self.threshold = failure_threshold
        self.state = 'closed'  # closed, open, half-open

    def call(self, func, *args):
        if self.state == 'open':
            raise Exception("Circuit is open")

        try:
            result = func(*args)
            self.failure_count = 0
            return result
        except Exception as e:
            self.failure_count += 1
            if self.failure_count >= self.threshold:
                self.state = 'open'
            raise e
```

### Saga Pattern (Distributed Transactions)
```
Order Service:
  1. Create Order (pending)
  2. Send to Payment Service

Payment Service:
  1. Process Payment
  2. On success: Send to Inventory Service
  3. On failure: Rollback Order

Inventory Service:
  1. Reserve Items
  2. On success: Send to Shipping Service
  3. On failure: Refund Payment & Rollback Order
```

## Database Design at Scale

### Normalization vs Denormalization
```sql
-- Normalized (optimized for writes)
CREATE TABLE users (id, name, email);
CREATE TABLE posts (id, user_id, content);
CREATE TABLE comments (id, post_id, user_id, content);

-- Denormalized (optimized for reads)
CREATE TABLE posts (
    id,
    content,
    user_id,
    user_name,
    user_email,
    comment_count,
    like_count
);
```

### Partitioning Strategies
- **Hash Partitioning**: user_id % num_partitions
- **Range Partitioning**: By date ranges
- **Directory-based**: Lookup table for partitions
- **Geo-partitioning**: By location

## Monitoring & Observability

### Key Metrics (The RED Method)
- **Rate**: Requests per second
- **Errors**: Error rate percentage
- **Duration**: Response time percentiles

### Logging Strategy
```
Application → Log Aggregator (Logstash) → Search (Elasticsearch) → Visualization (Kibana)
```

### Distributed Tracing
- **Trace ID**: Request identifier
- **Span ID**: Operation identifier
- **Parent Span**: Relationship between operations

## Resources

- **System Design Primer**: https://github.com/donnemartin/system-design-primer
- **Designing Data-Intensive Applications**: Book
- **High Scalability**: https://highscalability.com/
- **InfoQ**: https://www.infoq.com/
- **USENIX**: https://www.usenix.org/

---

**See Also**: database-technologies, cloud-devops, backend-frameworks
