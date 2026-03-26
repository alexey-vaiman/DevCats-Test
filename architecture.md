# System Architecture

## Overview
Приложение состоит из backend, frontend, storage, database и инфраструктурного слоя.

---

## Backend Structure
/backend
  /app
    /api        # FastAPI routes
    /services   # Business logic
    /schemas    # Pydantic models
    /models     # SQLAlchemy models
    /db         # Migrations, sessions
    main.py

---

## Frontend Structure
/frontend
  /src
    /components
    /pages
    /api         # Axios-based API client
    /store       # Zustand/Redux state

---

## Root
/
  docker-compose.yml
  .env
