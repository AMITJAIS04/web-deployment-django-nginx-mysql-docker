# Deploying a Web Application Using Django, Nginx, and MySQL

## Project Overview

This project demonstrates the deployment of a Django web application using Docker and Docker Compose on an AWS EC2 Ubuntu instance. Nginx acts as a reverse proxy, Django runs the application using Gunicorn, and MySQL is used as the database.

The purpose of this project is to practice containerization, multi-container deployment, reverse proxy configuration, and basic cloud deployment.

## Technologies Used

- **AWS EC2** – Hosts the application
- **Docker** – Containerizes the application
- **Docker Compose** – Manages multiple containers
- **Django** – Python web application framework
- **Gunicorn** – WSGI application server
- **Nginx** – Web server and reverse proxy
- **MySQL** – Database
- **Ubuntu Linux** – Server operating system
- **Git & GitHub** – Version control and source code management

## Architecture

The project consists of three main services:

1. **Nginx:** Receives incoming HTTP requests and forwards them to the Django application.
2. **Django:** Runs the application using Gunicorn and handles application logic.
3. **MySQL:** Stores application data persistently using a mounted volume.

Docker Compose manages the services and connects them through a shared Docker network.

## Project Structure

```text
django-notes-app/
├── nginx/
│   ├── Dockerfile
│   └── default.conf
├── manage.py
├── notesapp/
├── Dockerfile
├── docker-compose.yml
├── requirements.txt
├── .env
├── .gitignore
└── README.md
```

*Note: The exact files and directories may vary depending on your project.*

## Prerequisites

- An AWS EC2 instance running Ubuntu
- Docker installed
- Docker Compose plugin installed
- Git installed
- AWS security group configured to allow the required application traffic

## Deployment Steps

### 1. Clone the Repository

```bash
git clone https://github.com/AMITJAIS04/web-deployment-django-nginx-mysql-docker.git
cd web-deployment-django-nginx-mysql-docker
```

### 2. Configure Environment Variables

Create or update the `.env` file with the environment variables required by your Django application and database configuration.

**Important:** Do not upload passwords, secret keys, or other sensitive information to GitHub.

### 3. Build and Start the Containers

```bash
docker compose up --build -d
```

### 4. Check Container Status

```bash
docker compose ps
```

### 5. View Application Logs

```bash
docker compose logs
```

To check logs for an individual service:

```bash
docker compose logs django
docker compose logs nginx
docker compose logs db
```

### 6. Access the Application

Open the following URL in your browser:

```text
http://YOUR-EC2-PUBLIC-IP
```

Replace `YOUR-EC2-PUBLIC-IP` with your EC2 instance's public IP address. Ensure the Nginx service is configured correctly and inbound HTTP traffic on port 80 is allowed by the EC2 security group.

## Useful Docker Commands

Check running containers:

```bash
docker ps
```

Stop the application:

```bash
docker compose down
```

Rebuild and restart the application:

```bash
docker compose up --build -d
```

Follow application logs:

```bash
docker compose logs -f
```

## Key Learnings

- Containerizing a Django web application using Docker
- Managing multiple services using Docker Compose
- Configuring Nginx as a reverse proxy
- Running Django with Gunicorn
- Connecting Django to a MySQL database
- Using Docker networks and persistent volumes
- Deploying an application on AWS EC2
- Managing source code using Git and GitHub

## Future Improvements

- Configure HTTPS using SSL/TLS certificates
- Improve secret management using environment variables and secure storage
- Add health checks and service readiness dependencies
- Implement a CI/CD pipeline using GitHub Actions

## Author

**Amit Jaiswar**

GitHub: [AMITJAIS04](https://github.com/AMITJAIS04)

LinkedIn: [Connect with me](https://www.linkedin.com/in/amit-jais04)
