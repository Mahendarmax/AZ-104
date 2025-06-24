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
