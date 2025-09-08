Exercise: Creating Alias Records for Azure DNS


## Why Use Alias Records?
- **Alias records** create a dynamic link between your domain's apex (root) and an Azure resource (like a load balancer)[web:19][web:20].
- They automatically update if the resource's IP changes, so DNS always points to the correct address[web:19].

## Prerequisites
- An **Azure DNS zone** already exists for your domain[web:26].
- A **public IP address** and **load balancer** are set up in Azure[web:26].

## Setup Steps

1. **Create Test Environment (Optional)**
   - Use the provided setup script to quickly create a virtual network, two VMs, and a load balancer in Azure.
   - The script outputs the public IP you'll use as the alias target.

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

