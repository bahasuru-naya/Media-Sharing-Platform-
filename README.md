# Media Sharing Platform

[![Project Status: Active](https://img.shields.io/badge/Project%20Status-Active-brightgreen.svg)](https://github.com/bahasuru-naya/Media-Sharing-Platform-)
[![Distributed Systems](https://img.shields.io/badge/Course-CS4092%20Distributed%20Systems-blue.svg)](https://kdu.ac.lk/)

<img width="1912" height="861" alt="1" src="https://github.com/user-attachments/assets/23df2f9c-a3cd-48c3-8146-a7bcb6679ea0" />

A robust, event-driven distributed system designed for efficient media uploading, storage, and asynchronous processing. 

## 🚀 Overview

The **Media Sharing Platform** allows users to upload images and videos, which are then stored in cloud object storage. The system leverages an asynchronous architecture to process media (such as thumbnail generation) without blocking the user interface, ensuring a smooth and responsive experience.

## ✨ Key Features

- **Media Upload**: Support for image and video uploads with associated metadata (title, uploader).
- **Asynchronous Processing**: Automated thumbnail generation using worker functions (AWS Lambda).
- **Metadata Management**: Secure storage of media metadata with real-time status updates.
- **RESTful API**: Clean API endpoints for media retrieval, status checking, and management.
- **Cloud Native**: Built using AWS services for scalability and reliability.
- **Containerized**: Fully containerized using Docker and Docker Compose for consistent development and deployment.

## 🏗️ System Architecture

The platform follows an **Event-Driven Architecture** to handle high-volume media processing efficiently.

### Workflow
1. **Upload**: User uploads media via the UI/CLI.
2. **Object Storage**: The API stores the raw file in **Amazon S3**.
3. **Database Entry**: Metadata (filename, status, uploader) is saved in **Amazon DynamoDB**.
4. **Queuing**: The API sends a message to **Amazon SQS** to trigger processing.
5. **Processing**: An **AWS Lambda** worker consumes the message and generates a thumbnail.
6. **Update**: The worker updates the database status and stores the thumbnail in S3.
7. **Retrieval**: The user retrieves the list of media and processed results via the API.


## 🛠️ Technology Stack

| Component | Technology |
| :--- | :--- |
| **Backend** | Python (Flask) |
| **Frontend** | HTML5, CSS3, JavaScript (Vanilla) |
| **Object Storage** | Amazon S3 |
| **Database** | Amazon DynamoDB |
| **Message Queue** | Amazon SQS |
| **Serverless** | AWS Lambda |
| **Containerization** | Docker, Docker Compose |
| **Monitoring** | Amazon CloudWatch |

## 👨‍💻 My Role: Backend Developer

As the lead **Backend Developer** (PHDB Nayanakantha), I designed and implemented the core logic and data management layer of the platform. My contributions focused on creating a scalable and modular backend structure:

- **Service-Oriented Architecture**: Implemented a robust `MediaService` layer that encapsulates all business logic, ensuring a clean separation from the API and database layers.
- **Data Modeling & Validation**: Developed comprehensive data models using Python, including strict validation for media metadata (UUIDs, status states, file types).
- **Asynchronous Workflow**: Designed the integration with **Amazon SQS** and **AWS Lambda** to handle background tasks like thumbnail generation without blocking the main application flow.
- **Database Orchestration**: Implemented the interface for **Amazon DynamoDB**, including a local mock version for testing and development.
- **Reliability & Testing**: Built an automated simulation environment to verify end-to-end data flow, CRUD operations, and error handling.

For a detailed technical breakdown of the backend implementation, please see the [Backend README](backend/README.md).

## 📂 Project Structure

```text
.
├── backend/            # Flask API and core logic
│   ├── app/            # Application source code
│   ├── Dockerfile      # Backend container configuration
│   └── requirements.txt # Python dependencies
├── frontend/           # Web interface (HTML/CSS/JS)
│   ├── Dockerfile      # Frontend container configuration
│   └── nginx.conf      # Web server configuration
├── db/                 # Database initialization and scripts
├── docker-compose.yml  # Multi-container orchestration
└── README.md           # Project documentation
```

## ⚙️ Installation & Setup

### Prerequisites
- Docker & Docker Compose
- AWS Account (with S3, DynamoDB, SQS, and Lambda configured)
- AWS CLI configured with appropriate credentials

### Local Development
1. **Clone the repository:**
   ```bash
   git clone https://github.com/bahasuru-naya/Media-Sharing-Platform-.git
   cd Media-Sharing-Platform-
   ```

2. **Configure Environment Variables:**
   Create a `.env` file in the root directory based on `.env.example`.

3. **Run with Docker Compose:**
   ```bash
   docker-compose up --build
   ```

4. **Access the Application:**
   - Frontend: `http://localhost:8080`
   - Backend API: `http://localhost:5000`

## 👥 Team Members (Group A)

| Name | Role |
| :--- | :--- |
| **JARN Jayasinghe** | Project Lead / Integrator |
| **PHDB Nayanakantha** | **Backend Developer (Me)** |
| **L.K.D.H. Perera** | API Developer |
| **KKVRM Kalyanapriya** | Frontend / DevOps Specialist |
| **DMPT Dissanayake** | Worker / Processor Developer |
| **BDSD Douglas** | Database Administrator |

