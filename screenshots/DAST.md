# 🔐 DAST Demo Using OWASP ZAP & OWASP Juice Shop
### 🎯 Objective

Demonstrate Dynamic Application Security Testing (DAST) by scanning a vulnerable web application using OWASP ZAP running inside Docker.

This POC shows:
- Running a vulnerable application (Juice Shop)
- Scanning it using OWASP ZAP (CLI & UI)
- Generating an HTML security report

🧪 What is DAST?

Dynamic Application Security Testing (DAST) analyzes applications at runtime by simulating external attacks.

Unlike SAST:
- ❌ Does not scan source code
- ✅ Tests running application behavior
- ✅ Detects runtime vulnerabilities
- ✅ Finds misconfigurations, XSS, SQLi, etc.

## 🧃 Vulnerable Target Application

We use:

🔗 https://github.com/juice-shop/juice-shop

OWASP Juice Shop is an intentionally vulnerable e-commerce application designed for security testing and training.

## 🎥 DAST Demo Video Walkthrough
<video src="DAST-Demo.mp4" controls width="800"></video>


🚀 Step 1 — Run Juice Shop (Target Application)
```bash
docker run -d \
  --name juice-shop \
  -p 3000:3000 \
  bkimminich/juice-shop
```
🌐 Open in Browser
http://localhost:3000

Application should now be running.

🛠 Step 2 — Run OWASP ZAP via CLI (Automated Scan)
🐳 Run ZAP Baseline Scan (Generate HTML Report)
```bash
docker run --rm \
  -v "$(pwd):/zap/wrk" \
  -t ghcr.io/zaproxy/zaproxy:stable \
  zap-baseline.py \
  -t http://host.docker.internal:3000 \
  -r zap-report.html
```

  🪟 Windows (Git Bash) Fix

If the above command fails, use:
```bash
MSYS_NO_PATHCONV=1 docker run --rm \
  -v "$(pwd):/zap/wrk" \
  -t ghcr.io/zaproxy/zaproxy:stable \
  zap-baseline.py \
  -t http://host.docker.internal:3000 \
  -r zap-report.html
```

📄 Output

A file will be generated:

zap-report.html

Open it in your browser to view:
- High / Medium / Low vulnerabilities
- Alerts
- Risk classification
- Evidence
- Recommendations


🖥 Step 3 — Run OWASP ZAP via UI (Interactive Scan)
🐳 Start ZAP UI
```bash
docker run -it \
  -p 8080:8080 \
  ghcr.io/zaproxy/zaproxy:stable \
  zap-webswing.sh
```
  🪟 Windows Git Bash Fix
```bash
  MSYS_NO_PATHCONV=1 docker run -it \
  -p 8080:8080 \
  ghcr.io/zaproxy/zaproxy:stable \
  zap-webswing.sh
```

🌐 Open ZAP UI
```bash
http://localhost:8080/zap
```

From the UI:

- 1. Enter target URL:
http://host.docker.internal:3000
- 2. Start automated scan
- 3. Explore vulnerabilities visually

📊 What ZAP Does
- Crawls the application
- Discovers endpoints
- Performs active/passive scanning
- Simulates attack payloads
- Generates vulnerability report

🔎 Types of Vulnerabilities Detected
- Cross-Site Scripting (XSS)
- SQL Injection
- Insecure Headers
- Sensitive Information Exposure
- Broken Authentication
- Misconfigurations
- Insecure Cookies

🏗 Architecture Overview

User
  ↓
OWASP ZAP (Docker)
  ↓
Juice Shop (Docker)
  ↓
HTML Report

🧠 Why Use Docker for DAST?
- No local installation required
- Isolated environment
- Easy CI/CD integration
- Reproducible testing

🔄 CI/CD Integration Idea

You can integrate this into pipelines:
```bash
zap-baseline.py \
  -t http://app-url \
  -r zap-report.html \
  -x zap-report.xml
```

Then:
- Upload report as pipeline artifact
- Fail build on high severity findings

⚠ Important Notes
- Juice Shop is intentionally vulnerable.
- Never run DAST scans on applications without authorization.
- For production, consider authenticated scans.

🏆 Summary
| Component       | Purpose                  |
| --------------- | ------------------------ |
| Juice Shop      | Vulnerable target app    |
| OWASP ZAP       | DAST scanner             |
| Docker          | Runtime environment      |
| zap-report.html | Security findings report |


