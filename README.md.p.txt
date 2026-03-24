# Yahdi Tech: M365 E5 Enterprise Lab
**Architect:** Yahdi
**Focus:** Zero-Trust SharePoint Architecture & Data Loss Prevention (DLP)

## Architecture Overview
I have architected a Hub-and-Spoke model to centralize communication while maintaining strict departmental boundaries.

### Linked Sites:
* **Hub Site:** All Staff Internal Project (Communication Hub)
* **Spoke 1:** HR Department (Restricted Team Site)
* **Spoke 2:** Yahdi Tech Team Site (Collaboration)
* **Spoke 3:** Global Operations (Operational Logistics)

## How I Linked Them (Practical Steps)
1. **Hub Registration:** I designated the "All Staff" site as the Hub in the SharePoint Admin Center.
2. **Association:** I navigated to the HR and Global Operations sites and associated them with the "All Staff" Hub ID.
3. **Navigation Sync:** I enabled "Hub Navigation" so the top menu bar is consistent across all four sites.
4. **News Roll-up:** Configured the "News" web part on the Hub to automatically pull updates from the HR and Global Ops spoke sites.

## Security & DLP
* **Sensitivity Labels:** Applied "Highly Confidential" labels to the HR site.
* **DLP Policy:** Created a tenant-wide policy to block PII (Credit Cards/SSNs) from being shared via WhatsApp or External Email.

### 🛡️ Data-Centric Security (The "No Folders" Strategy)
In the **Yahdi Tech** HR Department, I implemented a "Flat" file structure rather than traditional folders. 

* **The Challenge:** Folders create "silos" and security often breaks if a file is moved.
* **The Solution:** I applied **Information Protection** directly to the data. 
* **The Proof:** Even with a sensitive file (Credit Card) sitting in the root directory, my **Sensitivity Labels** and **DLP** successfully identified, encrypted, and governed the data.
* **Evidence:** See `Flat-Architecture-Security.png` in the repository.

Pillar 2: Identity & Access Management (Entra ID)

Goal: Secure the HR Department using Zero-Trust principles.
Implementation: Configured a Conditional Access Policy that triggers an MFA (Multi-Factor Authentication) requirement whenever a user attempts to access SharePoint resources.
Logic: Verify Explicitly. Even with a correct password, the user must provide a secondary "Identity Proof" (Microsoft Authenticator app).

