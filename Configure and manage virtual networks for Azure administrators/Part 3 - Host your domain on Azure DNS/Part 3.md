# 🌐 Azure DNS - Exam Notes

> **Learn the fundamentals of DNS and Azure DNS in a concise, exam-focused format.**

---

## 📘 What is DNS?

- **DNS (Domain Name System)** translates domain names (e.g., `www.example.com`) into IP addresses.
- It's a **global directory** maintained by **name servers** worldwide.
- DNS servers:
  - 🔄 **Cache** domain lookups for faster resolution.
  - 📦 Maintain key-value pairs of domains & IPs they manage.

---

## 🔍 How DNS Works

1. DNS checks local cache.
2. If not found, queries upstream DNS servers.
3. If still not found → returns **"domain not found"**.

---

## 🧭 IP Address Standards

- **IPv4**: e.g., `192.168.1.1`
- **IPv6**: e.g., `fe80::1c2e:ac15:e884:ddee`
- Devices can have both IPv4 and IPv6.

---

## ⚙️ DNS Record Types

| Type   | Description                                       |
|--------|---------------------------------------------------|
| A      | Maps domain to IPv4 address                       |
| AAAA   | Maps domain to IPv6 address                       |
| CNAME  | Creates an alias from one domain to another       |
| MX     | Mail exchange – directs mail to email server      |
| TXT    | Stores text strings – used for domain verification|
| NS     | Delegates DNS zone to use the given name servers  |
| SOA    | Start of Authority – zone info record             |
| SPF    | Email sender policy                               |
| SRV    | Specifies services (e.g., SIP, LDAP)              |
| CAA    | Certificate authority restriction                 |
| *      | Wildcards supported in some record types          |

- ✅ SOA & NS records are **automatically created** in Azure DNS zones.
- ❌ **SOA and CNAME can't use record sets**.

---

## 📋 Record Sets

- Define **multiple records** for the same domain.
```text
www.contoso.com. 3600 IN A 10.0.0.1  
www.contoso.com. 3600 IN A 10.0.0.2  
