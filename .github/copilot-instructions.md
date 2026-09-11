# Copilot Instructions

## Project Overview

This repository contains a small FastAPI application for browsing and signing up for extracurricular activities at Mergington High School.

- Backend entry point: `src/app.py`
- Static frontend: `src/static/index.html`, `src/static/app.js`, and `src/static/styles.css`
- Activity data is stored in memory and resets when the process restarts.

## Development

Install dependencies with:

```bash
pip install -r requirements.txt
```

Run the development server from the repository root with:

```bash
uvicorn src.app:app --reload --reload-include 'src/static/*'
```

The application is available at `http://localhost:8000/`, with API docs at `/docs`.

## API Surface

- `GET /activities` returns the activity dictionary.
- `POST /activities/{activity_name}/signup?email=...` adds a participant.
- `/` redirects to the static frontend.

Preserve these endpoints and response shapes unless a task explicitly requires an API change.

## Change Guidelines

- Keep backend changes focused in `src/app.py` and preserve the existing FastAPI patterns.
- Keep frontend behavior in `src/static/app.js` and styling in `src/static/styles.css`.
- Reuse the existing in-memory model unless persistence is explicitly requested.
- Update `src/README.md` when setup steps or public API behavior changes.
- Avoid unrelated formatting or dependency changes.

## Validation

At minimum, verify that the application imports successfully:

```bash
python3 -c "import sys; sys.path.insert(0, 'src'); import app; print(app.app.title)"
```

Run the test suite with `python3 -m pytest -q` when pytest is installed. There are currently no test files in the repository.