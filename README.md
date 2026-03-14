# Docker Configurations

A collection of Docker Compose and Dockerfile configurations for self-hosted services. Each directory contains an independent, ready-to-deploy setup for a different service.

## Purpose

This repository serves as a central place to organize and version-control Docker configurations. Instead of scattering compose files and Dockerfiles across machines, everything lives here — making it easy to spin up services on any host.

## Repository Layout

```
.
├── README.md
├── <service-a>/
│   ├── docker-compose.yml
│   ├── Dockerfile          (if applicable)
│   ├── .env.example
│   └── ...
└── <service-b>/
    └── ...
```

Each directory is self-contained. Navigate into any folder, configure the environment, and run `docker compose up -d`.

## Prerequisites

- [Docker](https://docs.docker.com/get-docker/) (v20+)
- [Docker Compose](https://docs.docker.com/compose/install/) (v2+)

## Usage

```bash
cd <service-directory>
# configure environment variables
cp .env.example .env        # edit .env with your values
# start
docker compose up -d
# stop
docker compose down
# logs
docker compose logs -f
```

## Conventions

- **One directory per service** — keeps configs isolated and easy to manage.
- **Environment files** — use `.env` or `*.env` files for secrets; add them to `.gitignore` so credentials are never committed.
- **Volumes** — bind-mount data directories for persistence across container restarts.
- **Networks** — use named Docker networks when services need to talk to each other across compose files.
- **Image tags** — pin versions (e.g., `postgres:16`) in production instead of using `latest`.
