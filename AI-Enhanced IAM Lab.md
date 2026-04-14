# 🧠 AI-Enhanced Identity & Access Management Lab (Azure)

## 📌 Executive Summary

This project is an AI-enhanced version of the previous lab. It demonstrates the implementation of an **AI-enhanced Identity and Access Management (IAM) architecture** using Microsoft Entra ID and Azure security services.

The lab focuses on combining traditional IAM controls with **AI-driven risk detection, adaptive access policies, and behavioral analytics**.

---

## 🎯 Objectives

* Implement secure identity management using Entra ID
* Configure **AI-based risk detection** with Identity Protection
* Enforce **adaptive access control** using Conditional Access
* Apply **AI-assisted governance** via Access Reviews
* Simulate **security events and anomalies**
* Analyze logs using **behavioral detection queries**
* Improve posture using **Microsoft Defender for Cloud**

---

## 🧱 Architecture Components

* **Microsoft Entra ID**
* **Identity Protection (AI Risk Engine)**
* **Conditional Access (Adaptive MFA)**
* **Access Reviews (AI Decision Helpers)**
* **Log Analytics Workspace**
* **Microsoft Defender for Cloud**
* **Azure Policy**

---

## 🔐 Key Implementations

### 1. AI-Based Risk Detection

* Enabled **User Risk Policy**
* Enabled **Sign-in Risk Policy**
* Enforced MFA for medium/high risk users
* Blocked high-risk sign-ins

<img width="1511" height="187" alt="Identity Protection policies" src="https://github.com/user-attachments/assets/478add8d-67cf-4319-b7ee-9474960e0f7e" />

---

### 2. Role-Based Access Control (RBAC)

#### Users

* sec-admin
* app-owner
* reader-user

#### Groups

* SG-Security-Admins
* SG-App-Owners
* SG-Readers

#### Principle

* Least privilege access enforced

---

### 3. Privileged Identity Management (PIM)

* Role Strategy: Assigned Eligible status to sec-admin for high-privilege roles.

* Zero Standing Access: Enforced Just-In-Time (JIT) activation, requiring MFA and business justification for role elevation.

  <img width="1833" height="320" alt="PIM" src="https://github.com/user-attachments/assets/8db00373-d64d-4903-bddf-f452b077266b" />

---

### 4. 🧠 AI-Powered Access Reviews

Instead of relying on reactive alerts, this lab uses **AI-assisted access governance**.

#### Configuration

* Scope: Security Administrator
* Enabled **Decision Helpers**
* Rule: *No sign-in within 30 days*

<img width="628" height="640" alt="AI Powered Access Reviews 1" src="https://github.com/user-attachments/assets/32f1646e-d6af-402d-82c7-712a264a32f0" />

<img width="1835" height="434" alt="Access review" src="https://github.com/user-attachments/assets/f9e46e83-ac69-428f-8c15-19ae679a7810" />

#### AI Behavior

* Detects inactive privileged users
* Recommends access removal

> Example: *“User is inactive; AI recommends Deny.”*

---

### 5. 🔐 Adaptive Conditional Access

Policy Logic: Created a risk-based Conditional Access (CA) policy.

Enforcement: Access is granted to standard users, but an **MFA Challenge** is automatically triggered if the AI risk level is Medium or High.

<img width="1657" height="168" alt="Adaptive CAP" src="https://github.com/user-attachments/assets/c0af83c5-e261-45e4-8879-938a6476d958" />

---

### 6. 📊 AI-Powered Logging & Detection

Logs were sent to **Log Analytics** and analyzed using KQL.

#### Sample Queries

**Unusual Location Detection**

```kusto
SigninLogs
| summarize Locations = make_set(Location) by UserPrincipalName
```

<img width="1587" height="429" alt="Unusual Location detection" src="https://github.com/user-attachments/assets/ff44da39-6668-407b-8056-076c9278be3c" />

**Failed Login Detection**

```kusto
SigninLogs
| where ResultType != 0
| summarize FailedAttempts = count() by UserPrincipalName
| order by FailedAttempts desc
```

<img width="1633" height="446" alt="Login Detection" src="https://github.com/user-attachments/assets/1c086c2c-8e22-4b53-b240-22d35d428ea1" />

---

## 🛡️ Security Posture & AI Insights

**Microsoft Defender for Cloud**

* Used foundational CSPM capabilities
* Reviewed Secure Score
* Simulated misconfiguration:
   * Created a storage account with public access enabled
     
### Key Observation

<img width="1732" height="484" alt="image" src="https://github.com/user-attachments/assets/e494be83-c79a-4f82-9ec0-574ae7e8b3e4" />

As of testing, Defender did not immediately flag the issue. This highlights a critical security principle:

**Prevention > Detection**

* **Detection latency** can take hours (up to ~24h)
* ### Azure Policy enforcement is immediate

➡️ Conclusion: Use **“Deny” policy** for high-risk configurations whenever possible

---

### Assigned Azure Policy 

* Denied public access configurations
* Audited secure resource settings

---

## 📊 Compliance Mapping

| Framework | Control        | Implementation         | AI Enhancement       |
| --------- | -------------- | ---------------------- | -------------------- |
| NIST      | PR.AC-1        | Identity management    | Risk detection       |
| NIST      | PR.AC-6        | Access control         | AI access reviews    |
| ISO 27001 | A.9.4          | Access restrictions    | Adaptive MFA         |
| SOC 2     | CC6            | Monitoring             | Behavioral analytics |
| Loi 25    | Access control | Risk-based enforcement |                      |

---

## 🧠 Key Takeaways

* IAM is enhanced using **AI-driven decision making**
* Security is improved with **adaptive and contextual controls**
* Behavioral analysis is critical for detecting anomalies
* Governance evolves from **manual review → AI-assisted decisions**

---
### 🚀 Summary

This lab demonstrates how modern IAM can be transformed using AI to deliver:

* Smarter access decisions
* Reduced attack surface
* Automated governance
* Faster threat detection

A practical foundation for building **intelligent, adaptive cloud security architectures.**
