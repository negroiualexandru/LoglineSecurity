# Logline Security
### *AI-Powered Cybersecurity News Aggregator*

[![React](https://img.shields.io/badge/React-20232A?style=flat&logo=react&logoColor=61DAFB)](https://reactjs.org/) [![Azure](https://img.shields.io/badge/Azure-0078D4?style=flat&logo=microsoft-azure&logoColor=white)](https://azure.microsoft.com/) [![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=flat&logo=typescript&logoColor=white)](https://www.typescriptlang.org/) [![OpenAI](https://img.shields.io/badge/Azure_OpenAI-00A4EF?style=flat&logo=openai&logoColor=white)](https://azure.microsoft.com/en-us/products/ai-services/openai-service) [![Cybersecurity](https://img.shields.io/badge/Cybersecurity-CC0000?style=flat&logo=kalilinux&logoColor=white)](https://en.wikipedia.org/wiki/Computer_security)

**Logline Security** is a centralized intelligence platform designed to streamline information consumption for security professionals. By leveraging **Azure OpenAI**, it automatically aggregates, categorizes, and prioritizes cybersecurity news from verified global sources, reducing the noise in daily threat feeds.

[**🔴 Live Demo**](https://jolly-field-07b6e4f1e.2.azurestaticapps.net/) | [**🎥 Video Walkthrough**](https://youtu.be/l7jPnBRpH2E)

> **Note on Infrastructure:** This demo runs on a serverless free-tier architecture. Please allow **up to 60 seconds** for the cold start of the backend API on your first request.
> 
> **Demo Video Disclosure:** Due to screen recording limitations, overlay elements (dropdowns/modals) are not visible in the video playback. Please refer to the Live Demo to see these interactions in action.
---

## 🏗️ System Architecture

```mermaid
%%{init: {'theme': 'base', 'themeVariables': { 'background': '#ffffff', 'primaryColor': '#ffffff', 'edgeLabelBackground':'#ffffff', 'tertiaryColor': '#ffffff', 'clusterBkg': '#fafafa', 'clusterBorder': '#e5e7eb', 'lineColor': '#0078D4', 'fontSize': '14px'}}}%%
graph LR
    %% --- NODES & SUBGRAPHS ---
    subgraph Client ["Client & Proxy"]
        Browser["User / React App"]
        NodeProxy["Node.js Server <br/>(API Proxy)"]
    end

    subgraph Azure ["Microsoft Azure Cloud"]
        APIM["Azure API Management<br/>(Gateway)"]
        
        subgraph Apps ["Serverless Compute"]
            AuthFunc["Azure Functions <br/>(Backend API & JWT Auth)"]
            ScraperFunc["Azure Functions <br/>(Daily Scraper)"]
        end
        
        subgraph Data ["Data & Services"]
            CosmosDB[("Azure Cosmos DB")]
            OpenAI["Azure OpenAI Service<br/>(Classification)"]
            Email["Azure Communication<br/>Services"]
        end
    end
    
    %% EXTERNAL
    Timer(("8:00 AM<br/>Timer"))
    Internet(("External RSS"))

    %% --- CONNECTIONS ---
    
    %% 1. USER FLOW (Top Lane)
    Browser -- "1. HTTPS Request" --> NodeProxy
    NodeProxy -- "2. Forward" --> APIM
    APIM -- "3. Auth Request" --> AuthFunc
    AuthFunc -- "4. Query" --> CosmosDB
    CosmosDB -.-> AuthFunc
    AuthFunc -.-> Browser

    %% 2. SCRAPER FLOW (Bottom Lane)
    Timer -- "Triggers" --> ScraperFunc
    ScraperFunc -- "1. Fetch RSS" --> Internet
    ScraperFunc -- "2. Classify" --> OpenAI
    OpenAI -.-> ScraperFunc
    ScraperFunc -- "3. Store" --> CosmosDB
    ScraperFunc -- "4. Alert" --> Email

    %% --- STYLING ---
    
    %% Arrow Styling
    linkStyle default stroke:#0078D4,stroke-width:2px,fill:none

    %% Node Colors
    style APIM fill:#005C5C,stroke:#005C5C,color:#fff
    style AuthFunc fill:#FFFFFF,stroke:#2C3E50,stroke-width:2px,color:#333
    style ScraperFunc fill:#FFFFFF,stroke:#2C3E50,stroke-width:2px,color:#333
    style OpenAI fill:#0078D4,stroke:#0078D4,color:#fff
    style CosmosDB fill:#5C2D91,stroke:#5C2D91,color:#fff
    style Email fill:#FFFFFF,stroke:#666,stroke-dasharray: 5 5,color:#333
    style Internet fill:#fff,stroke:#333,color:#333
    style Timer fill:#fff,stroke:#333,color:#333

    %% Background Colors
    style Client fill:#ffffff,stroke:#e5e7eb,color:#333
    style Azure fill:#f9fafb,stroke:#d1d5db,color:#333
    style Apps fill:#f9fafb,stroke:none
    style Data fill:#f9fafb,stroke:none

```

This project utilizes a **cloud-native, serverless architecture** on Microsoft Azure to ensure scalability and cost-efficiency.

### **Core Components**
* **Automated Content Pipeline:** A daily C# Azure Function scrapes and normalizes data from multiple high-profile sources.
* **AI Classification Engine:** Integrated **Azure OpenAI** with custom prompt engineering to intelligently categorize articles.
* **Frontend:** A responsive **React (TypeScript)** dashboard hosted on Azure Static Web Apps.

---

## 🔐 Security Implementation
*As a security-focused tool, data integrity and access control were prioritized during development.*

* **Identity Management:** Implemented **Microsoft Entra ID** for robust user authentication and session management via MSAL.
* **API Security:** All 13 backend endpoints are secured with **JWT (JSON Web Token)** validation to prevent unauthorized access.
* **DDoS Mitigation:** Configured **Rate Limiting** (1,000 requests/minute) on the API Gateway to protect against denial-of-service attacks and abuse.

---

## 🛠️ Tech Stack

| Component | Technology | Reasoning |
| :--- | :--- | :--- |
| **Frontend** | React, TypeScript, Webpack | Type safety and component modularity for a scalable UI. |
| **Auth** | Microsoft Entra ID | Enterprise-grade identity management. |
| **Backend** | Node.js (Express), Azure Functions (C#) | Hybrid approach: Express for API proxying, C# for high-performance categorization and scraping jobs. |
| **Database** | Azure Cosmos DB (NoSQL) | Schemaless storage to handle varying article metadata structures. |
| **AI** | Azure OpenAI Service | Natural Language Processing for automated content tagging. |

---

## 🚀 Key Features
* **Smart Aggregation:** Consolidates news from 4+ trusted sources into a single feed.
* **Personalized Feeds:** Users can follow specific threat categories (e.g., *Cloud Security*, *Emerging Tech and AI Security*) to filter their dashboard.
* **Engagement Tools:** "Save for Later" functionality and email notifications for critical updates via **Azure Communication Services**.

---

## 🎨 Design
The original UI/UX flow was prototyped in Figma before implementation.
[**View Figma Prototype**](https://www.figma.com/proto/Vo0USUrtEzXWpz2gfd97fR/Project-Design?node-id=0-1&t=djtktjuiqusYH7wo-1)
