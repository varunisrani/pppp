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

- Python 3.9 (the version selected by `Dockerfile`)
- `pip` and virtual-environment support
- The missing internal modules described under **Status and limitations**

## Local setup

The repository declares the following intended FastAPI setup:

```bash
git clone https://github.com/varunisrani/pppp.git
cd pppp
python -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
python -m uvicorn app:app --host 0.0.0.0 --port 8000
```

The included container configuration expresses the same server entry point:

```bash
docker build -t pppp-film-api .
docker run --rm -p 8000:8000 pppp-film-api
```

The partial Streamlit entry point, if its missing modules are restored, is intended to run from its own directory:

```bash
cd sd1
python -m streamlit run app.py
```

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

This fork originates from [`vpxop111/pppp`](https://github.com/vpxop111/pppp) and does not declare a license. The current snapshot is not runnable from a fresh clone: `app.py` imports `sd1.src.*` and `utils.logging_utils`, while those modules are not tracked, and `sd1/app.py` likewise imports a missing `src/` tree. The requirements are unpinned and include duplicate and standard-library package names. The repository also contains a checked-in virtual environment, generated data, binary model/vector files, logs, and cache files; these should be reviewed before treating the project as reproducible or production-ready.
