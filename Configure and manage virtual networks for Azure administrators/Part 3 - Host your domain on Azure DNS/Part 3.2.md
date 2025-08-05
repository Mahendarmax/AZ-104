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

<img width="1094" height="763" alt="image" src="https://github.com/user-attachments/assets/a08df29d-3b5e-439a-9700-6782237b95bf" />


### Step 2: Get Azure DNS Name Servers
- After creating the DNS zone, retrieve **NS records**.
- These will be used to delegate the domain from the registrar.

<img width="1342" height="653" alt="image" src="https://github.com/user-attachments/assets/d989bbe7-fa91-432b-90fc-fc80a481cc8b" />


### Step 3: Domain Delegation
- Login to your domain registrar portal.
- Update **NS records** to Azure-provided values.
- Use **all four** name servers.
- This step enables **domain delegation** to Azure DNS.

### Step 4: Verify Delegation
- Use `nslookup` to query the SOA (Start of Authority) record:
  ```bash
  nslookup -type=SOA wideworldimports.com


# 🛠️ Configure Custom DNS Records in Azure DNS

# 📘 DNS Record Types: A vs AAAA vs CNAME

## 🔹 A Record (Address Record)
- Maps a domain to an **IPv4 address**
- Example: `example.com → 192.0.2.1`
- Used for pointing to IPv4 web servers

## 🔹 AAAA Record (Quad-A Record)
- Maps a domain to an **IPv6 address**
- Example: `example.com → 2001:db8::1`
- Used for IPv6-enabled clients

## 🔹 CNAME Record (Canonical Name)
- Maps a domain to **another domain name**
- Example: `www.example.com → example.com`
- Used for domain aliasing (subdomains only)
- ❌ **Not allowed at the zone apex** (e.g., `example.com`)

## 🔁 Summary

| Record Type | Points To         | IP Version | Used For                | Zone Apex Allowed |
|-------------|-------------------|------------|--------------------------|-------------------|
| A           | IPv4 Address      | IPv4       | Basic web hosting        | ✅ Yes            |
| AAAA        | IPv6 Address      | IPv6       | IPv6 support             | ✅ Yes            |
| CNAME       | Another Domain    | N/A        | Subdomain redirection    | ❌ No             |

> 📝 Use **ALIAS** or **ANAME** if you need to point the apex domain to another domain name.

<img width="813" height="203" alt="image" src="https://github.com/user-attachments/assets/f0bcb6e2-6b64-48da-ab65-47eae52dac61" />




## 🔹 A Record (IPv4 Mapping)

Used to map a domain or subdomain directly to an IPv4 address.

**Required Fields:**
- **Name**: e.g., `webserver1`
- **Type**: `A`
- **TTL**: Time-to-live in seconds (e.g., `3600`)
- **IP Address**: The IPv4 address of the target resource (e.g., `10.1.2.4`)

---

## 🔹 CNAME Record (Alias Mapping)

Used to alias one domain to another.

**Example Use Case:**
- Alias `www.wideworldimports.com` → `wideworldimports.com`

**Required Fields:**
- **Name**: e.g., `www`
- **Type**: `CNAME`
- **TTL**: e.g., `600`
- **Alias To**: The canonical target domain name

---

# 🔒 Configure Private DNS Zones in Azure

## 🔹 Step 1: Create a Private DNS Zone
Use the Azure portal to create a private DNS zone.

**Fields to define:**
- **Resource Group**
- **Zone Name**: e.g., `private.wideworldimports.com`

<img width="1064" height="836" alt="image" src="https://github.com/user-attachments/assets/9330d374-4643-4298-818b-45ee0e303a41" />


---

## 🔹 Step 2: Identify Virtual Networks

Identify the **Virtual Networks (VNets)** that contain **VMs** needing internal DNS resolution.

---

## 🔹 Step 3: Link VNet to DNS Zone

1. Go to your Private DNS Zone
2. Navigate to **Virtual Network Links**
3. Click **Add**
4. Link each **VNet** that needs DNS name resolution


<img width="1253" height="855" alt="image" src="https://github.com/user-attachments/assets/449053b3-2f33-4b6f-8e5b-7e38d45d3a8a" />

<img width="1157" height="582" alt="image" src="https://github.com/user-attachments/assets/e19494f2-2e67-405f-b7dc-f4a6da89f6ed" />



---

---
### Step 4: Verify Delegation
- Use `nslookup` to check if the domain is delegated successfully:
  ```bash
  nslookup -type=SOA wideworldimports.com

---

# Azure DNS - Custom DNS Records and Private DNS Zones

---

## 🧾 Step 5: Configure Custom DNS Records

### 📌 A Record
Maps a domain/subdomain to an **IPv4 address**.

**Required:**
- **Name:** e.g., `webserver1`
- **Type:** `A`
- **TTL:** Time to live in seconds (e.g., `3600`)
- **IP Address:** Target server IP (e.g., `10.0.0.5`)

---

### 📌 CNAME Record
Used to **alias** one domain to another.

**Example:**
www.wideworldimports.com → wideworldimports.com

yaml
Copy
Edit

**Required:**
- **Name:** `www`
- **TTL:** e.g., `600`
- **Type:** `CNAME`
- **Target:** Canonical domain name (e.g., `wideworldimports.com`)

---

## 🔐 Private DNS Zone Configuration

### Step 1: Create a Private DNS Zone
- Open **Azure Portal** → Search for **"Private DNS Zones"**
- Click **Create**
- Provide:
  - **Resource Group**
  - **Zone Name:** e.g., `private.wideworldimports.com`

---

### Step 2: Identify Virtual Networks
- Identify the **virtual networks (VNets)** where your **VMs** are deployed.
- These VMs need name resolution via the private DNS zone.

---

### Step 3: Link Virtual Networks to DNS Zone
- In the **Private DNS Zone**:
  - Go to `Virtual Network Links` → Click **Add**
  - Select the **Virtual Network** to link
  - Repeat for each VNet that needs **internal DNS resolution**

---


# 💡 Key Concepts

| Term               | Description                                                                 |
|--------------------|-----------------------------------------------------------------------------|
| **DNS Zone**        | Container for DNS records for a specific domain                            |
| **Public DNS Zone** | Used for domains exposed to the public internet                            |
| **Private DNS Zone**| Used for internal DNS resolution within Azure VNets                        |
| **NS Record**       | Name Server record; delegates domain authority to Azure DNS                |
| **SOA Record**      | Start of Authority; identifies the primary DNS server and delegation info  |
| **A Record**        | Direct mapping from domain name to an IPv4 address                         |
| **CNAME Record**    | Maps alias domain to a canonical (target) domain name                      |

---

✅ Use Azure DNS to centrally manage domain names with high availability and security for both public and private environments.

