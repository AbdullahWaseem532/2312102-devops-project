# DevOps Final Project (2312102)

**Student ID:** 2312102
**Course:** DevOps Fundamentals (BSCS 6th Semester)

## Project Overview

This project is a simple student management API built using FastAPI and PostgreSQL. The application is containerized using Docker and deployed on AWS EC2. GitHub Actions is used to automate testing and deployment.

## Project Architecture

```text
GitHub Repository
       |
       | Push Code
       v
GitHub Actions
   |       |
   |       ├── Run flake8
   |       └── Run pytest
   |
   v
AWS EC2 Server
   |
   └── Docker Compose
          ├── FastAPI App
          └── PostgreSQL Database
```

### Services Used

* **web** → FastAPI application running on port 8000
* **db** → PostgreSQL database with persistent storage

---

## Local Setup

### Requirements

* Python 3.12
* Docker
* Docker Compose

### Steps

Clone the repository:

```bash
git clone https://github.com/YOUR_USERNAME/2312102-devops-project.git
cd 2312102-devops-project
```

Create the environment file:

```bash
cp .env.example .env
```

Update the values inside `.env` according to your setup.

Start the application:

```bash
docker compose up --build
```

Test the API:

```bash
curl http://localhost:8000/health
curl http://localhost:8000/students
```

---

## API Endpoints

### Health Check

```http
GET /health
```

Returns application and database status.

### Create Student

```http
POST /students
```

Creates a new student record.

### Get All Students

```http
GET /students
```

Returns all student records.

### Get Student by Registration Number

```http
GET /students/{reg_no}
```

Returns a specific student record.

---

## Deployment on AWS EC2

Connect to the EC2 instance:

```bash
ssh -i your-key.pem ubuntu@YOUR_EC2_IP
```

Install Docker:

```bash
sudo apt update
sudo apt install -y docker.io docker-compose-plugin
sudo usermod -aG docker ubuntu
```

Clone the project:

```bash
git clone https://github.com/YOUR_USERNAME/2312102-devops-project.git
cd 2312102-devops-project
```

Create environment file:

```bash
cp .env.example .env
```

Run the application:

```bash
docker compose -f docker-compose.prod.yml up -d --build
```

---

## GitHub Secrets

The following secrets are required for automatic deployment:

* `EC2_HOST` – Public IP of EC2 instance
* `EC2_SSH_KEY` – Contents of the EC2 private key (.pem file)

---

## Running Tests

Install dependencies:

```bash
pip install -r requirements.txt
```

Run tests:

```bash
pytest app/tests/ -v
```

---

## Live Application

```text
http://YOUR_EC2_IP:8000
```

---

## Submitted By

**Student ID:** 2312102
**Course:** DevOps Fundamentals
**Semester:** BSCS 6th Semester

