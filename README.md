# Docker Compose Setup

Centralized Docker Compose configuration for local services used by Skill-Wanderer.

## PostgreSQL (Main SQL Database)

This repository includes a pre-configured PostgreSQL service to provide a consistent development environment. Contributors can start working immediately without manual database installation.

### Key Features

- Engine: Official PostgreSQL image pinned to `postgres:16`.
- Persistence: Uses named volume `postgres_data` to preserve data between restarts.
- Reliability: Integrated `pg_isready` healthcheck.
- Customization: Fully controlled via `.env` file.
- Optional admin tool: Includes `dpage/pgadmin4:9` under the `admin` profile.

## Quick Start

### 1. Initialize Environment

Create your local `.env` file from the provided template:

```powershell
# Windows PowerShell
Copy-Item .env.example .env

# macOS / Linux / Git Bash
cp .env.example .env
```

### 2. Launch Services

Start PostgreSQL in detached mode:

```bash
docker compose up -d
```

### 3. Verify Health

Ensure the container status is `Up (healthy)`:

```bash
docker compose ps
```

## Service Catalog

| Service | Image | Host Port | Default Credentials | Description |
| --- | --- | --- | --- | --- |
| PostgreSQL | `postgres:16` | `5432` | See `.env` | Primary SQL storage |
| pgAdmin (`admin` profile) | `dpage/pgadmin4:9` | `5050` | See `.env` | Web GUI for database management |

Note: pgAdmin is disabled by default. To enable it, use the `admin` profile:

```bash
docker compose --profile admin up -d
```

When enabled, pgAdmin starts only after PostgreSQL is healthy and stores its state in `pgadmin_data`.

## Advanced Operations

### Stop Services

Stop containers while keeping data intact:

```bash
docker compose down
```

### Hard Reset (Delete All Data)

To wipe the database and start fresh (warning: this deletes all records):

```bash
docker compose down -v
docker compose up -d
```

## Troubleshooting

### Port 5432 already in use

Change `POSTGRES_PORT` in your `.env` (for example, `5433`) and restart:

```bash
docker compose down
docker compose up -d
```

### Authentication failed

If credentials were changed after the first launch, reset the volume so PostgreSQL re-initializes with new values:

```bash
docker compose down -v
docker compose up -d
```

### pgAdmin keeps restarting

Ensure `PGADMIN_DEFAULT_EMAIL` in `.env` is a valid email format (for example, `admin@skill-wanderer.dev`).

Maintained by Skill-Wanderer Team.