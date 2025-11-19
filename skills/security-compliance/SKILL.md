---
name: security-compliance
description: Master security principles, cryptography, compliance frameworks, and secure development practices. Use when securing applications, implementing authentication/authorization, or ensuring regulatory compliance.
---

# Security & Compliance

## Quick Start

### Basic Authentication with JWT
```javascript
const jwt = require('jsonwebtoken');

// Generate token
const token = jwt.sign(
    { userId: 123, email: 'user@example.com' },
    'secret_key',
    { expiresIn: '24h' }
);

// Verify token
const decoded = jwt.verify(token, 'secret_key');
console.log(decoded);
```

### Password Hashing
```python
from werkzeug.security import generate_password_hash, check_password_hash

# Hash password
hashed = generate_password_hash('password123', method='pbkdf2:sha256')

# Verify password
check_password_hash(hashed, 'password123')  # True
check_password_hash(hashed, 'wrong')         # False
```

### HTTPS/TLS Configuration
```nginx
server {
    listen 443 ssl http2;
    ssl_certificate /path/to/cert.pem;
    ssl_certificate_key /path/to/key.pem;
    ssl_protocols TLSv1.2 TLSv1.3;
    ssl_ciphers HIGH:!aNULL:!MD5;
}
```

## Authentication & Authorization

### Authentication Methods
- **Username/Password**: Basic form-based
- **Multi-Factor Authentication (MFA)**: TOTP, SMS, U2F
- **OAuth 2.0**: Third-party authorization
- **SAML**: Enterprise single sign-on
- **OpenID Connect**: Identity layer on OAuth
- **Session-based**: Server-side sessions
- **Token-based**: JWT, API tokens

### Authorization Models
```python
# Role-Based Access Control (RBAC)
USER_ROLES = {
    'admin': ['read', 'write', 'delete', 'manage_users'],
    'editor': ['read', 'write'],
    'viewer': ['read']
}

def check_permission(user_role, action):
    return action in USER_ROLES.get(user_role, [])

# Attribute-Based Access Control (ABAC)
def has_access(user, resource):
    return (
        user.organization == resource.organization and
        user.department in resource.allowed_departments and
        resource.created_by == user.id or user.role == 'admin'
    )
```

## Cryptography

### Encryption Types
- **Symmetric**: Same key for encryption/decryption (AES-256)
- **Asymmetric**: Public/private key pairs (RSA, ECDSA)
- **Hashing**: One-way function (SHA-256, bcrypt)

### Practical Examples
```python
from cryptography.fernet import Fernet

# Symmetric encryption
key = Fernet.generate_key()
cipher = Fernet(key)
encrypted = cipher.encrypt(b"secret message")
decrypted = cipher.decrypt(encrypted)

# Asymmetric encryption
from cryptography.hazmat.primitives import serialization, hashes
from cryptography.hazmat.primitives.asymmetric import rsa, padding

private_key = rsa.generate_private_key(public_exponent=65537, key_size=2048)
public_key = private_key.public_key()

# Encrypt with public key
encrypted = public_key.encrypt(
    b"secret",
    padding.OAEP(hashes.SHA256())
)

# Decrypt with private key
decrypted = private_key.decrypt(encrypted, padding.OAEP(hashes.SHA256()))
```

## OWASP Top 10 Vulnerabilities

### 1. SQL Injection
```python
# ❌ VULNERABLE
query = f"SELECT * FROM users WHERE id = {user_id}"

# ✅ SAFE (Parameterized query)
query = "SELECT * FROM users WHERE id = %s"
cursor.execute(query, (user_id,))
```

### 2. Broken Authentication
- Weak password policies
- Insufficient password hashing
- Missing rate limiting on login attempts
- Session fixation vulnerabilities

### 3. Sensitive Data Exposure
```javascript
// ✅ SAFE: Hash and salt passwords
bcrypt.hash(password, 10);

// ✅ SAFE: Use HTTPS/TLS
// ✅ SAFE: Encrypt sensitive fields at rest
// ✅ SAFE: Never log sensitive data
```

