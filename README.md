# OmniDomain — Domain-aware Chatbot

OmniDomain is a domain-aware chatbot platform that provides specialized AI assistants tailored to different topic areas (finance, legal, entertainment, psychology, technical, etc.). It pairs a FastAPI backend (AI routing, persistence, streaming) with a Next.js frontend chat UI to deliver responsive, domain-focused conversations.

## Key Features

- Domain-specific assistants with configurable system prompts
- Streaming and synchronous chat endpoints
- Conversation persistence (SQLAlchemy + Alembic) and per-user ownership
- Image generation for supported domains (external image APIs)
- Short-term memory window + conversation history
- Extensible domain model and seed scripts for adding new assistants
- Basic auth and access control for user conversations

## Architecture (high level)

- `backend/` — FastAPI app, database models, AI services, routers, tests, and seed scripts
- `frontend/` — Next.js React app with chat UI, domain selector, and context providers

## Prerequisites

- Python 3.10+ (backend)
- Node.js 18+ (frontend) and a package manager (npm, pnpm, or yarn)
- PostgreSQL or another SQL database supported by SQLAlchemy (configured in `backend/app/config.py`)
- Google API key with access to Google generative models if using that integration (`GOOGLE_API_KEY`)

## Environment variables (common)

Create a `.env` file or set these in your environment for local development:

- `DATABASE_URL` — SQLAlchemy database URL (e.g., `postgresql+psycopg2://user:pass@localhost/dbname`)
- `SECRET_KEY` — FastAPI app secret for signing tokens
- `GOOGLE_API_KEY` — (optional) API key for Google generative models
- `ALLOWED_HOSTS` — (optional) comma-separated hosts for production

See `backend/app/config.py` for all backend configuration options.

## Quick start — Backend

1. Create and activate a Python virtual environment.

```bash
python -m venv .venv
.
# Windows PowerShell:
.\.venv\Scripts\Activate.ps1
# Windows cmd:
.\.venv\Scripts\activate.bat
```

2. Install backend dependencies and run migrations.

```bash
cd backend
pip install -r requirements.txt
alembic upgrade head
```

3. (Optional) Seed domains and demo data:

```bash
python -m scripts.seed_domains
```

4. Run the FastAPI server for development:

```bash
uvicorn main:app --reload --port 8000
```

The backend API will be available at `http://localhost:8000` and docs at `/docs`.

## Quick start — Frontend

1. Install frontend dependencies and run the dev server.

```bash
cd frontend
pnpm install   # or npm install
pnpm dev       # or npm run dev
```

2. Open the app in your browser at `http://localhost:3000`.

The frontend expects the backend to be reachable (see `frontend/services/api.js`), adjust the base URL if necessary.

## Development notes

- Domain definitions are stored in the database and can be seeded via `backend/scripts/seed_domains.py`.
- AI integration code lives under `backend/app/ai/` and domain routing logic is in `backend/app/ai/domain_router.py`.
- Database models are in `backend/app/models/` and API routers in `backend/app/routers/`.

## License

This project does not include a license file. If you want an open-source license, add a `LICENSE` file (MIT, Apache-2.0, etc.).

---

Updated README to provide a concise, actionable developer guide and project overview.
