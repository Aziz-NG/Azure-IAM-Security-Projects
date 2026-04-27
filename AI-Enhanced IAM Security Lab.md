# 🤖 AI-Enhanced Identity & Access Management Project
## Adaptive Identity & Access Management with Zero Trust + AI

## 📌 Executive Summary

This project is an AI-enhanced version of the previous one. It extends a traditional Azure IAM implementation by integrating **AI-driven security capabilities** to create an **adaptive, risk-aware identity architecture**.

Built on **Microsoft Entra ID** and Azure security services, the solution combines **Zero Trust principles** with **behavioral analytics, risk-based access control, and automated governance** to improve decision-making and reduce identity-based threats.

---

## 🎯 Objectives

* Implement **secure identity governance** using Microsoft Entra ID
* Enable **AI-driven risk detection** with Identity Protection
* Enforce **adaptive access control** using Conditional Access
* Automate governance using **AI-assisted Access Reviews**
* Simulate and analyze **security anomalies**
* Leverage **behavioral analytics** through Log Analytics (KQL)
* Strengthen posture with **Microsoft Defender for Cloud**
---

## 🧱 Architecture Components

* **Microsoft Entra ID** — Identity and access management
* **Identity Protection (AI Risk Engine)** — Risk-based detections
* **Conditional Access** — Adaptive MFA enforcement
* **Access Reviews** — AI Decision Helpers
* **Azure Policy** — Preventative security controls
* **Log Analytics Workspace** — Centralized logging & analysis
* **Microsoft Defender for Cloud** — Security posture management

---

## 🔐 Key Implementations

### 🧠 AI-Based Risk Detection

* Enabled **User Risk Policy** and **Sign-in Risk Policy**
* Enforced MFA for **medium/high risk users**
* Blocked **high-risk sign-ins**

### 🛡️ Impact:
Introduces **real-time, AI-driven identity protection**, reducing reliance on static controls.

<img width="1511" height="187" alt="Identity Protection policies" src="https://github.com/user-attachments/assets/478add8d-67cf-4319-b7ee-9474960e0f7e" />

---

### 👥 Role-Based Access Control (RBAC)

#### Defined users and groups:

* sec-admin > Security-Admins
* app-owner > App-Owners
* reader-user > Readers

> Enforced **least privilege access model**

### 🛡️ Impact:
Limits unnecessary permissions and reduces **lateral movement risk**.

---

### ⏱️ Privileged Identity Management (PIM)

* High-privilege roles configured as **eligible (JIT access)**

* Zero Standing Access: Enforced Just-In-Time (JIT) activation, requiring MFA and business justification for role elevation.

### 🛡️ Impact:
Eliminates **standing privileged access**, aligning with Zero Trust architecture.

  <img width="1833" height="320" alt="PIM" src="https://github.com/user-attachments/assets/8db00373-d64d-4903-bddf-f452b077266b" />

---

### 🧠 AI-Powered Access Reviews

* Scope: Privileged roles (e.g., Security Administrator)
* Enabled AI decision helpers
* Rule: Flag users inactive for 30+ days

<img width="628" height="640" alt="AI Powered Access Reviews 1" src="https://github.com/user-attachments/assets/32f1646e-d6af-402d-82c7-712a264a32f0" />

<img width="1835" height="434" alt="Access review" src="https://github.com/user-attachments/assets/f9e46e83-ac69-428f-8c15-19ae679a7810" />

#### AI Behavior

* Detects inactive privileged users
* Recommends access removal

> Example: *“User is inactive; AI recommends Deny.”*

### 🛡️ Impact:
Shifts gouvernance from **manual reviews → intelligent, automated decision support.**

---

### 🔐 Adaptive Conditional Access

* Implemented a **risk-based Conditional Access (CA) policy.**
* Access is granted to standard users, but an **MFA Challenge** is automatically triggered if the AI risk level is Medium or High.

<img width="1657" height="168" alt="Adaptive CAP" src="https://github.com/user-attachments/assets/c0af83c5-e261-45e4-8879-938a6476d958" />

---

### 📊 AI-Powered Logging & Detection

Logs centralized in **Log Analytics** and analyzed using KQL.

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


### 🛡️ Impact:
Enables **behavioral anomaly detection** and supports proactive threat hunting.

---

## 🛡️ Security Posture & AI Insights

**Microsoft Defender for Cloud**

* Used foundational CSPM capabilities
* Reviewed Secure Score
* Simulated misconfiguration:
   * Created a storage account with public access enabled
     
### Key Observation

<img width="1732" height="484" alt="image" src="https://github.com/user-attachments/assets/e494be83-c79a-4f82-9ec0-574ae7e8b3e4" />



As of testing, Defender did not immediately flag the issue. Detection latency can take hours (up to ~24h). 

This highlights a critical security principle:
**Prevention controls (Azure Policy) are more effective than reactive detection**


  <img width="1893" height="368" alt="image" src="https://github.com/user-attachments/assets/4ba484ba-ad78-472f-b8a1-860609b4f61e" />
  


➡️ Conclusion: 
* Use **“Deny” policy** for high-risk configurations
* Enforced **secure-by-default deployments**

---

## 📊 Compliance Mapping

| Framework | Control        | Implementation         | AI Enhancement       |
| --------- | -------------- | ---------------------- | -------------------- |
| NIST      | PR.AC-1        | Identity management    | Risk detection       |
| NIST      | PR.AC-6        | Access control         | AI access reviews    |
| ISO 27001 | A.9.4          | Access restrictions    | Adaptive MFA         |
| SOC 2     | CC6            | Monitoring             | Behavioral analytics |
| Law 25    | Access control | Risk-based enforcement | Context-aware decisions |

---

## 🚀 Key Takeaways

* IAM is enhanced using **AI-driven decision making**
* Security is improved with **adaptive and contextual controls**
* Behavioral analysis is critical for detecting anomalies
* Governance evolves from **manual review → AI-assisted decisions**

---
### 🚀 Summary

The project demonstrates how modern IAM can be transformed using AI to deliver:

* Smarter access decisions
* Reduced attack surface
* Automated governance
* Faster threat detection

A practical foundation for building **intelligent, adaptive cloud security architectures.**
