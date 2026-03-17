# Docker Compose Setup

Simplified local Docker Compose setup for Skill-Wanderer contributors.

## What Is Included

- PostgreSQL only (no pgAdmin in this repository).
- Official image pinned to `postgres:16`.
- Persistent volume `postgres_data`.
- Built-in `pg_isready` healthcheck.
- No `.env` file required.
- Placeholder credentials are included for local development (`change_me`).

## Folder Structure

- Compose file location: `postgreSQL/docker-compose.yml`

## Quick Start

### 1. Start PostgreSQL

```bash
cd postgreSQL
docker compose up -d
```

### 2. Verify Status

```bash
docker compose ps
```

### 3. Connection Info

- Host: `localhost`
- Port: `5432`
- Database: `skill_wanderer`
- Username: `skill_wanderer`
- Password: `change_me`

## Advanced Operations

### Stop Services

```bash
docker compose down
```

### Hard Reset (Delete All Data)

```bash
docker compose down -v
docker compose up -d
```

## Notes

- Contributors can use any preferred client (for example, DBeaver, pgAdmin Desktop, TablePlus, or psql).
- `change_me` is a local placeholder only and must be changed for any non-local or shared environment.

Maintained by Skill-Wanderer Team.