# AGENTS.md

## Project overview

This repository contains a small FastAPI application for Mergington High School. The app lets students view extracurricular activities and sign up for them.

- Application entry point: `src/app.py`
- Static frontend files: `src/static/`
- Dependency file: `requirements.txt`
- Project docs: `README.md` and `src/README.md`

## Key runtime behavior

- The app serves a static UI at `/` and redirects to `src/static/index.html`.
- The in-memory activity catalog lives in `activities` inside `src/app.py`.
- Activity data resets when the server restarts.
- Do not introduce persistence or a database unless the task explicitly requires it.

## How to run locally

From the repository root:

```bash
cd src
python app.py
```

Or:

```bash
python src/app.py
```

The app listens on `http://localhost:8000`.

## Important API endpoints

- `GET /activities` returns the activity list.
- `POST /activities/{activity_name}/signup?email=user@mergington.edu` signs up a student.
- Invalid activity names should return a `404` with a FastAPI `HTTPException`.

## Coding conventions

- Keep the codebase simple and lightweight.
- Prefer small, direct FastAPI handlers and minimal helper functions.
- Preserve the existing structure: app logic in `src/app.py`, static frontend assets in `src/static/`.
- If you change the API contract, update the related documentation in `src/README.md` and keep behavior consistent with the frontend.

## Validation

- Run the app locally to check behavior changes.
- If adding or updating automated tests, use `pytest`.
- Prefer targeted verification over broad changes.

## Typical task guidance

When working in this repo:

1. Read the route definitions in `src/app.py` before making API changes.
2. Check the frontend in `src/static/` when changing request/response expectations.
3. Keep the app state in memory unless a task explicitly calls for persistence.
4. Favor minimal changes that preserve the educational demo nature of the project.
