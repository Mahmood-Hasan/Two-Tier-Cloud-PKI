# Two-Tier-Cloud-PKI
#Intune M365 Ecosystem
# Microsoft Cloud PKI Deployment

This repository contains the configuration as code (CaC) and documentation for the organization's Microsoft Cloud PKI implementation within Microsoft Intune.

## 🏗 Architecture
This solution uses a **Two-Tier Cloud PKI** model:
1. **Root CA**: Hosted in Microsoft Cloud PKI (Offline/Protected).
2. **Issuing CA**: Hosted in Microsoft Cloud PKI (Online/Active).
3. **Delivery**: Certificates delivered via SCEP to Windows, iOS, and Android devices.

## 🚀 Getting Started

### Prerequisites
* **License**: Microsoft Intune Suite or Cloud PKI standalone add-on.
* **Role**: Intune Administrator.

### Deployment Order
1. **Deploy CAs**: Create Root & Issuing CAs manually in Intune Portal (currently no Graph API support for *creation* of CA objects, only management).
2. **Export Public Keys**: Download `.cer` files from the portal.
3. **Update Policies**: Update the JSON files in `src/policies/` with the new CA details.
4. **Deploy Profiles**: Run `Deploy-CloudPKI.ps1` to push Trusted Cert and SCEP profiles to Intune.

## 📂 Directory Structure
* `/src/policies`: JSON templates for Intune Configuration Profiles.
* `/src/scripts`: PowerShell automation for Graph API interaction.
