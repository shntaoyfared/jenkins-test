# Jenkins Docker CI/CD Demo

A simple CI/CD project demonstrating how to automate Docker application deployment using Jenkins.

## Project Overview

This project uses a Jenkins Pipeline to:

1. Build a Docker image from the application source code.
2. Stop and remove any existing container.
3. Deploy a new container using the latest image.
4. Automate the deployment process through Jenkins.

The goal is to demonstrate core DevOps concepts such as Continuous Integration, Continuous Deployment, containerization, and automation. Jenkins is commonly used to automate build, test, and deployment workflows.

---

## Technologies Used

* Jenkins
* Docker
* Git & GitHub
* Linux
* Shell Scripting
* CI/CD Pipelines

---

## Project Structure

```text
.
├── Jenkinsfile
├── Dockerfile
├── app.py
├── requirements.txt
└── README.md
```

> Modify the structure above if your repository contains additional files.

---

## Jenkins Pipeline Workflow

### Build Stage

Builds a Docker image:

```bash
docker build -t shntaoyfared/flask_demo:latest .
```

### Stop Existing Container

Stops and removes the currently running container:

```bash
docker stop flask_demo || true
docker rm flask_demo || true
```

### Deploy Stage

Runs the latest Docker image:

```bash
docker run -d \
  --name flask_demo \
  -p 5000:5000 \
  shntaoyfared/flask_demo:latest
```

---

## Prerequisites

Before running this project, ensure you have:

* Docker installed
* Jenkins installed
* Git installed
* Docker permissions configured for Jenkins user

Verify installations:

```bash
docker --version
jenkins --version
git --version
```

---

## Running Locally

Clone the repository:

```bash
git clone https://github.com/shntaoyfared/jenkins-test.git
cd jenkins-test
```

Build the image:

```bash
docker build -t flask_demo .
```

Run the container:

```bash
docker run -d -p 5000:5000 flask_demo
```

Access the application:

```text
http://localhost:5000
```

---

## Jenkins Setup

1. Create a Pipeline Job in Jenkins.
2. Connect the GitHub repository.
3. Configure Pipeline Script from SCM.
4. Select Git.
5. Enter the repository URL.
6. Set the script path to:

```text
Jenkinsfile
```

7. Save and build the job.

---

## CI/CD Flow

```text
Developer Push
       │
       ▼
    GitHub
       │
       ▼
    Jenkins
       │
       ▼
 Build Docker Image
       │
       ▼
 Stop Old Container
       │
       ▼
 Deploy New Container
       │
       ▼
 Application Running
```



