# DevCats Marketplace Prototype

This is a full-stack marketplace application organized with a parent repository and two submodules (backend and frontend).

## Structure
- `backend/`: FastAPI application (Submodule)
- `frontend/`: Vue 3 application (Submodule)
- `docker-compose.yml`: Root orchestration file

## Getting Started

### 1. Clone with submodules
```bash
git clone --recursive <repository-url>
cd DevCats-Test
```

### 2. Start the application
```bash
docker compose up -d
```
The frontend will be available at `http://localhost`, and the backend API at `http://localhost:8000`.

## Data Management

### Persistence
Data is stored in `./backend/data/`:
- `backend/data/postgres`: Database files
- `backend/data/minio`: S3 storage files

### Sharing & Testing (Option 3: Archive)
If you received a data archive (`data.zip` or similar):
1. Ensure the containers are stopped: `docker compose down`
2. Extract the archive into `backend/data/` so that you have `backend/data/postgres` and `backend/data/minio`.
3. Start the containers: `docker compose up -d`

### Seeding (Alternative)
To generate a *fresh* set of 1000 test products:
```bash
docker compose exec backend python app/db/seed.py
```
