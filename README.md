# Fullstack Dockerized App: Angular 10 + Spring Boot + MySQL + Redis

This project is a containerized full-stack web application using:

- **Angular** as the frontend (served via Nginx)
- **Spring Boot (JPA + Redis)** as the backend
- **MySQL** as the relational database
- **Redis** for caching
- **Docker Compose** to orchestrate all services

yml

---
## Services Overview

### 1. **Angular Frontend**
- Docker Image: `motidocker1994/angular-client`
- Serves on port `4200`

### 2. **Spring Boot Backend**
- Docker Image: `motidocker1994/employee-management`
- REST API served on port `8088`
- Connects to MySQL and Redis

### 3. **MySQL Database**
- Image: `mysql:8.0`
- DB Name: `employee_management_system`

### 4. **Redis Cache**
- Image: `redis:7.0-alpine`
- Used for caching in Spring Boot app

---

## Prerequisites
- Docker
- Docker Compose
## How to Run the Application

### 1. Clone the Repository
git clone https://github.com/motikumar1994/sb-docker-fullstack-app.git
cd sb-docker-fullstack-app/docker-compose

Start All Services:-
docker-compose up --build

Access the Application:-
Frontend: http://localhost:4200
Backend API: http://localhost:8088/api/v1/employees

