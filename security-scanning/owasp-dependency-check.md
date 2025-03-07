# 🔍 OWASP Dependency Check in Azure DevOps  

OWASP Dependency Check is a tool that **scans dependencies for known vulnerabilities** using the National Vulnerability Database (NVD). This helps in securing applications by identifying risks early in the development cycle.

## 📌 Why Use OWASP Dependency Check?  
✅ Detects **vulnerable third-party libraries**.  
✅ Supports **multiple programming languages** (Java, .NET, Python, etc.).  
✅ Integrates with **Azure DevOps Pipelines & GitHub Actions**.  
✅ Helps in **compliance with security best practices**.  

---

## 🚀 **How to Integrate OWASP Dependency Check in Azure Pipelines?**  

### **1️⃣ Install OWASP Dependency Check in Your Pipeline**  
Modify your **`azure-pipelines.yml`** file to install and run Dependency Check.

```yaml
trigger:
  branches:
    include:
      - main

pool:
  vmImage: 'ubuntu-latest'

steps:
  - task: Bash@3
    displayName: "Install OWASP Dependency Check"
    inputs:
      targetType: inline
      script: |
        sudo apt update
        sudo apt install dependency-check -y
        dependency-check --version

  - task: Bash@3
    displayName: "Run Dependency Check Scan"
    inputs:
      targetType: inline
      script: |
        dependency-check --project "MyProject" --scan $(Build.SourcesDirectory) --format HTML --out $(Build.ArtifactStagingDirectory)/dependency-check-report

  - task: PublishBuildArtifacts@1
    displayName: "Publish Dependency Check Report"
    inputs:
      pathToPublish: $(Build.ArtifactStagingDirectory)/dependency-check-report
      artifactName: SecurityReports
