# Permanent Context for AI-Driven Development

## Purpose
Этот проект разрабатывается полностью с помощью AI-агентов. Контекст определяет архитектуру, правила и обязательные практики, соблюдение которых гарантирует согласованность кода, API, данных, UI и инфраструктуры.

---

## System Architecture
- Backend: FastAPI (Python 3.12), SQLAlchemy 2.0, Alembic, Pydantic.
- Frontend: Vue 3 + TypeScript + Vite.
- Database: PostgreSQL.
- Storage: S3-compatible bucket (MinIO or AWS S3).
- Auth: JWT access + refresh tokens.
- API: REST, OpenAPI 3.1.
- Infrastructure: Docker Compose + ready-to-port Kubernetes manifests.

---

## Coding Standards
### Python
- Strict type hints.
- No TODO in code.
- Services contain business logic.
- Routes are thin wrappers around services.
- Pydantic models define request/response formats.
- Полностью асинхронная реализация
    - все endpoint-ы: async def
    - драйвер PostgreSQL: asyncpg
    - SQLAlchemy: SQLAlchemy 2.x (последняя стабильная) в async-режиме (sqlalchemy.ext.asyncio)
- Миграции Alembic обязательны для любых изменений схемы БД.
- PostgreSQL: последняя стабильная версия.
- S3 хранилище: MinIO.


### JavaScript/TypeScript
- ESLint + Prettier.
- Files structured as Feature-Sliced Design.
- Components must be pure.
- No inline styles unless necessary.
- API client in `/src/api`.

---

## Required Documentation Updates
Каждый раз при изменении проекта агент обязан обновлять:
- /docs/openapi.yaml
- /docs/domain-model.md
- /docs/architecture.md
- /docs/changelog.md

---

## Required Process (Every Agent Operation)
1. Проверить consistency всей системы.
2. Обновить domain model (если требуется).
3. Обновить API (openapi.yaml).
4. Обновить схемы данных.
