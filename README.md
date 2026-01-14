# 🚀 FinSecure: B2B Automated Onboarding & Compliance Platform

### 🎥 [Click Here to Watch the 2-Minute Demo Video](LINK_TO_YOUTUBE)

![Project Banner](assets/banner-image.png)
*(Note: Take a screenshot of your LWC Portal and put it in the assets folder)*

## 📖 Project Overview
FinSecure is an end-to-end Salesforce architecture designed to automate the **Customer Onboarding** and **KYC (Know Your Customer) Verification** process for FinTech companies. It eliminates manual data entry and integrates real-time compliance checks.

**Role:** Independent Salesforce Developer & Architect
**Timeline:** Jan 2026

## 💡 Key Features
* **Self-Service Portal:** Experience Cloud site allowing clients to self-onboard.
* **Real-Time API Verification:** Custom **Apex REST Integration** that connects to an external Government Tax Database (Simulated) to verify Business IDs instantly.
* **Auto-Conversion Logic:** Successful verification automatically converts Leads to Accounts & Opportunities.
* **Risk Management:** Failed verifications trigger **Service Cloud Cases** with High-Priority SLA for manual review.

## 🛠️ Technical Stack
| Category | Technologies Used |
|----------|-------------------|
| **Salesforce Clouds** | **Sales Cloud** (Lead & Opportunity Mgmt), **Service Cloud** (Case Automation), **Experience Cloud** (B2B Portal) |
| **Frontend** | Lightning Web Components (LWC), Aura Framework (embedded), SLDS |
| **Backend** | Apex Triggers, Asynchronous Apex (Queueable), REST API |
| **Integration** | Named Credentials, JSON Parsing, HTTP Callouts |
| **Automation** | Record-Triggered Flows, Assignment Rules, Entitlement Processes |
| **Tools** | VS Code, SFDX CLI, Postman, Git/GitHub |

## ⚙️ Architecture Diagram
*(Draw a simple box diagram in PowerPoint: Portal -> LWC -> Apex -> External API -> Salesforce Database. Save as image and link here)*
![Architecture](assets/architecture.png)

## 💻 Code Highlight: The Verification Engine
Here is how I handled the secure API call using Named Credentials to avoid hardcoding secrets:

```apex
// Snippet from KYCVerificationService.cls
public static void verifyClient(String taxId) {
    HttpRequest req = new HttpRequest();
    req.setEndpoint('callout:Government_Tax_DB/verify/' + taxId); // Named Credential
    req.setMethod('GET');
    // ... Error handling logic
}
