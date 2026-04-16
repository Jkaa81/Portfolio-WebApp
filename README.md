# HairWizard

HairWizard is an ASP.NET Core MVC web application for managing hair salon bookings.
It allows users to create, view, and manage appointments, as well as handle employees and treatments.

The application is containerized with Docker and deployed automatically using GitHub Actions to a cloud server (DigitalOcean).

---

## Features

* User authentication (ASP.NET Identity)
* Booking system for treatments
* Employee management
* Treatment management (e.g. haircut, styling)
* Lightweight SQLite database
* Automatic database migration on startup

---

## Tech Stack

* **Backend:** ASP.NET Core MVC (.NET 8)
* **Database:** SQLite + Entity Framework Core
* **Authentication:** ASP.NET Identity
* **Containerization:** Docker
* **CI/CD:** GitHub Actions
* **Hosting:** DigitalOcean (Ubuntu droplet)

---

## Local Setup

1. Clone the repository:

```bash
git clone https://github.com/your-username/RepoPortifolie.git
cd HairWizard
```

2. Run the application:

```bash
dotnet run
```

3. Open in browser:

```
https://localhost:xxxx
```

---

## Run with Docker

Build the image:

```bash
docker build -t hairwizard .
```

Run the container:

```bash
docker run -d \
  -p 8080:8080 \
  -v hairwizard_data:/app/data \
  -e ASPNETCORE_URLS=http://+:8080 \
  hairwizard
```

The application will be available at:

```
http://localhost:8080
```

---

## CI/CD & Deployment

The application is automatically deployed via GitHub Actions.

### Pipeline flow:

1. Build and test (.NET)
2. Build Docker image
3. Push to Docker Hub
4. Deploy via SSH to server

### Deployment process:

* Pull latest Docker image
* Stop existing container
* Start new container with updated image

---

### Database

* SQLite database (`hairwizards.db`)
* Stored in `/app/data` inside the container
* Persisted using a Docker volume
* Database is automatically created and updated at startup

---

### Secrets

The following secrets are used in GitHub Actions:

* `DO_SSH_KEY` → SSH access to server
* `DOCKERHUB_USERNAME`
* `DOCKERHUB_TOKEN`
* `DB_CONNECTION` → Connection string for database

---

# Considerations

* SQLite is used for simplicity and portability
* DataProtection keys are not persisted (can be improved for production)
* HTTPS is not yet configured

---

# Future Improvements

* HTTPS with Nginx + Let's Encrypt
* Switch to SQL Server or PostgreSQL
* Improved UI/UX
* Logging and monitoring

---

# About

This project was developed as part of my studies (currently 4th semester), focusing on:

* Full-stack development
* Building maintainable and scalable applications
* Containerization and deployment workflows

---

# What this project demonstrates

* ASP.NET Core MVC development
* Entity Framework Core with migrations
* Docker containerization
* CI/CD pipeline setup
* Cloud deployment and server management

---

# License

This project is intended for learning and demonstration purposes.
