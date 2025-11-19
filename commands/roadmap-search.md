# /roadmap-search

Search across all 77+ developer roadmaps and learning paths from roadmap.sh.

## Usage

```
/roadmap-search [query]
/roadmap-search [topic] [difficulty]
/roadmap-search [skill] [role]
```

## Search Examples

### By Technology
```
/roadmap-search React
/roadmap-search Docker
/roadmap-search PostgreSQL
/roadmap-search Kubernetes
```

Results show:
- Which roadmaps cover this technology
- Recommended order of learning
- Related technologies
- Difficulty level

### By Skill
```
/roadmap-search API Design
/roadmap-search System Design
/roadmap-search Security
/roadmap-search Performance Optimization
```

Results show:
- How the skill fits into different roles
- Required prerequisites
- Practice projects
- Recommended resources

### By Role
```
/roadmap-search Frontend Developer
/roadmap-search Backend Engineer
/roadmap-search DevOps Engineer
/roadmap-search Data Scientist
/roadmap-search Product Manager
```

Results show:
- Complete role roadmap
- Required skills and knowledge
- Learning timeline
- Career progression

### By Difficulty
```
/roadmap-search JavaScript beginner
/roadmap-search System Design advanced
/roadmap-search ML intermediate
/roadmap-search Kubernetes expert
```

Results show:
- Content at that difficulty level
- Prerequisites needed
- Next steps after mastery

## Available Roadmaps (77+)

### Role-Based Roadmaps (30)
**Beginner Paths:**
- Frontend Beginner
- Backend Beginner
- DevOps Beginner

**Core Developer Roles:**
- Frontend Developer
- Backend Developer
- Full Stack Developer

**Specialized Roles:**
- Android Developer
- iOS Developer
- Mobile Developer
- QA Engineer
- API Designer

**Leadership:**
- Software Architect
- Engineering Manager
- Product Manager
- Technical Writer
- DevRel Engineer

**Specialized Tech:**
- PostgreSQL DBA
- Blockchain Developer
- Cyber Security Specialist
- Client Side Game Developer
- Server Side Game Developer
- UX Designer

**AI/Data Roles:**
- Machine Learning Engineer
- AI Engineer
- AI and Data Scientist
- AI Agents Specialist
- Data Analyst
- BI Analyst
- Data Engineer
- MLOps Engineer

### Skill-Based Roadmaps (40+)

**Frontend Technologies:**
- HTML & Web Fundamentals
- CSS Styling
- JavaScript Programming
- TypeScript Advanced
- React Framework
- Vue.js Framework
- Angular Framework
- Next.js Full-Stack
- Design Systems

**Backend Technologies:**
- Node.js Runtime
- Python Language
- PHP Language
- Java Language
- Go Language
- Rust Systems
- C++ Programming
- Kotlin Language
- Spring Boot Framework
- ASP.NET Core Framework
- Laravel Framework

**Mobile Development:**
- React Native
- Flutter Framework
- Swift Programming

**Database Technologies:**
- SQL Fundamentals
- MongoDB NoSQL
- Redis Caching
- GraphQL Query Language

**DevOps & Infrastructure:**
- Docker Containerization
- Kubernetes Orchestration
- Linux Systems
- Terraform IaC
- AWS Cloud Platform
- Cloudflare CDN

**Computer Science:**
- Computer Science Basics
- Data Structures
- System Design
- Design Patterns

**Advanced Topics:**
- Git & GitHub Version Control
- Shell Scripting
- Code Review Practices
- Backend Performance
- Frontend Performance
- AWS Solutions Architecture
- API Security
- AI Red Teaming
- Prompt Engineering

## Advanced Search Features

### Search with Filters

```
/roadmap-search React --difficulty beginner
/roadmap-search Node.js --role backend
/roadmap-search Docker --duration 4weeks
/roadmap-search SQL --combined-with frontend
```

Filter Options:
- `--difficulty` - beginner, intermediate, advanced, expert
- `--role` - Any role from available roles
- `--duration` - Learning time estimate (weeks)
- `--combined-with` - Technologies to learn together
- `--projects` - Number of practical projects
- `--trend` - emerging, stable, declining

### Relationship Search

```
/roadmap-search what-comes-after React
/roadmap-search prerequisite-for DevOps
/roadmap-search alternative-to React
/roadmap-search complements Node.js
```

