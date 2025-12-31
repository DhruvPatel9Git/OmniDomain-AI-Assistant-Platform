# Domain Chatbot Project

A domain-aware chatbot web application that provides specialized AI assistants for different topics (stock, law, entertainment, psychology, technical). The project includes a FastAPI backend with AI integrations (Google Gemini via langchain/google generative APIs), database models, and a Next.js frontend chat UI.

## Features

- Domain-specific AI assistants with custom system prompts
- Streaming and synchronous chat endpoints
- Image generation for supported domains (uses Pollinations API)
- Conversation history and persistence (SQLAlchemy + Alembic migrations)
- Authentication + per-user conversation ownership

## Architecture

- `backend/` — FastAPI server, SQLAlchemy models, AI services, routers, and scripts
- `frontend/` — Next.js application (React) with domain selector, chat UI, and context for chat state

## Prerequisites

- Python 3.10+ (for backend)
- Node.js 18+ and a package manager (npm, pnpm, or yarn) (for frontend)
- Google API key with access to Google Generative models (set `GOOGLE_API_KEY`)

# Domain Chatbot Project

A domain-aware chatbot platform that provides specialized AI assistants tailored to specific topic areas (stock, law, entertainment, psychology, technical). The system pairs a FastAPI backend (AI routing, persistence, streaming) with a Next.js frontend chat UI to deliver responsive, domain-focused conversations.

## Elaborated Features

- **Domain-specialized Assistants:** Dedicated system prompts and behavior per domain (e.g., financial advisor, legal information assistant, entertainment recommender, psychology educator, senior software engineer).
- **Multi-step Query Analysis & Workflows:** Uses a router workflow to analyze user intent, generate targeted answers, and post-process/enhance responses for readability and safety.
- **Streaming & Progressive Responses:** Supports streaming responses for better UX; responses can be chunked and delivered progressively to the client.
- **Image Generation & Multimedia Support:** Detects image requests in supported domains and generates images via external image APIs (e.g., Pollinations), storing generated assets for delivery.
- **Conversation Memory & Context:** Short-term conversation memory (configurable window) plus conversation history persistence via a relational database for continuity across sessions.
- **Length & Format Controls:** Request-level instructions to enforce short/medium/long responses and formatting rules (e.g., sections for analysis/recommendations in financial responses).
- **Authentication & Ownership:** Per-user conversations and access control so users only interact with their own chat histories.
- **Extensible Domain Management:** Domains are stored as models with system prompts and metadata; new domains can be added via seed scripts or an admin UI.
- **Fallbacks & Robustness:** Graceful fallback behavior when external AI or image services fail, with user-friendly messages and retry paths.
- **Test Coverage & Integration Tests:** Includes tests for backend API and AI integration points to validate expected behavior and guard regressions.

## Project Extensions & Ideas

- **Role-based Assistants:** Allow multiple personas within the same domain (e.g., conservative vs. aggressive financial styles) selectable by the user.
- **Hybrid Retrieval-Augmented Generation (RAG):** Integrate a vector store and document retriever to ground domain responses in user-provided documents or curated knowledge bases.
- **Real Streaming Integration:** Replace simulated chunking with true server-side streaming supported by a streaming-capable LLM or streaming SDK.
- **Multi-modal Conversations:** Expand to accept and analyze images and audio inputs, returning annotated responses or transcripts.
- **Admin Dashboard:** Add a web UI to manage domains, prompts, usage analytics, and moderation controls for unsafe content.
- **Usage Quotas & Billing:** Add per-user quotas, usage tracking, and optional billing integrations for production deployments.
- **Explainability & Audit Logs:** Store analysis metadata and model reasoning steps to support audits and fine-grained review of model outputs.
- **Automated Moderation Pipeline:** Integrate safety filters and content moderation (pre- and post-generation) for sensitive domains like law and psychology.
- **Plugin System:** Allow developers to inject domain-specific tools (calculators, scrapers, code runners) that the assistant can call during a conversation.

## Notes

- The backend references Google Generative models via `langchain_google_genai` and configures `google.generativeai` with `GOOGLE_API_KEY`.
- The repository contains scripts to seed domain records and example integration tests.

---

If you'd like, I can also:

- Add a brief Getting Started snippet (environment variables and quick commands) back into the README.
- Create a small `CONTRIBUTING.md` or `ROADMAP.md` listing prioritized extensions.

Requested change: removed the `Architecture` section and all setup/run instructions; replaced them with an expanded `Features` and `Project Extensions & Ideas` listing.

```

```
