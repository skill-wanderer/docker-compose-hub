# PostgreSQL (Docker Compose)

This folder runs PostgreSQL using Docker Compose with a persistent external Docker volume.

## What is configured

- PostgreSQL image: `postgres:18`
- Persistent data volume: external Docker volume `postgres_data`
- No healthcheck (removed)

## Windows setup (PowerShell)

1. Open PowerShell and move to this folder:

```powershell
Set-Location .\postgreSQL
```

2. Create external volume one time:

```powershell
docker volume create postgres_data
```

3. Start PostgreSQL:

```powershell
docker compose -f .\docker-compose.yml up -d
```

4. Check running containers:

```powershell
docker compose -f .\docker-compose.yml ps
```

5. View logs:

```powershell
docker compose -f .\docker-compose.yml logs -f postgres
```

6. Stop containers:

```powershell
docker compose -f .\docker-compose.yml down
```

7. (Optional) Remove container and delete volume:

```powershell
docker compose -f .\docker-compose.yml down -v
```

## Linux setup (bash/zsh)

1. Open terminal and move to this folder:

```bash
cd ./postgreSQL
```

2. Create external volume one time:

```bash
docker volume create postgres_data
```

3. Start PostgreSQL:

```bash
docker compose -f ./docker-compose.yml up -d
```

4. Check running containers:

```bash
docker compose -f ./docker-compose.yml ps
```

5. View logs:

```bash
docker compose -f ./docker-compose.yml logs -f postgres
```

6. Stop containers:

```bash
docker compose -f ./docker-compose.yml down
```

7. (Optional) Remove container and delete volume:

```bash
docker compose -f ./docker-compose.yml down -v
```

## macOS setup (zsh/bash)

1. Open terminal and move to this folder:

```bash
cd ./postgreSQL
```

2. Create external volume one time:

```bash
docker volume create postgres_data
```

3. Start PostgreSQL:

```bash
docker compose -f ./docker-compose.yml up -d
```

4. Check running containers:

```bash
docker compose -f ./docker-compose.yml ps
```

5. View logs:

```bash
docker compose -f ./docker-compose.yml logs -f postgres
```

6. Stop containers:

```bash
docker compose -f ./docker-compose.yml down
```

7. (Optional) Remove container and delete volume:

```bash
docker compose -f ./docker-compose.yml down -v
```

## Notes

- Data is stored in Docker volume `postgres_data`, so it persists across container restarts and recreations.
- Current default credentials are set directly in `docker-compose.yml`.
- Change `POSTGRES_PASSWORD` before sharing or using beyond local development.
