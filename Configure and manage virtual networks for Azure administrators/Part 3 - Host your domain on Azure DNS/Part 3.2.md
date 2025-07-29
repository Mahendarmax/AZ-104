# Azure DNS Configuration - Exam Notes

## ✅ Objectives
- Create and configure DNS zones in Azure.
- Link domains to Azure DNS zones.
- Configure both **public** and **private** DNS zones.
- Add and manage DNS records (A, CNAME).
- Delegate a custom domain to Azure DNS.

---

## 🌐 Public DNS Zone Configuration

### Step 1: Create a DNS Zone
- Use **Azure DNS** to host the DNS records for your domain (e.g., `wideworldimports.com`).
- Required inputs:
  - **Subscription**
  - **Resource Group**
  - **Domain Name**
  - **Location** (defaults to Resource Group's location)

### Step 2: Get Azure DNS Name Servers
- After creating the DNS zone, retrieve **NS records**.
- These will be used to delegate the domain from the registrar.

### Step 3: Domain Delegation
- Login to your domain registrar portal.
- Update **NS records** to Azure-provided values.
- Use **all four** name servers.
- This step enables **domain delegation** to Azure DNS.

### Step 4: Verify Delegation
- Use `nslookup` to query the SOA (Start of Authority) record:
  ```bash
  nslookup -type=SOA wideworldimports.com

```
