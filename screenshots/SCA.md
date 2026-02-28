# 🛡️ Software Composition Analysis (SCA) – Vulnerability Detection in Dependencies
## 🎯 Objective

Demonstrate how Software Composition Analysis (SCA) helps detect security vulnerabilities in third-party dependencies using pip-audit in a Python project.

SCA scans:
- Direct dependencies
- Transitive (indirect) dependencies
- Known vulnerabilities
- CVE references
- Recommended fixed versions

🔍 What is SCA?

Software Composition Analysis (SCA) identifies security vulnerabilities in:
- Open-source libraries
- Third-party packages
- Transitive dependencies
- Package versions

Modern applications rely heavily on external libraries.
A vulnerability in one indirect dependency can compromise the entire application.

SCA tools analyze:
- Dependency trees
- Public vulnerability databases (NVD, PyPI Advisory DB)
- CVE identifiers
- Recommended remediations

⚠ Why SCA is Important

Without SCA:
- Developers may unknowingly use vulnerable packages
- Transitive dependencies may introduce critical CVEs
- Supply-chain attacks go undetected
- Compliance requirements may fail

With SCA:
- Known vulnerabilities are detected early
- CVE IDs are provided
- Safe version upgrades are recommended
- DevSecOps pipelines can fail builds automatically

🧪 Practical Demo Using pip-audit

We will:
- Create a virtual environment
- Install pip-audit
- Scan requirements.txt
- Review vulnerabilities

🚀 Step 1 — Create Virtual Environment
```bash
python -m venv .venv
```
Activate environment (Windows Git Bash):
```bash
source .venv/Scripts/activate
```

📦 Step 2 — Install pip-audit
```bash
pip-audit -r requirements.txt
```

This command:
- Scans direct dependencies
- Scans transitive dependencies
- Queries vulnerability databases
- Identifies vulnerable versions
- Displays CVE numbers
- Suggests fixed versions

📊 Example Output

Package     Version  ID                  Fix Versions
----------  -------  -------------------  -------------
urllib3     1.25.8   PYSEC-2021-123      1.26.5
requests    2.19.1   CVE-2018-18074      2.20.0

🧠 What This Means
| Field        | Explanation                               |
| ------------ | ----------------------------------------- |
| Package      | Vulnerable dependency                     |
| Version      | Installed version                         |
| ID           | Vulnerability reference (CVE or advisory) |
| Fix Versions | Secure version to upgrade                 |

🔐 What Developers Must Do
- When vulnerability is found:
- Check severity (Critical/High/Medium)
- Review CVE description
- Upgrade to safe version
- Test application
- Commit version bump

🧬 How SCA Detects Indirect Dependencies

Example:
Your App
 └── requests
       └── urllib3
Even if you don’t directly install urllib3,
SCA scans it because it’s part of the dependency tree.

This is critical for supply-chain security.

📌 Sample Vulnerability Explanation

Refer to vulnerability databases like:
- NVD (National Vulnerability Database)
- PyPI Advisory Database
- GitHub Security Advisories

Each CVE includes:
- Description
- Impact
- Affected versions
- Severity score (CVSS)
- Remediation guidance

Developers must assess business impact before patching.

🔄 CI/CD Integration (DevSecOps)

You can integrate SCA into pipelines:
pip-audit -r requirements.txt --strict

If vulnerabilities are found:
- Pipeline fails
- Report is generated
- Security team notified

🏗 SCA in DevSecOps Lifecycle

Code → Build → SCA Scan → Deploy

SCA ensures:
- Secure dependency management
- Supply-chain protection
- Early vulnerability detection
- Continuous monitoring

🆚 SCA vs SAST vs DAST

| Security Type | What It Scans            |
| ------------- | ------------------------ |
| SAST          | Source code              |
| DAST          | Running application      |
| SCA           | Third-party dependencies |

SCA focuses on supply-chain risk.

🏆 Key Takeaways
- Modern apps rely heavily on open-source packages
- Vulnerabilities can exist in indirect dependencies
- SCA identifies known CVEs
- Developers must upgrade to secure versions
- pip-audit is lightweight and effective
- SCA is critical for DevSecOps maturity

Refer the below link as sample of vulnerability explained with reasons which the developers will need to take care of this.

https://nvd.nist.gov/vuln/detail/CVE-2024-50181
