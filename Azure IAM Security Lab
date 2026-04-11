# 🔐 Azure IAM Security Lab

> Hands-on implementation of enterprise-grade Identity & Access Management (IAM) controls in Microsoft Azure, aligned with NIST, ISO 27001, and SOC 2.

![Azure](https://img.shields.io/badge/Cloud-Microsoft%20Azure-blue)
![Security](https://img.shields.io/badge/Focus-IAM%20%7C%20Zero%20Trust-green)
![Frameworks](https://img.shields.io/badge/Compliance-NIST%20%7C%20ISO%2027001%20%7C%20SOC2-orange)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

---

## 📌 Executive Summary

This project demonstrates the implementation of **Identity and Access Management (IAM)** controls in Azure using a **Zero Trust security model**.

The lab enforces:

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

* `SG-Security-Admins`
* `SG-App-Owners`
* `SG-Readers`

### 🔹 Role Assignments

| Group              | Role           | Scope        |
| ------------------ | -------------- | ------------ |
| SG-Security-Admins | Security Admin | Subscription |
| SG-App-Owners      | Contributor    | Subscription |
| SG-Readers         | Reader         | Subscription |

### 🔐 Security Principle

> All access follows the **Principle of Least Privilege**, ensuring users only receive required permissions.

---

## ⏱️ Privileged Identity Management (PIM)

* Security Admin role set as **eligible (not permanent)**
* Activation requires:

  * MFA
  * Justification
  * Time-bound access

### 🛡️ Security Benefit

Reduces risk of **standing privileged access** and limits attack surface.

📸 [View Screenshot](./screenshots/pim-activation.png)

---

## 🔐 Conditional Access & MFA

* Policy applied to **all users**
* Enforces **Multi-Factor Authentication (MFA)**
* Global admin excluded (break-glass account)

### 🛡️ Security Benefit

Protects against **credential compromise and unauthorized access**.

📸 [View Screenshot](./screenshots/conditional-access.png)

---

## 🚫 Azure Policy Enforcement

### 🔒 Policy Implemented

* Deny storage accounts with **public network access enabled**

### 🧪 Validation

* Attempted non-compliant deployment
* ❌ Deployment **blocked by policy**

### 🛡️ Security Benefit

Prevents insecure resources from being deployed.

📸 [View Screenshot](./screenshots/policy-deny.png)

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

📸 [View Screenshot](./screenshots/logs-query.png)

---

## 📋 RBAC Audit Summary

| Identity           | Role           | Scope        | Justification                |
| ------------------ | -------------- | ------------ | ---------------------------- |
| SG-Security-Admins | Security Admin | Subscription | Managed via PIM (JIT access) |
| SG-App-Owners      | Contributor    | Subscription | Application deployment       |
| SG-Readers         | Reader         | Subscription | Read-only access             |

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

This lab demonstrates how to implement **real-world cloud IAM security controls** using Azure.

It reflects practices used in:

* Enterprise cloud environments
* Security operations teams
* Compliance-driven organizations

---

## 📄 Optional: Full Report

📥 [Download PDF Version](./Lab1-IAM.pdf)
