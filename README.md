# fastapi-gino-postgres
High-performance Async REST API, in Python. FastAPI + GINO + Uvicorn + PostgreSQL.

## Get Started
### Run Locally
1. Clone this Repository. `git clone https://github.com/leosussan/fastapi-gino-postgres.git`
2. Run `pipenv install` from root. (Run `pip install pipenv` first, if necessary.)
3. Rename `.dist.env` to `.env`. Fill in PostgreSQL connection vars.
4. Generate DB Migrations: `alembic revision --autogenerate`. It will be applied when the application starts. You can trigger manually with `alembic upgrade head`.
5. Run locally with `python app/main.py`, or with the included Dockerfile / Docker-Compose file.

### Run Locally with Docker-Compose
1. Clone this Repository. `git clone https://github.com/leosussan/fastapi-gino-postgres.git`
2. Generate a DB Migration: `alembic revision --autogenerate`.*
3. Run locally using docker-compose. `docker-compose -f docker-compose.local.yml -f docker-compose.yml up --build`.

*`app/settings/prestart.sh` will run migrations for you before the app starts.

### Build Your Application
* Create routes in `/app/routes`, import & add them to the `ROUTERS` constant in  `/app/main.py`
* Create database models to `/app/models/orm`, add them to `/app/models/orm/migrations/env.py` for migrations
* Create pydantic models in `/app/models/pydantic`
* Store complex db queries in `/app/models/orm/queries`
* Add / edit globals to `/.env`, expose & import them from `/app/settings/globals.py`
* Define code to run before launch (migrations, setup, etc) in `/app/settings/prestart.sh`

## Features
### Core Dependencies
* **FastAPI:** touts performance on-par with NodeJS & Go + automatic Swagger + ReDoc generation. 
* **GINO:** built on SQLAlchemy core. Lightweight, simple, asynchronous ORM for PostgreSQL.
* **Uvicorn:** Lightning-fast, asynchronous ASGI server.
* **PostgreSQL:** Robust, fully-featured, scalable, open-source.
* **Optimized Dockerfile:** Optimized Dockerfile for ASGI applications, from https://github.com/tiangolo/uvicorn-gunicorn-docker.

#### Additional Dependencies
* **Pydantic:** Core to FastAPI. Define how data should be in pure, canonical python; validate it with pydantic. 
* **Alembic:** Handles database migrations. Compatible with GINO.
* **SQLAlchemy_Utils:** Provides essential handles & datatypes. Compatible with GINO.
