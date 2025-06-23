# 🏗️ Azure Physical Infrastructure Overview

Azure's infrastructure consists of:
- **Physical Infrastructure**: Datacenters, regions, availability zones
- **Management Infrastructure**: Tools and services used to manage resources

---

## 🏢 Datacenters
- Facilities housing servers with dedicated **power**, **cooling**, and **networking**
- Not directly accessible to users
- Grouped into **Regions** and **Availability Zones**

---

## 🌍 Regions
- A **region** is a geographical area with **1+ datacenters** connected via low-latency networks
- You select a region when deploying most Azure resources
- Some services (like **Microsoft Entra ID**, **Traffic Manager**, **Azure DNS**) are **global** and don’t require region selection

---

## 🧱 Availability Zones
- **Physically separate datacenters** within a region
- Each zone has **independent power, cooling, and networking**
- Designed for **high availability** and **fault isolation**
- Connected by **high-speed, private fiber networks**
- Used mainly for:
  - VMs, Managed Disks
  - Load Balancers, SQL Databases

### Types of Services:
- **Zonal**: Pinned to a specific zone (e.g., VMs)
- **Zone-redundant**: Auto-replicated across zones (e.g., zone-redundant storage)
- **Non-regional**: Global services resilient to region/zone failures

---

## 🔁 Region Pairs
- Most regions are paired with another region **300+ miles apart**
- Used for **disaster recovery** and **data replication**
- Benefits:
  - One region prioritized during large-scale outages
  - Updates rolled out one region at a time
  - Data stays within same geography (except Brazil South)

### Example Pairs:
- **West US ↔ East US**
- **Southeast Asia ↔ East Asia**
- **West India → South India** (One-directional)
- **Brazil South → South Central US** (Cross-geography)

---

## 🏛️ Sovereign Regions
Azure has **isolated sovereign regions** for compliance and legal requirements:

### Examples:
- **US Gov Regions**: For U.S. government agencies, with screened personnel
- **China Regions**: Operated by 21Vianet, not directly managed by Microsoft

---

## 🔗 Learn More
Explore Azure's global infrastructure here:  
👉 [Azure Global Infrastructure](https://azure.microsoft.com/en-us/explore/global-infrastructure/)
