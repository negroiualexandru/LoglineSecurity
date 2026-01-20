# Logline Security

**Live Demo URL:** https://jolly-field-07b6e4f1e.2.azurestaticapps.net/
 * *Due to a limitation of my free tier of the server hosting platform I am using, there might be a up to 1 min "wake up" time for my server on your first request.*
---

## About The Project

Logline Security is a personalized cybersecurity news aggregator, designed as a Minimum Viable Product (MVP) to serve security professionals, students, and enthusiasts.

Its core value is to save users time by consolidating news from trusted sources into a single, intelligent platform, providing a customized Cybersecurity news feed.

*Currently optimized for Desktop, mobile access will still work but will have some minor visual bugs.*

### Core Features:

* **Automated Content Pipeline:** A daily, serverless function scrapes articles from multiple high-profile news sites, uses the Azure OpenAI service to intelligently categorize them, and curates a list of top "featured" stories.
* **Personalized Dashboard:** After a secure login using Microsoft Entra ID, users can check categories they want to follow allowing them to filter their dashbard for those categories
* **User Engagement Tools:** The app includes essential features like the ability to save favorite articles for later reading, a robust search function, and opt-in email notifications for new content in followed categories.

---

## Tech Stack

This project is a full-stack web application built with a modern, cloud-native architecture on Microsoft Azure.

### Front-End (Client)

* **Framework:** React with TypeScript
* **Build Tool:** Webpack
* **Authentication:** Microsoft Entra ID (via MSAL React)
* **Hosting:** Azure Static Web Apps

### Back-End (Server & API)

* **API Proxy:** Node.js with Express
* **Hosting:** Render Free Tier
    * *Note: After 15 minutes of inactivity the server will sleep. The next request will have to "wake up" the server, causing a loading time of up to 1 min*
* **Serverless Functions:** Azure Functions (C#)
* **Database:** Azure Cosmos DB (NoSQL)
* **AI & Machine Learning:** Azure OpenAI Service
* **API Gateway:** Azure API Management
* **Email Notifications:** Azure Communication Services

---

## Original Design
* The original design (much different from final design) was created on Figma and is under this link: https://www.figma.com/proto/Vo0USUrtEzXWpz2gfd97fR/Project-Design?node-id=0-1&t=djtktjuiqusYH7wo-1
* Please note that not all button will work on every page of this design demo, to see which buttons are active, click somewhere on the demo and the buttons will highlight
*The source code for this project is in a private repository.*
