# AZ-104 Microsoft Azure Administrator - 104 Most Commonly Asked Exam Questions with Answers

## Identity and Governance (15 Questions)

1. **What is the difference between Azure AD tenant and Azure subscription?**
   - **Answer:** An Azure AD tenant is a dedicated instance of Azure AD that represents an organization, while an Azure subscription is an agreement with Microsoft to use cloud services. A tenant can have multiple subscriptions, but each subscription is associated with only one tenant.

2. **How do you configure Azure AD Connect for hybrid identity?**
   - **Answer:** Install Azure AD Connect on a domain-joined server, select "Customize" installation, choose password hash sync or federation, select the AD forest, configure OU filtering, and complete the synchronization process.

3. **What are the different license types available in Azure AD?**
   - **Answer:** Free, Office 365 apps, Premium P1, Premium P2, and Microsoft 365 Business Premium. Each tier provides increasing functionality for identity and access management.

4. **How do you implement Multi-Factor Authentication (MFA) for users?**
   - **Answer:** Navigate to Azure AD > Security > Conditional Access > New policy > Select users/groups > Require MFA > Enable policy. Can also enable per-user MFA in Azure AD > Users > Multi-Factor Authentication.

5. **What is Conditional Access and how do you configure it?**
   - **Answer:** Conditional Access is a policy-based system that enforces access controls based on conditions. Configure via Azure AD > Security > Conditional Access > New policy > Define conditions (user, location, device) > Grant/deny access controls.

6. **How do you create and manage Azure AD groups?**
   - **Answer:** Via Azure AD > Groups > New group > Select group type (Security/Microsoft 365), add members, assign roles/permissions. Can be managed through PowerShell or Azure CLI.

7. **What is the difference between Azure RBAC and Azure AD roles?**
   - **Answer:** Azure RBAC controls access to Azure resources (e.g., VM, storage), while Azure AD roles control access to Azure AD resources (e.g., user management, directory settings).

8. **How do you assign roles at different scopes?**
   - **Answer:** Via Access control (IAM) at each scope level: Management Group, Subscription, Resource Group, or Resource. Select Add role assignment > Choose role > Select members > Review and assign.

9. **What is Azure Policy and how does it differ from Azure RBAC?**
   - **Answer:** Azure Policy enforces organizational standards and compliance by evaluating resource properties. RBAC controls who can access resources. Policy prevents non-compliant resources from being created; RBAC controls access to existing resources.

10. **How do you create custom Azure Policy definitions?**
    - **Answer:** Via Azure Policy > Definitions > New policy definition > Define rules in JSON format > Set parameters > Save to appropriate scope. Use aliases to target specific resource properties.

11. **What is Azure Blueprint and when would you use it?**
    - **Answer:** Azure Blueprint packages artifacts (policies, roles, templates, resource groups) for consistent environment deployment. Use for standardizing compliance, security, and governance across subscriptions.

12. **How do you implement resource locks and what are the different types?**
    - **Answer:** Via resource > Settings > Locks > Add lock. Types: CanNotDelete (prevents deletion) and ReadOnly (prevents modification). Can be applied at resource, resource group, or subscription level.

13. **What is the difference between Azure AD B2B and B2C?**
    - **Answer:** B2B (Business-to-Business) allows external users from partner organizations to access resources. B2C (Business-to-Consumer) manages consumer/customer identities and access to applications.

14. **How do you configure guest user access in Azure AD?**
    - **Answer:** Via Azure AD > Users > New guest user > Invite user by email > Assign appropriate roles/permissions > Configure guest user settings in External collaboration settings.

15. **What is Privileged Identity Management (PIM) and how do you enable it?**
    - **Answer:** PIM provides just-in-time privileged access to Azure AD and Azure resources. Enable via Azure AD > Privileged Identity Management > Onboard > Configure roles for elevation, approval workflows, and access reviews.

## Storage (12 Questions)

16. **What are the different types of Azure Storage accounts?**
    - **Answer:** General Purpose v2 (recommended), General Purpose v1, BlockBlobStorage, FileStorage, and BlobStorage. GPv2 supports all storage services (blobs, files, queues, tables).

