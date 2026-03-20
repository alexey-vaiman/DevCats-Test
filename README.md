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
2. Make directory: `mkdir -p backend/data`
3. Download data.zip into `backend/data/`:
    ```bash
    curl https://drive.google.com/file/d/1cCsqmA14WcRQQNzsNDgO8RnEuBl2ZFst/view?usp=sharing --output data.zip
    ```
4. Extract the archive: `unzip data.zip`, you'll have `data/minio` and `data/postgres`
5. Start the containers: `docker compose up -d`

### Seeding (Alternative)
To generate a *fresh* set of 1000 test products:
```bash
docker compose exec backend python app/db/seed.py
```
