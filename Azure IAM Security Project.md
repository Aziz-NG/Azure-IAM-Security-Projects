# 🔐 Azure IAM Security Project

> Hands-on implementation of enterprise-grade Identity & Access Management (IAM) controls in Microsoft Azure, aligned with NIST, ISO 27001, and SOC 2.

![Azure](https://img.shields.io/badge/Cloud-Microsoft%20Azure-blue)
![Security](https://img.shields.io/badge/Focus-IAM%20%7C%20Zero%20Trust-green)
![Frameworks](https://img.shields.io/badge/Compliance-NIST%20%7C%20ISO%2027001%20%7C%20SOC2-orange)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

---

## 📌 Probelm Summary

Organizations operating in cloud environments frequently struggle with **over-permissioned accounts, weak authentication controls, and lack of visibility into user activity**. These gaps increase the risk of **credential compromise, privilege escalation, and unauthorized resource deployment**—all common entry points for modern attacks.

In many environments, privileged roles are assigned permanently, MFA is inconsistently enforced, and security policies are reactive rather than preventative. This project addresses those risks by implementing a **Zero Trust-based Identity and Access Management (IAM) model in Azure**, designed to meet both operational and compliance requirements.

---

## 🎯 Objectives

* Enforce **least privilege access** using Role-Based Access Control (RBAC)
* Eliminate standing privileged access with **Privileged Identity Management (PIM)**
* Strengthen authentication through **Multi-Factor Authentication (MFA)**
* Prevent insecure configurations using Azure Policy
* Enable **centralized logging and monitoring** for audit readiness
* Map controls to **NIST, ISO 27001, SOC 2**

---

## 🏗️ Architecture Overview

This environment integrates core Azure security services to enforce identity governance:

* **Microsoft Entra ID** — centralized identity and group management
* **Azure RBAC** — fine-grained access control at the subscription level
* Conditional Access policies — MFA enforcement and access conditions
* **Azure Policy** — proactive compliance enforcement
* **Azure Monitor & Log Analytics** — logging, auditing, and detection

---

## 👥 Identity & Access Management (RBAC)

### 🔹 Security Groups

* `Security-Admins`
* `App-Owners`
* `Readers`

### 🔹 Role Assignments

| Group              | Role           | Scope        |
| ------------------ | -------------- | ------------ |
| Security-Admins    | Security Admin | Subscription |
| App-Owners         | Contributor    | Subscription |
| Readers            | Reader         | Subscription |

### 🔐 Security Principle

> Access is strictly governed by the **Principle of Least Privilege**, ensuring users receive only the permissions necessary to perform their roles.

<img width="1545" height="402" alt="RBAC Role assignments" src="https://github.com/user-attachments/assets/66704f06-1d5a-4bd2-b167-35b4b10786aa" />


---

## ⏱️ Privileged Identity Management (PIM)

* Security Admin role set as **eligible (not permanent)**
* Activation requires:

  * MFA
  * Justification
  * Time-bound access

### 🛡️ Security Benefit

Minimizes exposure by removing **standing privileged access**, a common vector in lateral movement attacks.

<img width="1786" height="318" alt="PIM eligible roles" src="https://github.com/user-attachments/assets/bcf588c4-2037-4605-b926-da1cde329ebb" />


<img width="1893" height="954" alt="PIM Activation" src="https://github.com/user-attachments/assets/833c602b-25ba-4c26-b6bf-4087f3bad2db" />

---

## 🔐 Conditional Access & MFA

* MFA applied to **all users**
* Global admin excluded (break-glass account)

### 🛡️ Security Benefit

Mitigates risks associated with **credential theft and phishing attacks**, aligning with Zero Trust principles.

<img width="1371" height="807" alt="MFA Enforcement" src="https://github.com/user-attachments/assets/31b77aa6-1795-4a53-ba1d-ae9a10f2caa0" />

---

## 🚫 Azure Policy Enforcement

### 🔒 Policy Implemented

* Deny storage accounts with **public network access enabled**

### 🧪 Validation

* Attempted non-compliant deployment
* ❌ Deployment **blocked by policy**

### 🛡️ Security Benefit

Shift security **left**, preventing insecure resources from being deployed.

<img width="1899" height="494" alt="Azure Policy Enforcement" src="https://github.com/user-attachments/assets/7eccbefb-be1d-4ddf-8d2b-68308c876581" />

---

## 📊 Logging & Monitoring

Enabled:

* Sign-in logs
* Audit logs
* Log Analytics Workspace integration

### 🧪 Sample Query

```kusto
SigninLogs
| limit 10
```

### 🛡️ Security Benefit

Provides:

* Full traceability of user actions
* Threat detection capability
* Audit-ready evidence collection

<img width="1594" height="645" alt="Log Analytics query results" src="https://github.com/user-attachments/assets/cf0c117e-beab-44fb-b512-30253ef41d24" />

---

## 📋 RBAC Audit Summary

| Identity           | Role           | Scope        | Justification                |
| ------------------ | -------------- | ------------ | ---------------------------- |
|    Security-Admins | Security Admin | Subscription | Managed via PIM (JIT access) |
|    App-Owners      | Contributor    | Subscription | Application deployment       |
|    Readers         | Reader         | Subscription | Read-only access             |

---

## 🧩 Compliance Mapping

| Framework | Control | Requirement               | Implementation           |
| --------- | ------- | ------------------------- | ------------------------ |
| NIST CSF  | PR.AC-1 | Identity management       | Entra ID users & groups  |
| NIST CSF  | PR.AC-4 | Least privilege           | RBAC assignments         |
| NIST CSF  | PR.AC-6 | Privileged access control | PIM eligible roles       |
| NIST CSF  | PR.IP-1 | Secure configuration      | Azure Policy enforcement |
| ISO 27001 | A.9.4   | Access control            | Conditional Access + MFA |
| SOC 2     | CC6.1   | Logical access security   | MFA enforcement          |
| SOC 2     | CC6.2   | Privilege restriction     | RBAC + PIM               |

---

## 🧠 Key Security Outcomes

* ✅ Enforced **least privilege access model**
* ✅ Eliminated standing privileged roles (**PIM**)
* ✅ Strengthened identity security with **MFA enforcement**
* ✅ Prevented insecure deployments through **Azure Policy**
* ✅ Achieved **end-to-end audit visibility**

---

## 🚀 Key Takeaways

This project demonstrates how to design and implement **enterprise-grade IAM controls in Azure** using a Zero Trust approach. It reflects real-world practices used by security teams to:

* Reduce attack surface
* Improve identity governance
* Meet compliance requirements
* Enhance detection and response capabilities

---