17. **How do you configure storage account replication options?**
    - **Answer:** During storage account creation or via Configuration > Replication: LRS (Locally Redundant), GRS (Geo-Redundant), ZRS (Zone-Redundant), GZRS (Geo-Zone-Redundant). Choose based on durability and availability requirements.

18. **What is the difference between hot, cool, and archive storage tiers?**
    - **Answer:** Hot: frequently accessed data (higher cost, immediate access). Cool: infrequently accessed data (lower cost, immediate access). Archive: rarely accessed data (lowest cost, hours to retrieve).

19. **How do you implement Azure Storage encryption?**
    - **Answer:** Enabled by default with Microsoft-managed keys. For customer-managed keys: Storage account > Encryption > Select customer-managed keys > Configure key vault. Data is encrypted at rest and in transit.

20. **What are storage access keys and how do you rotate them?**
    - **Answer:** 512-bit keys used for authentication. Rotate via Storage account > Access keys > Regenerate key1/key2. Update applications to use new keys. Follow rotation best practices.

21. **How do you configure Shared Access Signatures (SAS) tokens?**
    - **Answer:** Via Storage account > Shared access signature > Define allowed services, resource types, permissions, start/expiry times, IP restrictions > Generate SAS token. Can also create service-level SAS.

22. **What is Azure Storage Explorer and how do you use it?**
    - **Answer:** Free standalone app for managing Azure Storage. Download from Microsoft, connect with Azure account or storage credentials, browse and manage blobs, files, queues, tables across subscriptions.

23. **How do you implement Azure Files and Azure File Sync?**
    - **Answer:** Create Azure Files share via Storage account > File shares. Install File Sync agent on Windows Server, register server, create sync group, add server endpoint and cloud endpoint.

24. **What is the difference between Azure Blob Storage and Azure Data Lake Storage Gen2?**
    - **Answer:** Blob Storage: object storage for unstructured data. Data Lake Gen2: hierarchical namespace with directory structure, optimized for big data analytics, supports both object and file system semantics.

25. **How do you configure lifecycle management policies for storage?**
    - **Answer:** Via Storage account > Lifecycle management > Add rule > Define conditions (age, tier, blob type) > Set actions (move to cool/archive, delete). Rules run daily to automate data lifecycle.

26. **What is soft delete and how do you enable it for different storage services?**
    - **Answer:** Protects against accidental deletion. Enable via: Blob storage > Data protection > Enable soft delete (configurable retention period). Also available for file shares and Azure Files.

27. **How do you monitor storage account performance and usage?**
    - **Answer:** Via Storage account > Monitoring > Metrics (transactions, latency, availability). Set up alerts, use Storage Analytics logs, configure diagnostic settings to send logs to Log Analytics.

## Compute (15 Questions)

28. **What are the different VM sizes available in Azure?**
    - **Answer:** General purpose (B, Dsv3, Dv3), Compute optimized (Fsv2), Memory optimized (Esv3, Ev3, M), Storage optimized (Lsv2), GPU (NC, NV), High performance compute (H, HB, HC).

29. **How do you configure VM availability sets and availability zones?**
    - **Answer:** Availability sets: group VMs across fault/update domains within a region. Availability zones: distribute VMs across physically separate zones within a region for higher availability.

30. **What is the difference between managed and unmanaged disks?**
    - **Answer:** Managed disks: Azure manages storage account creation/scaling, better reliability. Unmanaged disks: you manage storage accounts, limited scalability. Always use managed disks for new deployments.

31. **How do you implement VM scale sets?**
    - **Answer:** Via VM scale sets > Create > Configure VM template, scaling policy (manual/autoscale), load balancer, health probes. Supports up to 1000 VMs with custom images.

32. **What is Azure Dedicated Host and when would you use it?**
    - **Answer:** Physical server dedicated to your organization. Use for compliance requirements, licensing benefits, or when you need physical isolation from other tenants.

33. **How do you configure VM extensions?**
    - **Answer:** Via VM > Extensions > Add > Select extension (Custom Script, DSC, Monitoring). Can be installed automatically during VM deployment or added post-deployment.

