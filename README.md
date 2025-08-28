# Logline Security

**Live Demo URL:** [https://jolly-field-07b6e4f1e.azurestaticapps.net/](https://jolly-field-07b6e4f1e.azurestaticapps.net/)

---

## About The Project

Logline Security is a personalized cybersecurity news aggregator, designed as a Minimum Viable Product (MVP) to serve security professionals, students, and enthusiasts.

Its core value is to save users time by consolidating news from trusted sources into a single, intelligent platform, providing a customized and relevant threat intelligence feed.

*Currently optimized for Desktop, mobile access will still work but will have some minor visual bugs.*

### Core Features:

* **Automated Content Pipeline:** A daily, serverless function scrapes articles from multiple high-profile news sites, uses the Azure OpenAI service to intelligently categorize them, and curates a list of top "featured" stories.
* **Personalized Dashboard:** After a secure login using Microsoft Entra ID, users can check categories they want to follow allowing them to filter their dashbard for those categories
* **User Engagement Tools:** The app includes essential features like the ability to save favorite articles for later reading, a robust search function, and opt-in email notifications for new content in followed categories.

---

## Tech Stack

This project is a full-stack application built with a modern, cloud-native architecture on Microsoft Azure.

### Front-End (Client)

* **Framework:** React with TypeScript
* **Build Tool:** Webpack
* **Authentication:** Microsoft Entra ID (via MSAL React)
* **Hosting:** Azure Static Web Apps

### Back-End (Server & API)

* **API Proxy:** Node.js with Express
* **Hosting:** Render Free Tier
    * *Note: After 15 minutes of inactivity the server will sleep. The next request will have to "wake up" the server, causing a loading time of 1 to 2 minutes for the first request*
* **Serverless Functions:** Azure Functions (C#)
* **Database:** Azure Cosmos DB (NoSQL)
* **AI & Machine Learning:** Azure OpenAI Service
* **API Gateway:** Azure API Management
* **Email Notifications:** Azure Communication Services

---

*The source code for this project is in a private repository.*
