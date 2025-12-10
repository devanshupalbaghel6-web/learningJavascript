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

## Render Deployment

1. Create a new **Web Service** on Render.
2. Connect your GitHub repository.
3. Settings:
   - **Runtime**: Python 3
   - **Build Command**: `pip install -r requirements.txt`
   - **Start Command**: `uvicorn app.main:app --host 0.0.0.0 --port $PORT`
4. Add a **PostgreSQL** database on Render.
   - Copy the `Internal Database URL`.
5. In your Web Service settings, go to **Environment Variables**.
   - Add `DATABASE_URL` and paste the internal database URL.
   
The application will automatically create the necessary tables on startup.
