📌 java-snyk-gating-demo
This project demonstrates how to integrate Snyk with GitHub Actions to automatically scan a vulnerable Java application and fail pull requests or builds when high or critical vulnerabilities are detected. It showcases shift-left security by enforcing security early in the CI/CD pipeline.
🛠️ What This Project Includes
Forked from Snyk Labs Java Goof

GitHub Actions workflow defined in .github/workflows/security-pipeline.yml

Automated Snyk scan with JSON output

Gating logic using jq to:

Show medium vulnerabilities

Fail build/PR if high or critical vulnerabilities exist

⚙️ Tools & Technologies
Java 17 (Temurin)

Maven

GitHub Actions

Snyk CLI

jq (command-line JSON parser)

🚀 How It Works
The workflow triggers on push or pull_request to the main branch.

Code is scanned using Snyk CLI across all Maven projects.

Results are exported as JSON.

jq parses the report:

If any high/critical vulns → build fails.

Otherwise → build passes.
Sample output:
🟠 Medium Vulnerabilities: 3
🔴 High/Critical Vulnerabilities: 1
::error ::Found 1 High or Critical vulnerabilities. Failing the build.

Folder Structure:
.
├── .github/
│   └── workflows/
│       └── security-pipeline.yml  # GitHub Actions pipeline
├── todolist-goof/                 # Vulnerable Java modules
├── log4shell-goof/               # Another vulnerable module
├── pom.xml
└── snyk-report.json              # Snyk scan output

🧑‍💻 How to Reproduce Locally
Fork this repo.

Add your Snyk Token to your GitHub repo secrets as SNYK_TOKEN.

Push a change or raise a PR to trigger the scan.

View logs in GitHub Actions.

Medium vulnerabilities are shown in logs for awareness.
