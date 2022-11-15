# Komplano Local Docker Development Environment

This is a local development environment for Komplano. It uses Docker to run the
application and its dependencies in containers.

## Requirements

- Docker
- Docker Compose

## Setup

1. Clone this repository `git clone --recursive https://github.com/codezeit/Komplano-Development.git`
2. Copy `.env.example` to `.env` and edit it to your needs
   ( right now we actually don't support any configuration directly in the
   `.env` file in this layer. But we'll add it in the future )
3. Run `docker-compose up -d` to start the containers or `docker-compose up` to
   start the containers and watch the logs
4. In the Browser go to https://localhost and accept the self-signed certificate

## Overview

The application is split into multiple containers:

| Container | Description | internal address | external address |
|-----------|-------------|------------------|------------------|
| [Client](https://github.com/codezeit/Komplano-Client) | The frontend of Komplano | http://client:4200 | http://localhost |
| [Server](https://github.com/codezeit/Komplano-Server) | The backend of Komplano | http://server:8000 | http://localhost/api |
| [Database](https://hub.docker.com/_/postgres) | The database of Komplano | postgres://postgres:postgres@database:5432/postgres | - |
| [nginx](https://hub.docker.com/_/nginx) | The reverse proxy for the frontend and backend | - | http://localhost |
