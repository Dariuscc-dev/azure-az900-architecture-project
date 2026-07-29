# azure-az900-architecture-project
Cloud architecture case study (E-commerce migration) and quick reference guide for Microsoft Azure Fundamentals (AZ-900).

# ☁️ Microsoft Azure Architecture & Fundamentals (AZ-900)

![Microsoft Azure](https://img.shields.io/badge/Microsoft_Azure-0089D6?style=for-the-badge&logo=microsoft-azure&logoColor=white)
![Certification](https://img.shields.io/badge/AZ--900-Passed-brightgreen?style=for-the-badge)
![Architecture](https://img.shields.io/badge/Cloud_Architecture-PaaS_--_IaaS-blue?style=for-the-badge)

Professional reference repository for **Microsoft Azure**. It contains a **Practical Cloud Architecture Case Study** (E-commerce Migration) and a **Quick Reference Guide (Cheat Sheet)** based on the skills measured in the **AZ-900: Microsoft Azure Fundamentals** exam.

---

## 🚀 PART 1: Azure Architecture Case Study

### 📋 Project Context
A retail company wants to migrate its traditional e-commerce platform to **Microsoft Azure** to ensure high availability, high scalability during sales peaks (e.g., Black Friday), advanced security for banking data, and operational cost optimization.

### 🏗️ Solution Architecture Diagram

```text
                        [ USERS / CLIENTS ]
                                   │
                                   ▼
                       [ Azure Front Door / WAF ]
                                   │
                                   ▼
                        [ Azure Virtual Network ]
      ┌─────────────────────────────────────────────────────────┐
      │  [ Frontend / Backend Subnet ]                         │
      │   └── Azure App Service (Auto-scaling / PaaS)           │
      │        ├── Web / API Microservice                       │
      │        └── Azure Functions (Order Processing)           │
      │                                                         │
      │  [ Data / Internal Services Subnet ]                   │
      │   ├── Azure SQL Database (Relational / Order Data)      │
      │   ├── Azure Blob Storage (Catalog / Images)             │
      │   └── Azure Key Vault (Secrets, Certificates & Keys)    │
      └─────────────────────────────────────────────────────────┘
                                   ▲
                                   │ (Identity & RBAC Permissions)
                        [ Microsoft Entra ID ]