34. **What is Azure Bastion and how do you configure it?**
    - **Answer:** PaaS service providing secure RDP/SSH access to VMs via browser/Azure portal. Configure via Bastion > Create > Associate with VNet > Configure SKU (Basic/Standard).

35. **How do you implement backup for Azure VMs?**
    - **Answer:** Via Recovery Services vault > Backup > Azure Virtual Machine > Select VMs > Configure backup policy (frequency, retention). Supports file-level and VM-level recovery.

36. **What is the difference between Azure Container Instances and AKS?**
    - **Answer:** ACI: simple, serverless container deployment for single containers. AKS: full managed Kubernetes service for container orchestration with scaling, networking, storage.

37. **How do you configure container registries?**
    - **Answer:** Via Container registries > Create > Configure SKU (Basic/Standard/Premium), admin user, network access. Use for storing Docker images, integrate with AKS/ACI.

38. **What is Azure App Service and what are the different app types?**
    - **Answer:** PaaS for web applications. Types: Web Apps, API Apps, Mobile Apps, Function Apps. Supports multiple languages (.NET, Java, Node.js, Python, PHP).

39. **How do you configure deployment slots for App Service?**
    - **Answer:** Via App Service > Deployment slots > Add slot > Configure source (code repository, container). Supports staging/production slots with traffic routing and swap capabilities.

40. **What is the difference between App Service Plans and ASE?**
    - **Answer:** App Service Plan: shared infrastructure with other customers. ASE (App Service Environment): dedicated isolated environment with full network control and higher scale.

41. **How do you configure auto-scaling for App Service?**
    - **Answer:** Via App Service Plan > Scale out > Configure autoscale based on metrics (CPU, memory, requests) or schedule. Supports horizontal scaling with instance limits.

42. **What is Azure Functions and how do you configure triggers?**
    - **Answer:** Serverless compute service for event-driven code. Triggers: HTTP, Timer, Queue, Blob, Event Grid. Configure via function.json or portal settings.

## Virtual Networking (15 Questions)

43. **What is the difference between VNet peering and VNet-to-VNet connection?**
    - **Answer:** VNet peering: low-latency, high-bandwidth connection between VNets (same or different regions). VNet-to-VNet: VPN connection using VPN gateways.

44. **How do you configure Network Security Groups (NSGs)?**
    - **Answer:** Via NSG > Create > Configure inbound/outbound security rules (priority, source/destination, port, protocol). Associate with subnets or network interfaces.

45. **What is Azure Firewall and how does it differ from NSG?**
    - **Answer:** Azure Firewall: fully stateful firewall as a service with threat intelligence, FQDN filtering. NSG: basic layer 3/4 filtering at subnet/NIC level. Firewall provides more advanced features.

46. **How do you implement Azure Application Gateway?**
    - **Answer:** Via Application Gateway > Create > Configure frontend IP, backend pools, health probes, routing rules (path-based, multi-site). Supports SSL termination and WAF.

47. **What is the difference between public, private, and static IP addresses?**
    - **Answer:** Public: accessible from internet. Private: internal VNet communication. Static: reserved IP that doesn't change. Dynamic: allocated from pool and may change.

48. **How do you configure Azure DNS?**
    - **Answer:** Via DNS zones > Create > Add DNS records (A, AAAA, CNAME, MX, TXT). Can host domains or configure private DNS zones for VNet name resolution.

49. **What is Azure Front Door and when would you use it?**
    - **Answer:** Global load balancing service with SSL offload and WAF. Use for global applications requiring low latency, high availability, and protection at edge.

50. **How do you implement VPN Gateway and different VPN types?**
    - **Answer:** Via VPN Gateway > Create > Configure gateway type (VPN), VPN type (Route-based/Policy-based), SKU (Basic/VpnGw1-5), connection type (Site-to-Site, Point-to-Site, VNet-to-VNet).

51. **What is ExpressRoute and how does it differ from VPN?**
    - **Answer:** ExpressRoute: private dedicated connection through connectivity provider. VPN: encrypted connection over public internet. ExpressRoute offers higher bandwidth, lower latency, and reliability.

