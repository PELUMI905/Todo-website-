# Todo App — Full Project

This folder combines your existing FastAPI API with a React + Vite frontend.

## Folder structure

- `backend/` — your FastAPI API, SQLite database setup, JWT login, task endpoints, and tests.
- `frontend/` — React login/register pages and task dashboard.

## 1. Start the backend (Windows)

Open a terminal in `backend`:

```powershell
py -m venv venv
.\venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
copy .env.example .env
python -m uvicorn main:app --reload
```

If PowerShell blocks activation, use Command Prompt and run `venv\\Scripts\\activate.bat`.

Backend docs: http://127.0.0.1:8000/docs

**Security:** Before any public deployment, change `SECRET_KEY` in `backend/.env` to a long random secret. Do not upload `.env` to GitHub.

## 2. Start the frontend

Open a second terminal in `frontend`:

```powershell
npm install
copy .env.example .env
npm run dev
```

Open the local address Vite prints, usually http://localhost:5173.

The frontend `.env` should contain:

```env
VITE_API_URL=http://127.0.0.1:8000
VITE_USE_DEMO=false
```

Restart `npm run dev` after changing `.env`.

## API routes used by this frontend

- `POST /api/auth/register/`
- `POST /api/auth/login/`
- `GET /api/auth/me/`
- `GET /tasks/`
- `POST /tasks/`
- `PUT /tasks/{task_id}`
- `DELETE /tasks/{task_id}`
- `PATCH /tasks/{task_id}/complete`

## Important note about reopening completed tasks

The existing API can mark a task as completed but has no endpoint to mark it pending again. The frontend displays an explanation if you try to uncheck a completed task. We can add that endpoint as the next improvement.

## Tests

From `backend`, install requirements, then run:

```powershell
python -m pytest
```
