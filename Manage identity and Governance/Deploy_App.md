# ASP.NET Core Deployment Guide

## 🚀 Environment-Specific Deployment

### 1. Publish with Environment Configuration

```bash
# Production Environment
dotnet publish -c Release -o ./publish/prod /p:EnvironmentName=Prod

# UAT Environment
dotnet publish -c Release -o ./publish/uat /p:EnvironmentName=UAT

# Pre-Production Environment
dotnet publish -c Release -o ./publish/preprod /p:EnvironmentName=PreProd
```

### 2. Deploy to Azure Web App
Change --src-path to the appropriate environment folder (e.g., ./publish/uat for UAT)
```bash
az webapp deploy \
  --resource-group YourResourceGroup \
  --name YourAppName \
  --src-path ./publish/uat \
  --type zip
```