52. **How do you configure Azure Load Balancer?**
    - **Answer:** Via Load Balancer > Create > Configure frontend IP, backend pool, health probes, load balancing rules (protocol, port, backend port). Supports public and internal load balancers.

53. **What is Azure Traffic Manager and how do you configure routing methods?**
    - **Answer:** DNS-based traffic routing service. Routing methods: Priority, Weighted, Performance, Geographic, Multivalue, Subnet. Configure via Traffic Manager profile > Endpoints > Routing method.

54. **How do you implement Network Watcher?**
    - **Answer:** Via Network Watcher > Enable in region > Use tools: IP flow verify, NSG diagnostics, Connection troubleshoot, Packet capture, Topology view.

55. **What is Service Endpoint and Private Endpoint?**
    - **Answer:** Service Endpoint: extends VNet identity to Azure services over Microsoft backbone. Private Endpoint: private IP from VNet for accessing Azure services privately.

56. **How do you configure Azure DDoS Protection?**
    - **Answer:** Via DDoS Protection Plans > Create > Associate with VNets. Two tiers: Basic (automatically enabled) and Standard (additional mitigation, cost based on resources).

57. **What is Azure Virtual WAN?**
    - **Answer:** Networking service providing optimized branch connectivity to Azure. Combines VPN, ExpressRoute, and SD-WAN connectivity with centralized management and routing.

## Monitoring (10 Questions)

58. **What is Azure Monitor and what are its components?**
    - **Answer:** Comprehensive monitoring solution. Components: Metrics, Logs, Alerts, Workbooks, Application Insights, VM insights, Container insights.

59. **How do you configure Log Analytics workspaces?**
    - **Answer:** Via Log Analytics workspaces > Create > Configure pricing tier, retention, data sources. Collect logs from Azure resources, agents, or custom sources.

60. **What is Application Insights and how do you implement it?**
    - **Answer:** APM service for web applications. Implement via: App Service > Application Insights > Enable, or manually add SDK to application code. Provides performance, availability, and usage telemetry.

61. **How do you create and manage alerts in Azure?**
    - **Answer:** Via Monitor > Alerts > New alert rule > Select resource > Define condition (metric/log) > Set action group (email, SMS, webhook) > Configure alert details.

62. **What is the difference between metrics and logs?**
    - **Answer:** Metrics: numerical values at regular intervals (performance, usage). Logs: detailed events with properties, collected when events occur. Metrics for real-time monitoring, logs for troubleshooting.

63. **How do you configure diagnostic settings for Azure resources?**
    - **Answer:** Via resource > Diagnostic settings > Add diagnostic setting > Select categories > Choose destination (Log Analytics, Storage account, Event Hub) > Save.

64. **What is Azure Advisor and how do you use it?**
    - **Answer:** Personalized cloud consultant providing recommendations for high availability, security, performance, and cost optimization. Access via Azure portal > Advisor > Review recommendations.

65. **How do you implement Azure Service Health?**
    - **Answer:** Via Service Health > Configure health alerts > Select services/regions > Set up notifications for planned maintenance, service issues, health advisories.

66. **What is Kusto Query Language (KQL) and how do you use it?**
    - **Answer:** Query language for Azure Monitor Logs. Use in Log Analytics workspace to analyze log data: basic syntax includes where, project, summarize, join operators.

67. **How do you configure action groups for alerts?**
    - **Answer:** Via Monitor > Alerts > Action groups > Create > Configure notifications (email, SMS, push) and actions (webhook, runbook, logic app) > Associate with alert rules.

## Backup and Recovery (8 Questions)

68. **What is Azure Backup and what can you protect?**
    - **Answer:** Cloud-based backup solution protecting: Azure VMs, SQL databases, SAP HANA, Azure Files, on-premises servers. Provides long-term retention and centralized management.

69. **How do you configure Recovery Services vaults?**
    - **Answer:** Via Recovery Services vaults > Create > Configure backup policies (frequency, retention), storage replication (LRS/GRS), soft delete settings, encryption.