### 4. XML External Entities (XXE)
```python
# ❌ VULNERABLE
import xml.etree.ElementTree as ET
tree = ET.parse(user_input)  # Can be XXE attack

# ✅ SAFE: Disable external entities
from xml.etree.ElementTree import XMLParser
parser = XMLParser(resolve_entities=False)
tree = ET.parse(user_input, parser)
```

### 5. Broken Access Control
```python
# ❌ VULNERABLE: Missing auth check
@app.route('/admin')
def admin():
    return "Admin panel"

# ✅ SAFE: Check user role
@app.route('/admin')
def admin():
    if current_user.role != 'admin':
        abort(403)
    return "Admin panel"
```

### 6. Security Misconfiguration
- Default credentials
- Unnecessary services enabled
- Outdated libraries
- Missing security headers

### 7. Cross-Site Scripting (XSS)
```javascript
// ❌ VULNERABLE: Direct HTML injection
document.innerHTML = userInput;

// ✅ SAFE: Text content only
document.textContent = userInput;

// ✅ SAFE: Escape HTML
const div = document.createElement('div');
div.textContent = userInput;
```

### 8. Insecure Deserialization
- Don't deserialize untrusted data
- Use whitelists for serialization
- Validate input schema

### 9. Using Components with Known Vulnerabilities
```bash
# Check for vulnerable dependencies
npm audit
pip check
cargo audit
```

### 10. Insufficient Logging & Monitoring
```python
# ✅ GOOD: Log security events
import logging

logger.warning(f"Failed login attempt for user: {username}")
logger.error(f"Unauthorized access attempt to /admin by {user_id}")
logger.info(f"Password changed for user: {user_id}")
```

## Secure Development Practices

### Input Validation
```javascript
// Whitelist validation
const VALID_ROLES = ['admin', 'user', 'guest'];
function validateRole(role) {
    if (!VALID_ROLES.includes(role)) {
        throw new Error('Invalid role');
    }
}

// Type checking
function processUser(user) {
    if (typeof user !== 'object' || !user.id) {
        throw new Error('Invalid user object');
    }
}
```

### Security Headers
```javascript
// Express.js
const helmet = require('helmet');
app.use(helmet());

// Or manually:
app.use((req, res, next) => {
    res.setHeader('X-Content-Type-Options', 'nosniff');
    res.setHeader('X-Frame-Options', 'DENY');
    res.setHeader('X-XSS-Protection', '1; mode=block');
    res.setHeader('Strict-Transport-Security', 'max-age=31536000; includeSubDomains');
    next();
});
```

## Compliance Frameworks

### GDPR (General Data Protection Regulation)
- User consent for data collection
- Right to access personal data
- Right to be forgotten
- Data breach notification within 72 hours
- Data Protection Impact Assessment (DPIA)

### HIPAA (Health Insurance Portability and Accountability Act)
- Encrypt Protected Health Information (PHI)
- Access controls and audit logs
- Incident response procedures
- Business Associate Agreements (BAA)

### PCI DSS (Payment Card Industry Data Security Standard)
- Encrypt cardholder data
- Use secure authentication
- Maintain firewall configuration
- Regular security testing
- Implement access control measures

### SOC 2
- Security controls (5 trust service categories)
- Availability, processing integrity, confidentiality
- Privacy, security management processes

## Security Tools & Practices

### Code Security Scanning
```bash
# SAST (Static Application Security Testing)
snyk test
sonarqube scan

# DAST (Dynamic Application Security Testing)
owasp-zap scan
burp-suite
```

### Dependency Management
```bash
# Check for vulnerabilities
npm audit
pip check
composer audit

# Use specific versions
npm ci
pip install -r requirements.txt
```

### Penetration Testing
- Authorized security testing
- Vulnerability identification
- Exploitation testing
- Report and remediation

## Resources

- **OWASP**: https://owasp.org/
- **OWASP Top 10**: https://owasp.org/www-project-top-ten/
- **CWE**: https://cwe.mitre.org/
- **Snyk**: https://snyk.io/
- **HackerOne**: https://www.hackerone.com/
- **Security Headers**: https://securityheaders.com/

---

**See Also**: backend-frameworks, cloud-devops
