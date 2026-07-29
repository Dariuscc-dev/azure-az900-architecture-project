# azure-az900-architecture-project
Cloud architecture case study (E-commerce migration) and quick reference guide for Microsoft Azure Fundamentals (AZ-900).

# Microsoft Azure Architecture & Fundamentals (AZ-900)

![Microsoft Azure](https://img.shields.io/badge/Microsoft_Azure-0089D6?style=for-the-badge&logo=microsoft-azure&logoColor=white)
![Certification](https://img.shields.io/badge/AZ--900-Passed-brightgreen?style=for-the-badge)
![Architecture](https://img.shields.io/badge/Cloud_Architecture-PaaS_--_IaaS-blue?style=for-the-badge)

Professional reference repository for **Microsoft Azure**. It contains a **Practical Cloud Architecture Case Study** (E-commerce Migration) and a **Quick Reference Guide (Cheat Sheet)** based on the skills measured in the **AZ-900: Microsoft Azure Fundamentals** exam.

---

## PART 1: Azure Architecture Case Study

### Project Context
A retail company wants to migrate its traditional e-commerce platform to **Microsoft Azure** to ensure high availability, high scalability during sales peaks (e.g., Black Friday), advanced security for banking data, and operational cost optimization.

### Solution Architecture Diagram

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
```
### Services Breakdown & Technical Justification

| Component | Selected Service | Type | Business / Technical Justification |
| :--- | :--- | :--- | :--- |
| **Compute** | **Azure App Service** | PaaS | Hosts the web app without managing OS servers. Allows vertical and horizontal *auto-scaling* based on traffic. |
| **Serverless** | **Azure Functions** | PaaS | Executes asynchronous tasks on demand (confirmation emails, invoice processing), paying only for milliseconds of use. |
| **Database** | **Azure SQL Database** | PaaS | Managed relational DB with automated backups, encryption at rest, and a 99.99% SLA. |
| **Storage**| **Azure Blob Storage** | IaaS/PaaS | Massive, cost-effective object storage for product images and multimedia assets using *Hot/Cool* tiers. |
| **Security** | **Microsoft Entra ID** | SaaS | Unified authentication, conditional access, and Role-Based Access Control (**RBAC**). |
| **Secrets** | **Azure Key Vault** | PaaS | Centralized and secure custody of DB connection strings, API tokens, and SSL certificates. |

### Financial Estimation & Cost Management
Using the **Azure Pricing Calculator**, an initial architecture in the *West Europe* / *Spain Central* region was estimated:
* **Estimated Environment:** ~180 USD/month for baseline traffic.
* **Optimization Strategy:**
  * Use of **Azure Reserved Instances (1 or 3 years)** for Azure SQL, achieving savings of up to 40-60%.
  * **Auto-scaling rules** in App Service to reduce instances to the minimum scale during night hours.
  * Definition of **Budgets and Alerts** using *Azure Cost Management*.

---

## PART 2: AZ-900 Fundamentals & Cheat Sheet

### 1. Key Cloud Computing Concepts
* **High Availability (HA):** The system's ability to remain operational without prolonged interruptions (SLAs).
* **Scalability & Elasticity:** *Scalability* is the ability to grow to meet demand; *Elasticity* is the ability to automatically expand or contract resources based on current demand.
* **CapEx vs. OpEx:**
  * **CapEx (Capital Expenditure):** Upfront investment in physical infrastructure.
  * **OpEx (Operational Expenditure):** Ongoing cost under a *Pay-as-you-go* model.

### 2. Cloud Service Models
```text
┌──────────────────────────────────────────────────────────┐
│ SaaS: Microsoft 365, Power BI (Managed by Microsoft)     │
├──────────────────────────────────────────────────────────┤
│ PaaS: App Service, Azure SQL  (Code/Data = User)         │
├──────────────────────────────────────────────────────────┤
│ IaaS: Azure VMs, VNets        (OS/Network/App = User)    │
└──────────────────────────────────────────────────────────┘
```
### 3. Azure Global Infrastructure
* **Regions:** Geographical areas comprising one or more Data Centers connected by a low-latency network.
* **Availability Zones (AZs):** Physically separate datacenters within an Azure region (fault tolerance against power/cooling/network failures).
* **Region Pairs:** Each region is paired with another region at least 300 miles away to ensure Disaster Recovery (DR).

---

## Official Certification
* **Exam:** AZ-900: Microsoft Azure Fundamentals
* **Date Achieved:** May 6th
* **Status:** ✅ Passed / Officially Certified
