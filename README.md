# AppSecops_SAST_DAST_SCA

# 🔐 DevSecOps Security Testing Demo
## 🛡️ SAST | 📦 SCA | 🌐 DAST

Welcome to this hands-on DevSecOps Security Testing Demonstration Repository.

This project showcases practical implementation of:
### 🔎 SAST – Static Application Security Testing
### 📦 SCA – Software Composition Analysis
### 🌐 DAST – Dynamic Application Security Testing

Each security domain includes:
- Setup steps
- Docker usage
- CLI commands
- Vulnerability findings
- Screenshots
- Report generation
- Production considerations

🏗 Repository Structure
.
├── README.md
├── screenshots/
│   ├── SAST-Demo.md
│   ├── SCA-Demo.md
│   ├── DAST-Demo.md
│   ├── images/
│   └── demo-videos/

### 🔎 1️⃣ SAST – Static Application Security Testing

Tool Used:

#### 🐳 SonarQube (Community Edition)

#### 🛠 Sonar Scanner CLI

Detects:
- Insecure coding patterns
- Hardcoded secrets
- Weak randomness
- Security vulnerabilities
- Code smells
- Technical debt

#### 📘 View Detailed Guide Here:
👉 Go to SAST Demo Documentation

#### 📸 Includes:
- SonarQube setup
- Token generation
- sonar-project.properties setup
- Vulnerability screenshots
- Risk analysis

### 📦 2️⃣ SCA – Software Composition Analysis

Tool Used:

v🐍 pip-audit
- Detects:
- Vulnerable dependencies
- Indirect (transitive) vulnerabilities
- CVE references
- Secure upgrade recommendations

#### 📘 View Detailed Guide Here:

#### 📸 Includes:
- Virtual environment setup
- pip-audit scanning
- CVE breakdown
- Dependency tree explanation

### 🌐 3️⃣ DAST – Dynamic Application Security Testing

Tools Used:
- 🐳 OWASP ZAP
- 🧃 OWASP Juice Shop (Vulnerable App)

Detects:
- Runtime vulnerabilities
- XSS
- SQL Injection
- Insecure headers
- Authentication flaws

#### 📘 View Detailed Guide Here:

#### 📸 Includes:
- Juice Shop setup
- ZAP CLI scan
- ZAP UI scan
- HTML report generation
- Runtime vulnerability findings


#### 🔄 DevSecOps Pipeline Overview

Developer Code
      ↓
SAST (Code Scan)
      ↓
SCA (Dependency Scan)
      ↓
Build & Deploy
      ↓
DAST (Runtime Scan)

This demonstrates shift-left security and full lifecycle security validation.

#### 🧠 Why This Matters

Modern applications are vulnerable at multiple layers:
| Layer        | Tool | Purpose                    |
| ------------ | ---- | -------------------------- |
| Source Code  | SAST | Secure coding validation   |
| Dependencies | SCA  | Supply-chain protection    |
| Runtime      | DAST | Live vulnerability testing |

Security must be integrated across the entire SDLC.

#### 🏭 Production Considerations
- SonarQube Enterprise recommended for organizations
- CI/CD integration for automated scanning
- Vulnerability gating before deployment
- Database-backed SonarQube setup
- Kubernetes deployment options

#### 🚀 How To Use This Repository
- Navigate to each .md file inside screenshots/
- Follow step-by-step instructions
- Review screenshots and generated reports
- Understand vulnerability patterns and remediation