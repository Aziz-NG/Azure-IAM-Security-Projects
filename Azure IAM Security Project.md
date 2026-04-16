# 🔐 Azure IAM Security Project

> Hands-on implementation of enterprise-grade Identity & Access Management (IAM) controls in Microsoft Azure, aligned with NIST, ISO 27001, and SOC 2.

![Azure](https://img.shields.io/badge/Cloud-Microsoft%20Azure-blue)
![Security](https://img.shields.io/badge/Focus-IAM%20%7C%20Zero%20Trust-green)
![Frameworks](https://img.shields.io/badge/Compliance-NIST%20%7C%20ISO%2027001%20%7C%20SOC2-orange)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

---

## 📌 Executive Summary

This project demonstrates the implementation of **Identity and Access Management (IAM)** controls in Azure using a **Zero Trust security model**.

The project enforces:

* Least privilege access
* Strong authentication (MFA)
* Just-in-time privileged access
* Secure configuration policies
* Full audit logging

All controls are mapped to **industry-standard compliance frameworks**, making this project audit-ready.

---

## 🎯 Objectives

* Implement **Role-Based Access Control (RBAC)**
* Configure **Privileged Identity Management (PIM)**
* Enforce **Multi-Factor Authentication (MFA)**
* Deploy **Azure Policy** for security baselines
* Enable **logging and monitoring**
* Map controls to **NIST, ISO 27001, SOC 2**

---

## 🏗️ Architecture Overview

This environment includes:

* Microsoft Entra ID (users & groups)
* Azure RBAC (subscription-level access control)
* Conditional Access policies (MFA enforcement)
* Azure Policy (deny insecure configurations)
* Azure Monitor + Log Analytics (audit logging)

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

> All access follows the **Principle of Least Privilege**, ensuring users only receive required permissions.

<img width="1545" height="402" alt="RBAC Role assignments" src="https://github.com/user-attachments/assets/94a1c790-cb3a-413e-bb26-aa0973597d7e" />

---

## ⏱️ Privileged Identity Management (PIM)

* Security Admin role set as **eligible (not permanent)**
* Activation requires:

  * MFA
  * Justification
  * Time-bound access

### 🛡️ Security Benefit

Reduces risk of **standing privileged access** and limits attack surface.

<img width="1786" height="318" alt="PIM eligible roles" src="https://github.com/user-attachments/assets/bcf588c4-2037-4605-b926-da1cde329ebb" />


<img width="1893" height="954" alt="PIM Activation" src="https://github.com/user-attachments/assets/833c602b-25ba-4c26-b6bf-4087f3bad2db" />

---

## 🔐 Conditional Access & MFA

* Policy applied to **all users**
* Enforces **Multi-Factor Authentication (MFA)**
* Global admin excluded (break-glass account)

### 🛡️ Security Benefit

Protects against **credential compromise and unauthorized access**.

<img width="1371" height="807" alt="MFA Enforcement" src="https://github.com/user-attachments/assets/31b77aa6-1795-4a53-ba1d-ae9a10f2caa0" />

---

## 🚫 Azure Policy Enforcement

### 🔒 Policy Implemented

* Deny storage accounts with **public network access enabled**

### 🧪 Validation

* Attempted non-compliant deployment
* ❌ Deployment **blocked by policy**

### 🛡️ Security Benefit

Prevents insecure resources from being deployed.

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

* Traceability
* Threat detection capability
* Audit readiness

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

* ✅ Enforced **least privilege access**
* ✅ Eliminated standing privileged roles (**PIM**)
* ✅ Strengthened authentication (**MFA**)
* ✅ Prevented insecure deployments (**Azure Policy**)
* ✅ Achieved full **audit visibility**

---

## 🚀 Key Takeaways

This project demonstrates how to implement **real-world cloud IAM security controls** using Azure.

It reflects practices used in:

* Enterprise cloud environments
* Security operations teams
* Compliance-driven organizations

---
