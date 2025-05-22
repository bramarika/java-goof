
# 📌 java-snyk-gating-demo

This project demonstrates how to integrate [Snyk](https://snyk.io/) with GitHub Actions to automatically scan a vulnerable Java application and **fail builds or pull requests** if **high or critical vulnerabilities** are detected.

It showcases **DevSecOps best practices** by shifting security left in the CI/CD pipeline.

---

## 🛠️ Project Features

- 🔧 CI pipeline with GitHub Actions
- 🔍 Scans for vulnerabilities using [Snyk CLI](https://docs.snyk.io/snyk-cli)
- 📄 JSON output parsed with `jq`
- ❌ Conditional gating: build fails on high/critical vulns
- ⚠️ Medium vulns shown, but don’t fail the build

---

## 🧰 Tech Stack

- Java 17 (Temurin)
- Maven
- GitHub Actions
- Snyk CLI
- jq (lightweight JSON processor)

---

## 🚦 How It Works

1. CI pipeline triggers on push or PR to `main`.
2. Snyk scans all Maven projects (`--all-projects`).
3. Outputs vulnerabilities to `snyk-report.json`.
4. A script uses `jq` to:
   - Count medium, high, and critical issues
   - Fail the build if **any high/critical** issues are found

### ✅ Example Output

\`\`\`
🟠 Medium Vulnerabilities: 2
🔴 High/Critical Vulnerabilities: 1
::error ::Found 1 High or Critical vulnerabilities. Failing the build.
\`\`\`

---

## 📁 Project Structure

\`\`\`
.
├── .github/workflows/security-pipeline.yml   # GitHub Actions workflow
├── todolist-goof/                            # Vulnerable Java modules
├── log4shell-goof/
├── pom.xml                                   # Root Maven project file
└── snyk-report.json                          # Output file after Snyk scan
\`\`\`

---

## 🚀 Getting Started

### 1. Fork the repo

### 2. Add your Snyk token

Go to **GitHub → Settings → Secrets and variables → Actions**  
Add a new secret:

\`\`\`
Name: SNYK_TOKEN
Value: <your-snyk-token>
\`\`\`

You can get this token from your Snyk account: https://app.snyk.io/account

### 3. Trigger a scan

- Commit and push a change to \`main\`, or
- Open a pull request targeting \`main\`

Check the **Actions tab** for results.

---

## ✍️ Rename the Repository

You can rename your GitHub repo:

1. Click the **Settings** tab of your repo.
2. Under **Repository name**, rename to:

   \`\`\`
   java-snyk-gating-demo
   \`\`\`

3. Click **Rename** to confirm.

---

## 💬 Why Use This?

- ✅ Block insecure builds early
- 🛡️ Practice real-world DevSecOps
- 🔁 Easily extendable to other languages/tools
- 🧠 Learn how to parse and gate on real SCA results

---

## 📎 Resources

- [Snyk CLI Docs](https://docs.snyk.io/snyk-cli)
- [GitHub Actions Docs](https://docs.github.com/en/actions)
- [jq Manual](https://stedolan.github.io/jq/manual/)

---

