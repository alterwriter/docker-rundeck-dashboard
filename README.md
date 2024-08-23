# Rundeck Automation Dashboard with PostgreSQL Integration

![rundeck-gh-image](https://github.com/user-attachments/assets/2ddc1f8f-1ef4-4191-b733-5fe2e572d118)

## Overview

This project sets up a fully automated Rundeck dashboard, integrated with PostgreSQL, using Docker Compose. It supports both local development and production environments. The project includes predefined environment variables for seamless integration and easy deployment.

## Features

- **Rundeck Integration:** Automated task scheduling, job orchestration, and execution using Rundeck.
- **PostgreSQL Database:** Secure and efficient data management for Rundeck.
- **Environment-Specific Configurations:** Separate setups for local and production environments.
- **Volume Management:** Persistent data storage for Rundeck and PostgreSQL.
- **Customizable via Environment Variables:** Flexible configuration through `.env` files.

## Prerequisites

- Docker
- Docker Compose
- Git

## Local Setup

To run Rundeck locally, clone the repository and use Docker Compose:

```bash
git clone https://github.com/alterwriter/docker-rundeck-dashboard.git
cd docker-rundeck-dashboard
docker-compose -f local-docker-compose up -d --build
```

### Environment Variables for Local Setup

Create a `.env` file in the project root with the following variables:

```env
RUNDECK_GRAILS_URL=http://localhost:4440
RUNDECK_DATABASE_DRIVER=org.postgresql.Driver
RUNDECK_DATABASE_USERNAME=rundeckuser
RUNDECK_DATABASE_PASSWORD=rundeckpassword
RUNDECK_DATABASE_URL=jdbc:postgresql://postgres:5432/rundeckdb
RUNDECK_SERVER_ADDRESS=localhost
RUNDECK_FEATURE_UINEXT_NAME=NewUI
RUNDECK_FEATURE_UINEXT_ENABLED=true
RUNDECK_ADMIN_USERNAME=admin
RUNDECK_ADMIN_PASSWORD=adminpassword
POSTGRES_DB=rundeckdb
POSTGRES_USER=rundeckuser
POSTGRES_PASSWORD=rundeckpassword
```

## Production Setup

For production, the setup is defined in the `docker-compose.yml` file with specific environment variables tailored for a secure deployment.

### Production Environment Variables

Set up your production environment variables in your own CI/CD platform.

```env
RUNDECK_GRAILS_URL=https://your-production-domain.com
RUNDECK_DATABASE_DRIVER=org.postgresql.Driver
RUNDECK_DATABASE_USERNAME_PRODUCTION=prod_rundeckuser
RUNDECK_DATABASE_PASSWORD_PRODUCTION=prod_rundeckpassword
RUNDECK_DATABASE_URL=jdbc:postgresql://your-production-db-url:5432/prodrundeckdb
RUNDECK_SERVER_ADDRESS=your-production-domain.com
RUNDECK_FEATURE_UINEXT_NAME=NewUI
RUNDECK_FEATURE_UINEXT_ENABLED=true
RUNDECK_ADMIN_USERNAME_PRODUCTION=prod_admin
RUNDECK_ADMIN_PASSWORD_PRODUCTION=prod_adminpassword
POSTGRES_DB=prodrundeckdb
POSTGRES_USER_PRODUCTION=prod_rundeckuser
POSTGRES_PASSWORD_PRODUCTION=prod_rundeckpassword
```

### Deploying to Production

To deploy to a production server:

1. Set up the environment variables.
2. Build and start the containers:

```bash
docker-compose --env-file .env.production -f docker-compose.yaml up -d --build
```

## Volumes

- **dbdata:** Persistent storage for PostgreSQL.
- **rundeck_data:** Persistent storage for Rundeck data.
- **rundeck_config:** Persistent storage for Rundeck configuration.

## License

This project is open-source and available under the [MIT License](./LICENSE).

## Contributing

Contributions are welcome! Please submit a pull request or open an issue to discuss any changes.
