---
layout: post
title: "FlashField: Citizen Science Platform for Micro-Experiments"
date: 2025-03-28
author: "Fara Rahmasari Fahirun"
categories: [Web Development, Software Engineering, System Design]
tags: [Python, FastAPI, React.js, PostgreSQL, GIS, TailwindCSS, Docker]
image: /assets/img/flashfield.png
---

## **Project Description**

FlashField is a comprehensive web-based "Citizen Science" platform designed to democratize scientific data collection. The core philosophy of the project is *"Science for everyone — starting from around you."*

In the academic and research world, gathering geographically distributed data (e.g., tracking invasive plant species, monitoring local weather anomalies, or urban noise mapping) is often logistically expensive and time-consuming. FlashField addresses this by creating a bridge between **Researchers**, who define "micro-experiments," and **Volunteers**, who contribute data from their local environments.

Unlike static survey tools, FlashField is built as a robust, location-aware system featuring **dynamic input configuration**, allowing researchers to define custom data structures (numbers, text, weather, dates) that render instantaneously on the volunteer's interface. The platform includes real-time geospatial visualization (heatmaps) and statistical dashboards.

## **My Role & Contribution**

As a Full Stack Developer for this project (developed for the Advanced Web Programming course), I engineered the end-to-end architecture:

* **System Architecture Design:** I designed the relational database schema to handle dynamic field definitions and spatial data efficiently.
* **Backend Development (FastAPI):** I built a high-performance RESTful API using Python's FastAPI. This involved implementing JWT authentication, role-based access control (RBAC), and complex CRUD operations for experiment management.
* **Frontend Development (React):** I developed a responsive Single Page Application (SPA) using React 18 and Vite. I focused on creating a dynamic form renderer that adapts to the researcher's configuration and integrated **Leaflet** for interactive map visualizations.
* **Database Management:** I implemented the data layer using PostgreSQL and SQLAlchemy, optimizing queries for retrieving aggregated experiment statistics.

## **Technical Architecture**

### **The Stack**
I chose a modern, performance-oriented stack to ensure scalability and developer experience:

* **Backend:** Python 3.11+, **FastAPI** (for high-concurrency async support), **SQLAlchemy** (ORM), **Pydantic** (Data Validation).
* **Frontend:** **React 18**, **Vite**, **TailwindCSS** (Styling), **Leaflet** (Maps), **Chart.js** (Data Viz), **Axios**.
* **Database:** **PostgreSQL** (chosen for its robustness and potential for PostGIS extensions).
* **Auth:** OAuth2 with Password Flow (Bearer JWT), Passlib (Bcrypt hashing).

### **Core Features Implementation**

1.  **Dynamic Form Engine:**
    * *Challenge:* Researchers need different data types for different experiments (e.g., temperature vs. species count).
    * *Solution:* I implemented a JSON-based schema in the database. When a researcher creates an experiment, they define `input_fields` (type, label, required, min/max). The Frontend reads this configuration and dynamically renders the appropriate HTML inputs (Select, Radio, Number, Textarea) at runtime.

2.  **Geospatial Data Collection:**
    * When a volunteer submits an observation, the application leverages the browser's Geolocation API to capture high-precision GPS coordinates (`geo_lat`, `geo_lng`).
    * These points are visualized on the Researcher Dashboard using Leaflet, allowing for the identification of spatial clusters or distribution patterns.

3.  **Role-Based Access Control (RBAC):**
    * **Volunteers:** Can browse active experiments and submit data.
    * **Researchers:** Can create experiments, configure input fields, and view analytics/heatmaps.
    * **Admins:** Have global oversight for user management and system integrity.

## **Database Design**

The database schema was designed to enforce referential integrity while allowing flexibility for the dynamic inputs.

* **Users:** Stores credentials and roles.
* **Experiments:** Stores metadata (title, deadline) and the critical `input_fields` JSON structure.
* **Submissions:** Links Users to Experiments. It stores the location data and the actual `data_json` payload containing the volunteer's answers.
* **Audit_Logs:** Tracks critical system actions for security and accountability.

## **Results & Features**

The final deployed system successfully demonstrated the following capabilities:

* **Interactive Dashboards:** Researchers can view submission trends over time via line charts and spatial distribution via interactive maps.
* **Secure Authentication:** Complete registration and login flows with secure token handling.
* **Data Integrity:** Pydantic models ensure that data submitted by volunteers matches the strict constraints defined by the researcher (e.g., preventing a user from entering text in a numeric temperature field).

| Feature Component | Implementation Details |
| :--- | :--- |
| **API Performance** | Sub-millisecond response times for read operations using FastAPI's async capabilities. |
| **Security** | Hashed passwords (Bcrypt) and stateless JWT authentication. |
| **UX/UI** | Mobile-first design ensures volunteers can submit data easily from the field. |


## **Future Work**

To evolve FlashField from an academic project to a production-ready SaaS product, the following features are planned:

1.  **PostGIS Integration:** Migrating raw lat/long columns to PostGIS geometry types to enable advanced spatial queries (e.g., "Find all submissions within a 5km radius of a landmark").
2.  **Offline Support (PWA):** Converting the frontend into a Progressive Web App to allow volunteers to collect data in remote areas without internet, syncing when a connection is restored.
3.  **Media Attachments:** Extending the backend to support image and audio file uploads via AWS S3 or MinIO, which is crucial for biological verifications.

## **Conclusion**

FlashField demonstrates the power of combining modern Python async web frameworks with reactive frontends to solve complex data collection problems. It successfully simplifies the workflow for researchers while providing an engaging experience for citizen scientists, bridging the gap between academic research and community participation.

**Repository:** [View on GitHub](https://github.com/abijaksana96/FlashField)