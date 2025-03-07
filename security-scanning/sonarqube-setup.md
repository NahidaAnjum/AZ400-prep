
---

### **4️⃣ `security-scanning/sonarqube-setup.md` (SonarQube in Azure Pipelines)**
```md
# 🛡️ Setting Up SonarQube in Azure DevOps  

SonarQube helps in **static code analysis** and improving code quality.

## 🔹 Steps to Integrate SonarQube in Azure Pipelines
1️⃣ **Install the SonarQube extension** in Azure DevOps.  
2️⃣ **Create a SonarQube Service Connection** in Azure DevOps.  
3️⃣ **Modify your `azure-pipelines.yml` file**:

```yaml
- task: SonarQubePrepare@4
  inputs:
    SonarQube: 'SonarQubeServiceConnection'
    scannerMode: 'CLI'
    configMode: 'manual'
    projectKey: 'your_project_key'
