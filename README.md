# 🔐 Node.js Secure CI/CD Pipeline with AWS

## 📌 Project Overview
This project demonstrates how to build a **secure CI/CD pipeline** for a Node.js application using **AWS CodePipeline** and **AWS 
CodeBuild**.  
It integrates **DevSecOps practices** by running automated **security scans** at multiple stages of the pipeline.

The pipeline ensures:
- Secure build and deployment of Node.js code.
- Automated detection of vulnerabilities before releasing code.
- Continuous integration of **SCA, SAST, and DAST** tools.

---

## ⚙️ Pipeline Stages

1. **Source (GitHub → CodePipeline)**  
   - The pipeline is triggered when code is pushed to the GitHub repository.

2. **Build (CodeBuild)**  
   - Installs dependencies (`npm ci`).  
   - Runs application tests (`npm test`).  
   - Executes **security scans**:
     - **SCA (Software Composition Analysis)** → *Snyk*  
     - **SAST (Static Application Security Testing)** → *Semgrep*  
   - Generates security reports (`semgrep.sarif`).  

3. **Deploy (CodePipeline → S3/EC2/Elastic Beanstalk)**  
   - Builds an artifact (zip file).  
   - Deploys the application to the configured environment.  

4. **DAST (Dynamic Application Security Testing)**  
   - Runs **OWASP ZAP** to scan the deployed application.  
   - Detects runtime vulnerabilities like XSS, SQL Injection, etc.  

---

## 🏗️ Tech Stack

- **AWS CodePipeline** – Orchestrates the CI/CD flow.  
- **AWS CodeBuild** – Builds and runs security scans.  
- **Node.js 18** – Application runtime.  
- **Snyk** – Scans for vulnerable dependencies (SCA).  
- **Semgrep** – Analyzes source code for security flaws (SAST).  
- **OWASP ZAP** – Performs penetration testing on live app (DAST).  
- **Amazon S3** – Stores build artifacts and reports.  

---

