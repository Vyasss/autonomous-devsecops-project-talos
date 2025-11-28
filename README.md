# 🛡️ Sentinel: Autonomous DevSecOps Agent

**Sentinel** is an intelligent, self-healing infrastructure agent designed to audit code commits in real-time. It acts as a "Gatekeeper" for software repositories, automatically detecting security vulnerabilities, logic errors, and missing dependencies before they reach production.

![Architecture Diagram](architecture_diagram.png)

## 🚀 How It Works

This system leverages **Event-Driven Architecture** using **n8n** and **Google Gemini 1.5 Pro**.

1.  **👂 Listen:** A Webhook listener triggers instantly when code is pushed to GitHub.
2.  **🔍 Filter:** Conditional logic isolates relevant files (e.g., Python scripts), ignoring documentation/noise.
3.  **🧠 Audit:** An Autonomous AI Agent (Gemini) retrieves the raw code using the GitHub API.
    * It performs a **Syntax Check** (acting as an Interpreter).
    * It performs a **Security Audit** (OWASP Top 10).
    * It performs a **Dependency Check** (scanning for missing `requirements.txt`).
4.  **📢 Report:** The Agent compiles a structured report and emails the lead developer.
5.  **🛠️ Remediation:** If vulnerabilities or missing files are found, the Agent **auto-generates the fix** code.

## 🛠️ Tech Stack

* **Orchestration:** n8n (Self-Hosted on Docker/VPS)
* **Cognitive Engine:** Google Gemini 1.5 Flash
* **Vector Memory:** Pinecone (for RAG context)
* **Integration:** GitHub API, Gmail OAuth2

## ⚡ Key Features

* **Precision Targeting:** Uses `commit_sha` to audit the *exact* version of the code pushed, bypassing API caching.
* **Multi-Modal Analysis:** Audits Logic, Security, and Infrastructure simultaneously.
* **Self-Correction:** Automatically detects missing dependencies based on `import` statements and generates the required config files.

## 📥 Installation (Import Workflow)

1.  Install n8n (Docker or Cloud).
2.  Download `sentinel-agent-workflow.json` from this repo.
3.  Import into n8n.
4.  Configure Credentials (GitHub, Google Gemini, Gmail).
5.  Set the Webhook URL in your target GitHub repository.

---
*Created by [Your Name]*
