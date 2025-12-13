# FastAPI Postgres PoC on Render

## Local Setup

1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

2. Set up your database.
   - If you have a local Postgres running, update `.env` with your `DATABASE_URL`.
   - Example: `postgresql://postgres:password@localhost:5432/testdb`
   - If you don't set `DATABASE_URL`, it will default to a local SQLite file `test.db` for testing.

3. Run the app:
   ```bash
   uvicorn app.main:app --reload
   ```

4. Open http://127.0.0.1:8000/docs to test the API.

## Render Deployment with Neon Database

1. **Database Setup (Neon)**:
   - Sign up at [Neon.tech](https://neon.tech).
   - Create a new project.
   - Copy the **Connection String** (it looks like `postgres://user:pass@ep-xyz.region.neon.tech/neondb?sslmode=require`).

2. **App Deployment (Render)**:
   - Create a new **Web Service** on Render.
   - Connect your GitHub repository.
   - Settings:
     - **Runtime**: Python 3
     - **Build Command**: `pip install -r requirements.txt`
     - **Start Command**: `uvicorn app.main:app --host 0.0.0.0 --port $PORT`
   - Go to **Environment Variables**:
     - Add `DATABASE_URL` and paste your **Neon Connection String**.

The application will automatically create the necessary tables on startup.
