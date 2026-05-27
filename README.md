# WorkOS — two Laravel apps (SQLite) with Docker Compose

Mono-repo with **`app1`** and **`app2`**, each running Laravel **13** with **SQLite only** (database files `database/app1.sqlite` and `database/app2.sqlite`). No MySQL/Postgres containers.

## Requirements

- Docker Desktop (or Docker Engine + Compose v2)

## URLs

After `docker compose up --build`:

- **App 1**: [http://localhost:8001](http://localhost:8001)
- **App 2**: [http://localhost:8002](http://localhost:8002)

## Usage

From this directory:

```bash
docker compose up --build
```

Each service runs `composer install` on startup (mounted code + `vendor` from your machine), then `php artisan serve` on port 8000 inside the container.

## Running without Docker

```bash
cd app1 && php artisan serve --port=8001
cd app2 && php artisan serve --port=8002
```

Use the SQLite paths set in each app’s `.env` (`DB_CONNECTION=sqlite`, `DB_DATABASE=database/app1.sqlite` / `database/app2.sqlite`).