70. **What is the difference between Azure Backup and Azure Site Recovery?**
    - **Answer:** Backup: data backup and recovery. Site Recovery: disaster recovery for business continuity (VM replication, failover). Backup protects data, Site Recovery protects entire workloads.

71. **How do you implement backup policies?**
    - **Answer:** Via Recovery Services vault > Backup policies > Create > Define backup frequency (daily/weekly), retention range (daily/weekly/monthly/yearly), backup time windows.

72. **What is the difference between snapshot and backup?**
    - **Answer:** Snapshot: point-in-time copy of disk, stored in same region, limited retention. Backup: complete backup with long-term retention, cross-region storage, application-consistent.

73. **How do you perform file-level recovery from Azure VM backup?**
    - **Answer:** Via Recovery Services vault > Backup items > Azure VM > File recovery > Select recovery point > Download script > Mount volumes > Copy files.

74. **What is cross-region restore in Azure Backup?**
    - **Answer:** Capability to restore backup data to a secondary region during primary region outage. Configure via vault > Properties > Cross Region Restore > Enable.

75. **How do you configure soft delete for Azure Backup?**
    - **Answer:** Enabled by default for 14 days. Configure via Recovery Services vault > Properties > Security Settings > Soft delete > Adjust retention period (7-14 days).

## Data Protection (8 Questions)

76. **What is Azure Information Protection and how do you configure it?**
    - **Answer:** Cloud-based classification and protection service. Configure via Azure portal > Information Protection > Activate > Configure labels and policies > Deploy client.

77. **How do you implement Azure Key Vault?**
    - **Answer:** Via Key Vault > Create > Configure access policies, network access, soft delete, purge protection. Store secrets, keys, certificates with RBAC control.

78. **What is the difference between secrets, keys, and certificates in Key Vault?**
    - **Answer:** Secrets: passwords, connection strings. Keys: cryptographic keys for encryption/signing. Certificates: X.509 certificates with automatic renewal.

79. **How do you configure access policies for Key Vault?**
    - **Answer:** Via Key Vault > Access policies > Add > Select principal > Configure key/secret/certificate permissions > Save. Can use access policies or Azure RBAC.

80. **What is Azure Disk Encryption and how do you implement it?**
    - **Answer:** Uses BitLocker for Windows, DM-Crypt for Linux. Implement via VM > Disks > Encryption > Select key vault and key > Enable encryption. Requires VM agent.

81. **How do you implement Transparent Data Encryption (TDE) for Azure SQL?**
    - **Answer:** Enabled by default for new databases. Configure via SQL database > Transparent data encryption > Use service-managed or customer-managed keys in Key Vault.

82. **What is Always Encrypted and how do you configure it?**
    - **Answer:** Feature protecting sensitive data in SQL databases. Configure via SQL Server Management Studio > Always Encrypted wizard > Select columns > Generate column master key > Configure key store.

83. **How do you implement Azure AD authentication for Azure SQL?**
    - **Answer:** Via SQL server > Azure Active Directory admin > Set admin > Connect using Azure AD authentication (contained users or Azure AD groups).

## Migration and Integration (6 Questions)

84. **What is Azure Migrate and what does it assess?**
    - **Answer:** Service assessing on-premises workloads for migration to Azure. Assesses: VMware/Hyper-V VMs, physical servers, databases, web apps, providing sizing and cost estimates.

85. **How do you use Azure Site Recovery for migration?**
    - **Answer:** Configure ASR > Create Recovery Services vault > Prepare infrastructure > Enable replication > Perform test failover > Complete migration > Disable replication.

86. **What is Azure Database Migration Service?**
    - **Answer:** Service for migrating databases to Azure with minimal downtime. Supports SQL Server, MySQL, PostgreSQL, MongoDB migrations to Azure database services.

87. **How do you implement Azure Data Box?**
    - **Answer:** Order via Azure portal > Data Box > Create order > Receive device > Copy data > Return device > Data uploaded to Azure storage account.

88. **What is Azure Import/Export service?**
    - **Answer:** Service for importing/exporting large amounts of data using physical disks. Configure via Azure portal > Import/Export jobs > Prepare drives with WAImportExport tool.

