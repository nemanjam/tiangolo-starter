# Tiangolo starter

## Installation and running

### In Docker

Frontend: http://localhost:5173

Backend: http://localhost:8000

#### Important: 

For `print()` logs must look **in backend Docker logs, not in terminal**.

```bash
docker compose watch
```

### Local

```bash
docker compose stop frontend

cd frontend
npm run dev

docker compose stop backend

cd backend
fastapi dev app/main.py
```

#### Migrate database

`docker compose watch` runs it by default.

```yaml
# docker-compose.yml

  prestart:
    depends_on:
      db:
        condition: service_healthy
        restart: true
    command: bash scripts/prestart.sh
```

Manually:

```bash
docker compose exec backend bash
alembic upgrade head

# or
docker compose exec backend bash alembic upgrade head
```
