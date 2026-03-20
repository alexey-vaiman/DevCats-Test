# DevCats Marketplace Prototype

This is a full-stack marketplace application organized with a parent repository and two submodules (backend and frontend).

## Structure
- `backend/`: FastAPI application (Submodule)
- `frontend/`: Vue 3 application (Submodule)
- `docker-compose.yml`: Root orchestration file

## Getting Started

### 1. Clone with submodules
```bash
git clone --recurse-submodules git@github.com:alexey-vaiman/DevCats-Test.git
cd DevCats-Test
```

### 2. Create .env files
```bash
cp .env.example .env
cp backend/.env.example backend/.env
cp frontend/.env.example frontend/.env
```

### 3. Start the application
```bash
docker compose up -d
```
The frontend will be available at `http://localhost`, and the backend API at `http://localhost:8000`.

## API Configuration

The frontend can talk to the backend in two ways:

### A. Proxy Mode (Default / Recommended)
Requests to `/api/v1` are proxied via **Nginx** (in Docker) or **Vite** (in dev mode).
- **Docker**: Nginx handles it via `nginx.conf`.
- **Local Dev**: `npm run dev` handles it via `vite.config.ts`.
*No extra configuration needed.*

### B. Direct Mode (Remote Backend)
If the backend is hosted on a different machine, set `VITE_API_URL` in `frontend/.env`:
```env
VITE_API_URL=http://your-remote-backend-ip:8000/v1
```
> [!IMPORTANT]
> When using Direct Mode, ensure the frontend's address is added to `BACKEND_CORS_ORIGINS` in the backend's `.env` file.

## Data Management

### Persistence
Data is stored in `./backend/data/`:
- `backend/data/postgres`: Database files
- `backend/data/minio`: S3 storage files

### Sharing & Testing (Option 3: Archive)
You can download the data archive from the following link:
https://drive.google.com/file/d/1cCsqmA14WcRQQNzsNDgO8RnEuBl2ZFst/view?usp=drive_link

If you received a data archive (`data.zip` or similar):
1. Ensure the containers are stopped: `docker compose down`
2. Make directory: `mkdir -p backend/data && cd backend/data`
3. Download data.zip into `backend/data/`:
4. Extract the archive: `unzip data.zip`, you'll have `data/minio` and `data/postgres`
5. Start the containers: `docker compose up -d`

### Seeding (Alternative)
To generate a *fresh* set of 1000 test products:
```bash
docker compose exec backend python app/db/seed.py
```