89. **How do you configure hybrid connections with on-premises?**
    - **Answer:** Via App Service > Networking > Hybrid connections > Add > Configure endpoint (host, port) > Install hybrid connection manager on on-premises server.

## Cost Management (8 Questions)

90. **What is Azure Cost Management + Billing?**
    - **Answer:** Service for monitoring, analyzing, and optimizing Azure costs. Provides cost analysis, budgets, recommendations, and export capabilities.

91. **How do you configure budgets and alerts?**
    - **Answer:** Via Cost Management + Billing > Budgets > Add > Set amount, time period, filters > Configure alert conditions and action groups > Save.

92. **What are Reserved Instances and how do they save costs?**
    - **Answer:** Pre-paid VM capacity for 1-3 years offering up to 72% discount. Purchase via Reservations > Add > Select scope, region, VM size, term > Commit to usage.

93. **How do you analyze cost using Azure Advisor?**
    - **Answer:** Via Advisor > Cost tab > Review recommendations (right-size VMs, delete unused resources, use reserved instances) > Implement suggestions.

94. **What is the difference between pay-as-you-go and Enterprise Agreement?**
    - **Answer:** Pay-as-you-go: monthly billing based on usage. Enterprise Agreement: volume licensing with discounted rates, annual commitment, centralized billing for organizations.

95. **How do you implement Azure Hybrid Benefit?**
    - **Answer:** Use existing Windows/SQL Server licenses in Azure for cost savings. Configure during VM creation or via VM > Configuration > Azure Hybrid Benefit > Select license type.

96. **What are Azure Spot VMs and when would you use them?**
    - **Answer:** Unused Azure compute capacity at discounted rates (up to 90% off). Use for fault-tolerant, flexible workloads like batch processing, dev/test environments.

97. **How do you configure resource tagging for cost allocation?**
    - **Answer:** Via Resource > Tags > Add tags (e.g., Department, Environment, CostCenter). Use tags in cost analysis for filtering and grouping expenses by categories.

## Governance and Compliance (8 Questions)

98. **What is Azure Resource Manager (ARM) and how do you use it?**
    - **Answer:** Management layer providing consistent operations for Azure resources. Use via portal, PowerShell, CLI, REST API, or ARM templates for resource deployment and management.

99. **How do you create and deploy ARM templates?**
    - **Answer:** Create JSON template defining resources > Deploy via portal (Custom deployment), PowerShell (New-AzResourceGroupDeployment), CLI (az deployment group create), or DevOps pipelines.

100. **What is Azure Policy and how do you create custom policies?**
    - **Answer:** Service enforcing organizational standards. Create custom policy via Policy > Definitions > New > Define rules in JSON using aliases > Set parameters > Save to scope.

101. **How do you implement resource tagging strategies?**
    - **Answer:** Define tagging standards (Environment, Owner, CostCenter), enforce via Azure Policy, automate tagging during deployment, use tag inheritance, regularly audit compliance.

102. **What is Azure Management Groups and how do you organize them?**
    - **Answer:** Level above subscriptions for hierarchical governance. Create via Management groups > Add > Build hierarchy (e.g., Root > Departments > Subscriptions) > Apply policies and RBAC.

103. **How do you configure Azure Security Center?**
    - **Answer:** Enable via Security Center > Pricing and settings > Select subscription > Enable enhanced security features > Configure security policies and recommendations.

104. **What is Azure Blueprint and how do you implement it?**
    - **Answer:** Package of artifacts (templates, policies, RBAC) for consistent environment deployment. Create via Blueprints > Create blueprint > Add artifacts > Publish > Assign to subscription.

---

## Additional Study Resources:
- **Microsoft Learn Path**: Complete AZ-104 learning path
- **Practice Labs**: Use Azure free account for hands-on practice
- **Documentation**: Review Azure docs for each service
- **Community**: Join Azure forums and study groups
- **Updates**: Check exam updates as Azure services evolve

## Exam Tips:
- Focus on understanding concepts, not just memorization
- Practice in Azure portal regularly
- Understand the "why" behind each configuration
- Review case studies and scenario-based questions
- Time management during exam is crucial
