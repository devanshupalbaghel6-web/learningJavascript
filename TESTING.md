# Testing the PoC

1. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

2. **Run the App**:
   ```bash
   python -m uvicorn app.main:app --reload --port 8001
   ```

3. **Open Swagger UI**:
   Go to [http://127.0.0.1:8001/docs](http://127.0.0.1:8001/docs).

4. **Test Steps**:
   - **Register**: Use `POST /users/` to create a new user.
     - JSON: `{"email": "test@example.com", "password": "secretpassword"}`
   - **Login**: Use `POST /token` (Authorize button usually handles this, or use the endpoint directly).
     - Username: `test@example.com`
     - Password: `secretpassword`
     - It returns an `access_token`.
   - **Access Protected Route**: Use `GET /users/me`.
     - Click "Authorize" button at top right.
     - Enter username/password.
     - Execute the request.
     - It should return your user details.

If this works, your app is successfully:
1. Connecting to Neon (Postgres).
2. Writing data (creating user).
3. Reading data (login & fetching profile).
