## Exercise (Sandbox): Creating Alias Records for Azure DNS

## 📋 Prerequisites
- An active **Azure subscription**.
- Access to **Azure Cloud Shell** (Bash environment).

---

## 🚀 Steps to Run

1. **Clone the Repository**
   ```bash
   git clone https://github.com/MicrosoftDocs/mslearn-host-domain-azure-dns.git
  ```

2. **Navigate to the Directory**
   ```bash
   git clone https://github.com/MicrosoftDocs/mslearn-host-domain-azure-dns.git
  ```



2. **Add Alias Record in Azure DNS**
   - Go to your Azure DNS zone for your domain (e.g., wideworldimportsXXXX.com).
   - Select **+ Record set**.
   - Leave the **Name** blank to set the record for the apex (root) domain.
   - **Type**: Select `A`.
   - **Alias record set**: Choose `Yes`.
   - **Alias type**: Select `Azure resource`.
   - **Azure resource**: Pick your public IP resource (from the script or portal).
   - Save the record[web:19][web:26].

3. **Verification**
   - It may take up to 15 minutes for DNS changes to take effect.
   - Use DNS lookup tools to confirm your domain (wideworldimportsXXXX.com) resolves to the new load balancer IP.

## Example Settings Table

| Setting           | Value / Action      |
|-------------------|--------------------|
| Name              | (Leave blank)      |
| Type              | A                  |
| Alias record set  | Yes                |
| Alias type        | Azure resource     |
| Azure resource    | Select myPublicIP  |

## Key Benefits
- **Automatic updates**: DNS records update if Azure resource IP changes[web:19].
- **Easy load balancing**: The apex domain can directly send traffic to the load balancer.

---

> With these steps, your domain’s root address will always direct users to your Azure load balancer, making scaling-out and high availability simple[web:19][web:26].

