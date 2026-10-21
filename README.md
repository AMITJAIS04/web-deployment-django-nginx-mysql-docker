# Deploying a Web Application Using Django, Nginx, and MySQL

## Project Overview

This project demonstrates the deployment of a Django web application using Docker, Docker Compose, Nginx, and MySQL on an AWS EC2 Ubuntu instance. Nginx acts as a reverse proxy, Gunicorn runs the Django application, and MySQL stores application data.

## Technologies Used

- AWS EC2
- Ubuntu Linux
- Docker
- Docker Compose
- Django
- Gunicorn
- Nginx
- MySQL
- Git and GitHub

## Architecture

The project consists of three main services:

1. **Nginx:** Receives incoming HTTP requests and forwards them to the Django application.
2. **Django:** Handles application logic and runs using Gunicorn.
3. **MySQL:** Stores application data in a database.

Docker Compose manages all three services and connects them through a shared Docker network.

## Docker Networking and Persistent Storage

- **Docker Network:** Created a custom Docker network named `notes-app` to enable communication between the Nginx, Django, and MySQL containers using their service names.

- **Persistent Storage:** Configured persistent storage for MySQL database files using a host directory mounted into the container. This helps preserve database data when containers are stopped, restarted, or recreated.

- **Container Management:** Used Docker Compose to build, configure, and manage all application services from a single configuration file.

## Project Structure

```text
django-notes-app/
├── nginx/
│   ├── Dockerfile
│   └── default.conf
├── notesapp/
├── manage.py
├── Dockerfile
├── docker-compose.yml
├── requirements.txt
├── .env
├── .gitignore
└── README.md
```

*Note: The exact directory structure may vary depending on the project files.*

## Deployment Steps

### 1. Clone the Repository

```bash
git clone https://github.com/AMITJAIS04/web-deployment-django-nginx-mysql-docker.git
cd web-deployment-django-nginx-mysql-docker
```

### 2. Configure Environment Variables

Configure the required environment variables in the `.env` file for Django and database connectivity.

Do not upload sensitive information such as passwords or Django secret keys to GitHub.

### 3. Build and Start Containers

```bash
docker compose up --build -d
```

### 4. Verify Container Status

```bash
docker compose ps
```

### 5. Check Application Logs

```bash
docker compose logs
```

To check individual services:

```bash
docker compose logs nginx
docker compose logs django
docker compose logs db
```

### 6. Access the Application

Open the following URL in your browser:

```text
http://YOUR-EC2-PUBLIC-IP
```

Replace `YOUR-EC2-PUBLIC-IP` with your EC2 instance's public IP address. Ensure inbound traffic on port 80 is allowed in the EC2 security group and Nginx is configured to forward requests to Django.

## Useful Docker Commands

Check running containers:

```bash
docker ps
```

Stop the application:

```bash
docker compose down
```

Rebuild and start the application:

```bash
docker compose up --build -d
```

View live logs:

```bash
docker compose logs -f
```

## Key Learnings

- Deployed a Django web application using Docker and Docker Compose.
- Configured Nginx as a reverse proxy for the Django application.
- Used Gunicorn to run the Django application.
- Integrated Django with a MySQL database.
- Created a custom Docker network for container-to-container communication.
- Configured persistent storage to retain database data across container restarts and recreation.
- Deployed the application on AWS EC2 Ubuntu.
- Managed project source code using Git and GitHub.

## Future Improvements

- Configure HTTPS using SSL/TLS certificates.
- Implement a CI/CD pipeline using GitHub Actions.
- Improve secrets management and application security.
- Configure regular database backups and monitoring.
