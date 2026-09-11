# Film Production AI API (`pppp`)

This repository is a public fork containing a FastAPI entry point and a partial Streamlit application for AI-assisted film preproduction workflows.

## Core features

- FastAPI endpoints for script upload/text analysis, scene one-liners, character breakdowns, scheduling, budgeting, and storyboard generation.
- JSON-file persistence for generated workflow results.
- Endpoints for retrieving or clearing stored results and API logs.
- A separate Streamlit interface for navigating upload, analysis, one-liner, character, schedule, budget, storyboard, and overview stages.
- Docker configuration for serving the FastAPI application with Uvicorn.

## Technology stack

- Python and FastAPI
- Uvicorn and Pydantic
- Streamlit and Plotly
- OpenAI Agents SDK, Replicate, and Google Generative AI dependencies
- pandas, NumPy, NetworkX, and scikit-learn

## Prerequisites

- Git, for inspecting the repository locally
- A dependency and source audit before attempting installation or execution

## Local setup

The current snapshot is safe to clone for inspection only:

```bash
git clone https://github.com/varunisrani/pppp.git
cd pppp
```

Do not install the current requirements or attempt to start the application or container. Before any installation or execution, audit and pin every dependency, deduplicate the requirements, remove the `logging` entry (logging is part of Python's standard library), and restore and review the missing internal modules.

### Declared but unverified entry points

These declarations describe repository intent, not runnable setup: root `app.py` declares a FastAPI application; `Dockerfile` declares an Uvicorn process serving `app:app`; and `sd1/app.py` is a partial Streamlit interface. The declared entry-point behavior has not been verified from a fresh clone because required internal modules are missing and the dependency set is unsafe and unreproducible in its current form.

## Configuration

`app.py` loads a `.env` file, but the tracked application files do not explicitly name any environment variables. Provider credentials and other required settings therefore cannot be determined reliably from this snapshot; do not commit credentials to the repository.

## Project structure

```text
app.py             FastAPI application and HTTP endpoints
Dockerfile         Python 3.9/Uvicorn container definition
requirements.txt   Unpinned Python dependencies
sd1/app.py         Streamlit workflow interface
sd1/temp.py        Incomplete storyboard UI fragment
sd1/static/        Checked-in example result and storyboard files
```

## Status and limitations

This fork originates from [`vpxop111/pppp`](https://github.com/vpxop111/pppp) and does not declare a license. The current snapshot is not runnable from a fresh clone: `app.py` imports `sd1.src.*` and `utils.logging_utils`, while those modules are not tracked, and `sd1/app.py` likewise imports a missing `src/` tree. The requirements are unpinned, duplicated, and include `logging`, which must not be installed as a third-party substitute for the Python standard library module. The repository also contains a checked-in virtual environment, generated data, binary model/vector files, logs, and cache files; these should be reviewed before treating the project as reproducible or production-ready.