Shows:
- Natural learning progression
- Skills that complement each other
- Alternative technologies
- Common combinations

## Search Results Format

### Example 1: Technology Search
```
/roadmap-search React

REACT ROADMAP RESULTS
====================

Main Roadmap: React Framework

Part Of These Roles:
├─ Frontend Developer (Core)
├─ Full Stack Developer (Core)
└─ Web Development (Intermediate)

Prerequisites:
├─ HTML Fundamentals
├─ CSS Styling
├─ JavaScript ES6+
└─ Problem-Solving (Mindset)

Learning Path:
1. React Fundamentals (2 weeks)
   - Components and JSX
   - Props and State
   - Hooks (useState, useEffect)

2. Intermediate Concepts (3 weeks)
   - Context API
   - Custom Hooks
   - Performance Optimization

3. Advanced Patterns (2 weeks)
   - Server Components
   - Advanced Hooks
   - Framework Integration (Next.js)

Related Technologies:
├─ TypeScript (Recommended)
├─ Next.js (Enhancement)
├─ Redux (State Management)
└─ React Testing Library (Testing)

Practical Projects:
├─ Todo Application (Beginner)
├─ E-commerce Frontend (Intermediate)
├─ Real-time Dashboard (Advanced)
└─ Full-stack SaaS (Expert)

Time Estimate: 6-8 weeks at 10 hrs/week

Relevant Agent: Frontend Web Development Agent
```

### Example 2: Role Search
```
/roadmap-search Backend Developer

BACKEND DEVELOPER ROADMAP
==========================

Duration: 9-12 months (full-time), 18-24 months (part-time)

Core Topics:
├─ Programming Language Basics
├─ Web Frameworks
├─ Database Design
├─ API Design Patterns
├─ Security Fundamentals
├─ Deployment & DevOps
└─ System Design

Required Skills (Choose 1 Language):
├─ Node.js + Express
├─ Python + Django/FastAPI
├─ Java + Spring Boot
└─ Go + Gin

Optional Advanced:
├─ Microservices Architecture
├─ Event Streaming (Kafka)
├─ GraphQL APIs
└─ Container Orchestration

Projects:
├─ REST API (Todo app)
├─ Multi-entity API (E-commerce)
├─ Real-time Service
└─ Distributed System

Career Progression:
Junior → Senior → Tech Lead → Architect

Relevant Agent: Backend & Server Development Agent
```

## Search Tips

1. **Broad Searches** - Search for a topic to see all related content
2. **Specific Searches** - Search for exact technologies or roles
3. **Combination Searches** - Find how topics relate
4. **Difficulty Matching** - Filter by your current level
5. **Progression Searches** - Find what to learn next

## Common Search Queries

**"I want to learn X"**
```
/roadmap-search web development
/roadmap-search machine learning
/roadmap-search cloud infrastructure
```

**"What's required for Y?"**
```
/roadmap-search prerequisites-for full-stack
/roadmap-search required-skills-for DevOps
/roadmap-search foundation-for system-design
```

**"What comes after Z?"**
```
/roadmap-search what-after-frontend
/roadmap-search next-steps-after-react
/roadmap-search advanced-topics-node.js
```

## Combine with Other Commands

### Workflow Example
```
1. /roadmap-search backend
   (Explore Backend Developer roadmap)

2. /explore-agents backend-server-development
   (Learn about Backend Agent)

3. /learn-roadmap
   (Start structured learning for Backend)

4. /skill-assessment backend
   (Test current backend knowledge)

5. /roadmap-search node.js intermediate
   (Find Node.js intermediate content)
```

## Save and Share Results

After searching, you can:
- **Save** results to your learning dashboard
- **Share** with colleagues or mentors
- **Create** custom learning plans
- **Compare** multiple roadmaps side-by-side
- **Track** progress through saved roadmaps

## Search Performance

- Real-time search across 77+ roadmaps
- Instant results
- Related content suggestions
- Trending topics highlighted
- Community recommendations

## Get Help

If you need guidance:
- Use `/explore-agents` to find relevant experts
- Ask agents about search results
- Request personalized learning plans
- Connect with community mentors

## Related Commands

- `/learn-roadmap` - Start a structured learning path
- `/explore-agents` - Get expert guidance
- `/skill-assessment` - Evaluate your knowledge
