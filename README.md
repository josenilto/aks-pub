# aks-pub

Enterprise-ready Azure IaC repository.

Enterprise-ready Azure IaC repository for a publicly accessible AKS cluster.

## Overview

This repository contains a modular Azure Bicep landing zone designed to provision:
- Azure Resource Groups for network, platform, and security
- Azure Virtual Network with AKS subnet delegation
- Azure Container Registry (ACR)
- Azure Log Analytics Workspace
- Azure Key Vault
- Azure Kubernetes Service (AKS) public cluster
- Subscription-level policy assignment for tags and allowed locations

## Deployment

1. Fork or clone this repo.
2. Configure Azure service principal and GitHub secrets:
   - `AZURE_CREDENTIALS`
      - `AZURE_SUBSCRIPTION_ID`
      3. Update bicep/parameters.production.json values.
      4. Run:
         - az login
            - az account set --subscription <subscription-id>
               - az deployment sub create --location eastus2 --template-file bicep/main.bicep --parameters bicep/parameters.production.json

               ## GitHub Actions

               - .github/workflows/deploy.yml deploys the Bicep template to Azure.
               - .github/workflows/security.yml validates Bicep build and syntax.

               ## Structure

               - bicep/main.bicep central deployment entrypoint.
               - bicep/modules/ reusable infrastructure modules.
               - scripts/ deployment helpers.
               
