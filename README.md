# Dockerized Node.js Microservices

## Overview

This project containerizes four Node.js microservices using Docker and Docker Compose. The services communicate over a shared Docker bridge network.

## Architecture

- User Service: port 3000
- Product Service: port 3001
- Order Service: port 3002
- Gateway Service: port 3003

## Prerequisites

- Docker Desktop
- Docker Compose
- Git

## Project Structure

```text
Microservices-Task-main/
├── Microservices/
│   ├── user-service/
│   │   ├── Dockerfile
│   │   ├── app.js
│   │   └── package.json
│   ├── product-service/
│   │   ├── Dockerfile
│   │   ├── app.js
│   │   └── package.json
│   ├── order-service/
│   │   ├── Dockerfile
│   │   ├── app.js
│   │   └── package.json
│   └── gateway-service/
│       ├── Dockerfile
│       ├── app.js
│       └── package.json
├── docker-compose.yml
├── README.md
```

## Setup and Execution

1. Install and start Docker Desktop.
2. create and write the docker file for each microservice and a "docker.yaml" file in the root
3. Open a terminal in the project root.
4. Validate the Compose configuration:

   ```bash
   docker compose config
   ```

5. Build the service images:

   ```bash
   docker compose build
   ```

6. Start all services:

   ```bash
   docker compose up -d
   ```

7. Check container status:

   ```bash
   docker compose ps
   ```

## Testing Endpoints

| Service | Endpoint |
|---|---|
| User | http://localhost:3000/users |
| Product | http://localhost:3001/products |
| Order | http://localhost:3002/orders |
| Gateway health | http://localhost:3003/health |
| Gateway users | http://localhost:3003/api/users |
| Gateway products | http://localhost:3003/api/products |
| Gateway orders | http://localhost:3003/api/orders |

## Troubleshooting

- **Port already in use:** Stop the conflicting application or change the host port mapping in `docker-compose.yml`.
- **Build errors:** Verify that each service has a Dockerfile, `app.js`, and `package.json`.
- **Container exits:** Inspect logs with `docker compose logs <service-name>`.
- **Gateway returns an error:** Check that all backend containers are running and that the gateway uses the correct Compose service names and internal ports.
- **Changes are not reflected:** Rebuild and restart using `docker compose up -d --build`.

## Screenshots

<img width="1632" height="726" alt="Screenshot 2026-10-17 201159" src="https://github.com/user-attachments/assets/8b853a63-9880-4776-921f-86a7e3493a61" />

<img width="1827" height="585" alt="Screenshot 2026-10-17 201220" src="https://github.com/user-attachments/assets/8233b74b-1307-41f2-93a4-a38509d3496e" />

<img width="1917" height="1078" alt="Screenshot 2026-10-17 201259" src="https://github.com/user-attachments/assets/43e7f530-ea1e-4bcb-90c1-018cef35d61f" />

<img width="1917" height="1078" alt="image" src="https://github.com/user-attachments/assets/a0d66d71-e215-4f48-b14d-c6990a40fd7a" />

<img width="1917" height="1078" alt="image" src="https://github.com/user-attachments/assets/32e148de-500c-443b-9c1a-dd2d5a54f232" />

<img width="1917" height="1078" alt="image" src="https://github.com/user-attachments/assets/7c0ef5ef-006f-4add-b965-c8d0037a7dc8" />

<img width="1917" height="1078" alt="image" src="https://github.com/user-attachments/assets/8e2c3ab3-3f25-464a-89fa-37a3cd1774bc" />


## Cleanup

Stop and remove the containers and network:

```bash
docker compose down
```

## Conclusion

The application is containerized using individual Dockerfiles and orchestrated using Docker Compose. The shared network enables communication between the gateway and the backend services.
