---
name: cloud-devops
description: Master cloud platforms and DevOps tools including Docker, Kubernetes, Terraform, AWS, and CI/CD pipelines. Use when building infrastructure, containerizing applications, or setting up deployment automation.
---

# Cloud & DevOps Platforms

## Quick Start

### Docker Basics
```dockerfile
FROM node:18-alpine

WORKDIR /app

COPY package*.json ./
RUN npm install --production

COPY . .

EXPOSE 3000

CMD ["node", "server.js"]
```

```bash
# Build and run
docker build -t myapp:1.0 .
docker run -p 3000:3000 myapp:1.0
```

### Docker Compose
```yaml
version: '3.8'

services:
  app:
    build: .
    ports:
      - "3000:3000"
    environment:
      DATABASE_URL: postgres://db:5432/myapp
    depends_on:
      - db

  db:
    image: postgres:15
    environment:
      POSTGRES_PASSWORD: password
      POSTGRES_DB: myapp
    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  postgres_data:
```

### Kubernetes Basics
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp
spec:
  replicas: 3
  selector:
    matchLabels:
      app: myapp
  template:
    metadata:
      labels:
        app: myapp
    spec:
      containers:
      - name: app
        image: myapp:1.0
        ports:
        - containerPort: 3000
        env:
        - name: DATABASE_URL
          valueFrom:
            secretKeyRef:
              name: db-secret
              key: url
        resources:
          limits:
            memory: "512Mi"
            cpu: "500m"
---
apiVersion: v1
kind: Service
metadata:
  name: myapp-service
spec:
  selector:
    app: myapp
  ports:
  - port: 80
    targetPort: 3000
  type: LoadBalancer
```

### Terraform Infrastructure
```hcl
provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "web" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"

  tags = {
    Name = "my-instance"
  }
}

resource "aws_s3_bucket" "data" {
  bucket = "my-data-bucket"

  versioning {
    enabled = true
  }
}

output "instance_ip" {
  value = aws_instance.web.public_ip
}
```

## Container Technologies

### Docker
- **Images**: Building and managing Docker images
- **Containers**: Running and managing containers
- **Registry**: Docker Hub, ECR, GCR
- **Volumes**: Persistent storage
- **Networks**: Inter-container communication
- **Best Practices**: Multi-stage builds, layer optimization

### Container Orchestration
- **Kubernetes**: Production-grade orchestration
- **Docker Swarm**: Simpler native clustering
- **Amazon ECS**: AWS container service
- **Google Cloud Run**: Serverless containers

## Kubernetes Ecosystem

### Core Components
- **Pods**: Smallest deployable unit
- **Deployments**: Managing replicas
- **Services**: Load balancing and networking
- **ConfigMaps**: Configuration management
- **Secrets**: Sensitive data management
- **PersistentVolumes**: Storage abstraction
- **Ingress**: HTTP routing

### Advanced Topics
- **Namespaces**: Resource isolation
- **RBAC**: Role-based access control
- **NetworkPolicies**: Network segmentation
- **ResourceQuotas**: Resource limits
- **HorizontalPodAutoscaler**: Auto-scaling
- **StatefulSets**: Stateful applications
- **DaemonSets**: Node-wide deployments
- **Operators**: Kubernetes extensions

### Helm Package Manager
```yaml
# values.yaml
image:
  repository: myapp
  tag: 1.0
replicas: 3
service:
  type: LoadBalancer
  port: 80

# In template
apiVersion: apps/v1
kind: Deployment
metadata:
  name: {{ .Release.Name }}-app
spec:
  replicas: {{ .Values.replicas }}
  template:
    spec:
      containers:
      - image: {{ .Values.image.repository }}:{{ .Values.image.tag }}
```

## Infrastructure as Code

### Terraform
- **Providers**: AWS, Google Cloud, Azure, etc.
- **Resources**: Define infrastructure
- **Variables**: Input parameters
- **Outputs**: Export values
- **Modules**: Reusable components
- **State**: Infrastructure state management
- **Remote State**: Shared state with backends

### CloudFormation (AWS)
- **Templates**: JSON/YAML format
- **Stacks**: Collection of resources
- **Change Sets**: Preview changes
- **Nested Stacks**: Reusable components
- **Parameters**: Input values

## AWS Services

### Compute
- **EC2**: Virtual machines
- **Lambda**: Serverless functions
- **ECS**: Container orchestration
- **EKS**: Managed Kubernetes
- **Elastic Beanstalk**: PaaS platform

### Storage & Database
- **S3**: Object storage
- **EBS**: Block storage
- **RDS**: Relational databases
- **DynamoDB**: NoSQL database
- **ElastiCache**: Caching service

### Networking
- **VPC**: Virtual private cloud
- **ELB/ALB**: Load balancing
- **Route 53**: DNS service
- **CloudFront**: CDN
- **VPN/Direct Connect**: Secure connections

### Monitoring & Logging
- **CloudWatch**: Metrics and logs
- **X-Ray**: Distributed tracing
- **CloudTrail**: API logging

## CI/CD Pipelines

### GitHub Actions
```yaml
name: Deploy

on:
  push:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3

    - name: Build
      run: npm run build

    - name: Test
      run: npm test

    - name: Deploy
      run: npm run deploy
      env:
        DEPLOY_KEY: ${{ secrets.DEPLOY_KEY }}
```

### GitLab CI
```yaml
stages:
  - build
  - test
  - deploy

build:
  stage: build
  script:
    - npm install
    - npm run build
  artifacts:
    paths:
      - dist/

test:
  stage: test
  script:
    - npm test

deploy:
  stage: deploy
  script:
    - ./deploy.sh
  only:
    - main
```

## Monitoring & Observability

### Prometheus & Grafana
```yaml
global:
  scrape_interval: 15s

scrape_configs:
  - job_name: 'app'
    static_configs:
      - targets: ['localhost:9090']

alerting:
  alertmanagers:
    - static_configs:
        - targets: ['localhost:9093']
```

### ELK Stack (Elasticsearch, Logstash, Kibana)
- Log aggregation and analysis
- Real-time visualization
- Full-text search capabilities
- Alerting based on logs

### Other Tools
- **Datadog**: APM and monitoring
- **New Relic**: Application performance monitoring
- **Splunk**: Log analysis and monitoring
- **CloudFlare**: Edge network and DDoS protection

## Linux Administration

### Essential Commands
```bash
# System info
uname -a
lsb_release -a
ps aux

# File management
ls -la
find . -name "*.log"
tar -czf backup.tar.gz ./data

# User management
useradd username
passwd username
sudo usermod -aG sudo username

# Networking
ifconfig
netstat -tuln
curl -X GET http://example.com

# Package management
apt update && apt upgrade
yum install package_name

# Process management
systemctl start service
systemctl enable service
```

## Resources

- **Docker Docs**: https://docs.docker.com/
- **Kubernetes Docs**: https://kubernetes.io/docs/
- **Terraform**: https://terraform.io/
- **AWS Documentation**: https://docs.aws.amazon.com/
- **Linux Academy**: https://linuxacademy.com/
- **O'Reilly**: https://learning.oreilly.com/

---

**See Also**: system-design, database-technologies, security-compliance
