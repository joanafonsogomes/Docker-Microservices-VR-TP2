# Docker Microservices — Authentication & Access Control

**A containerized web application exploring microservices, JWT-based authentication, and role-based access control.**

Academic project developed during the *Network Virtualization* course at the University of Minho (2020/2021), as part of the Network Management and Virtualization specialization.

## Overview

This project explores the deployment and communication of multiple services using Docker and Docker Compose.

The application separates user authentication from HTTP content delivery, using JSON Web Tokens (JWT) to manage access to protected pages.

It includes two Node.js services and a MongoDB database, connected through dedicated Docker networks.

## Tech Stack

| Area | Technologies |
|---|---|
| Backend | JavaScript, Node.js, Express |
| Database | MongoDB, Mongoose |
| Authentication | JWT, RS256 |
| Frontend | Pug |
| Containerization | Docker, Docker Compose |
| Communication | HTTP, Cookies |

## Key Features

- **Containerized Services** — Separate authentication and HTTP services, configured using Docker Compose.
- **User Registration & Login** — User account creation and authentication with MongoDB persistence.
- **JWT Authentication** — Token generation and verification using asymmetric cryptography.
- **Role-Based Access Control** — Protected application pages for regular users and administrators.
- **Service Isolation** — Dedicated Docker networks controlling connectivity between services.
- **Persistent Storage** — Docker volumes for database data and HTTP access logs.

## Architecture

The application consists of three containerized services:

**Authentication Service (`auth`)**
- Handles user registration and login.
- Stores user information in MongoDB.
- Generates JWTs containing user identity and access level.

**HTTP Service (`http`)**
- Provides protected user and administrator pages.
- Validates JWTs before granting access.
- Records user access information in a persistent log.

**Database Service (`db`)**
- Uses MongoDB to store user records.
- Communicates with the authentication service through a dedicated Docker network.

## Docker Configuration

The `docker-compose.yml` file defines:

| Service | Container | Port |
|---|---|---|
| Authentication | `auth` | 4000 |
| HTTP Application | `http` | 4004 |
| Database | `mongodb` | Internal |

Two networks are configured:

- `network1` connects the authentication service to MongoDB.
- `network2` connects the authentication and HTTP services.

Docker volumes are used for persistent storage.

## Concepts Explored

- Microservice-based application architecture.
- Containerization and multi-container orchestration.
- Docker networking and service communication.
- Authentication using JSON Web Tokens.
- Role-based authorization.
- Database integration and persistent storage.

## Documentation

The original project documentation is available in [report.pdf](report.pdf).

## Project Context

Developed as an academic assignment at the University of Minho during the 2020/2021 academic year.

The repository preserves an educational implementation using historical dependencies and configuration. It is not intended for production deployment without security and dependency updates.
