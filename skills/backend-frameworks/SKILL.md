---
name: backend-frameworks
description: Master backend frameworks and languages including Node.js, Python, Java, Go, GraphQL, and RESTful API design. Use when building server applications, APIs, or backend services.
sasmp_version: "1.3.0"
bonded_agent: 01-frontend-web-development
bond_type: PRIMARY_BOND
---

# Backend Frameworks & Languages

## Quick Start

### Node.js with Express
```javascript
const express = require('express');
const app = express();

app.use(express.json());

// Middleware
app.use(logger);

// Route handlers
app.get('/api/users/:id', async (req, res) => {
  try {
    const user = await db.users.findById(req.params.id);
    res.json(user);
  } catch (error) {
    res.status(500).json({ error: error.message });
  }
});

app.listen(3000);
```

### Python with FastAPI
```python
from fastapi import FastAPI, HTTPException
from pydantic import BaseModel

app = FastAPI()

class User(BaseModel):
    id: int
    name: str
    email: str

@app.get("/users/{user_id}")
async def get_user(user_id: int):
    user = await db.users.find_by_id(user_id)
    if not user:
        raise HTTPException(status_code=404, detail="User not found")
    return user

@app.post("/users")
async def create_user(user: User):
    return await db.users.insert(user)
```

### Java with Spring Boot
```java
@RestController
@RequestMapping("/api/users")
public class UserController {

    @Autowired
    private UserService userService;

    @GetMapping("/{id}")
    public ResponseEntity<User> getUser(@PathVariable Long id) {
        return userService.findById(id)
            .map(ResponseEntity::ok)
            .orElseGet(() -> ResponseEntity.notFound().build());
    }

    @PostMapping
    public ResponseEntity<User> createUser(@RequestBody User user) {
        User created = userService.save(user);
        return ResponseEntity.status(201).body(created);
    }
}
```

### Go with Gin
```go
package main

import "github.com/gin-gonic/gin"

func main() {
    router := gin.Default()

    router.GET("/api/users/:id", func(c *gin.Context) {
        id := c.Param("id")
        user, err := db.GetUser(id)
        if err != nil {
            c.JSON(404, gin.H{"error": "User not found"})
            return
        }
        c.JSON(200, user)
    })

    router.Run(":3000")
}
```

## RESTful API Design

### Best Practices
```javascript
// Resource-oriented endpoints
GET    /api/users           // List users
POST   /api/users           // Create user
GET    /api/users/123       // Get user by ID
PUT    /api/users/123       // Update user
DELETE /api/users/123       // Delete user

// Nested resources
GET    /api/users/123/posts // Get user's posts
POST   /api/users/123/posts // Create post for user

// Query parameters
GET    /api/users?page=1&limit=10&sort=name
GET    /api/posts?filter[status]=published&fields=title,author

// Versioning
GET    /api/v1/users
GET    /api/v2/users
```

### HTTP Status Codes
- **2xx**: Success (200, 201, 204)
- **3xx**: Redirect (301, 302, 304)
- **4xx**: Client error (400, 401, 403, 404, 409)
- **5xx**: Server error (500, 502, 503)

## GraphQL API Design

```graphql
type User {
  id: ID!
  name: String!
  email: String!
  posts: [Post!]!
}

type Post {
  id: ID!
  title: String!
  content: String!
  author: User!
}

type Query {
  user(id: ID!): User
  users(limit: Int, offset: Int): [User!]!
  post(id: ID!): Post
}

type Mutation {
  createUser(name: String!, email: String!): User!
  createPost(title: String!, content: String!, userId: ID!): Post!
  updateUser(id: ID!, name: String, email: String): User
  deleteUser(id: ID!): Boolean!
}
```

## Framework Comparison

### Node.js Ecosystem
- **Express**: Minimalist, flexible, large ecosystem
- **Fastify**: High performance, plugin system
- **Hapi**: Enterprise-grade, built-in features
- **NestJS**: TypeScript-first, modular, opinionated

### Python Ecosystem
- **FastAPI**: Modern, async, auto-documentation
- **Django**: Full-featured, batteries included
- **Flask**: Lightweight, microframework
- **Bottle**: Minimal, single-file deployments

### Java Ecosystem
- **Spring Boot**: Enterprise standard, ecosystem
- **Quarkus**: Cloud-native, fast startup
- **Micronaut**: Lightweight, GraalVM compatible
- **Dropwizard**: Simple REST services

### Go Ecosystem
- **Gin**: Fast HTTP router and framework
- **Echo**: Minimalist and fast
- **Fiber**: Express.js inspired
- **Chi**: Lightweight router and middleware

## Advanced Topics

### Authentication & Authorization
- **JWT (JSON Web Tokens)**: Stateless authentication
- **OAuth 2.0**: Third-party authorization
- **OpenID Connect**: Identity verification
- **Session-based**: Server-side sessions
- **RBAC**: Role-based access control

### Error Handling
```javascript
// Custom error classes
class ValidationError extends Error {
  constructor(message) {
    super(message);
    this.status = 400;
  }
}

// Global error handler
app.use((err, req, res, next) => {
  const status = err.status || 500;
  res.status(status).json({ error: err.message });
});
```

### Middleware & Interceptors
- Request logging
- Authentication/Authorization
- Request validation
- Rate limiting
- CORS handling
- Compression
- Error handling

### Database Integration
- **ORM/ODM**: Sequelize, TypeORM, Prisma, SQLAlchemy, Mongoose
- **Query Builders**: Knex.js, SQLc
- **Connection Pooling**: Managing database connections
- **Migrations**: Alembic, db-migrate
- **Transactions**: ACID compliance

## Resources

- **Node.js Docs**: https://nodejs.org/docs/
- **Express Guide**: https://expressjs.com/
- **FastAPI Docs**: https://fastapi.tiangolo.com/
- **Spring Boot Docs**: https://spring.io/projects/spring-boot
- **Go Official Site**: https://golang.org/
- **RESTful API Design**: https://restfulapi.net/
- **GraphQL Official**: https://graphql.org/

---

**See Also**: api-design, database-technologies, system-design
