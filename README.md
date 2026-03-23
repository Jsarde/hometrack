# HomeTrack

A privacy-first, self-hosted home expense tracker.

[![Python 3.12](https://img.shields.io/badge/python-3.12-blue.svg)](https://www.python.org/downloads/)

## Overview

This project helps you to track home-related expenses: condominium fees, utilities, taxes, insurance and more.
It runs entirely on your machine — a single Python process serving a browser-based UI.

## Quickstart

### local development

**Prerequisites:** Python 3.12, [uv](https://docs.astral.sh/uv/getting-started/installation/), git

```bash
# 1. Clone and enter the repo
git clone git@github.com:Jsarde/hometrack.git
cd hometrack

# 2. Install all dependencies
uv sync

# 3. Run the application
uv run hometrack
# Open http://localhost:8080 in your browser
```

### Podman container
```bash
podman-compose up
# Open http://localhost:8080 in your browser
# Data is persisted in the 'hometrack-data' Podman volume
```

## Configuration

All configuration is via environment variables (or a `.env` file for local dev):

| Variable | Default | Description |
|---|---|---|
| `HOMETRACK_DB_URL` | `sqlite:///~/.local/share/hometrack/hometrack.db` | SQLAlchemy database URL |
| `HOMETRACK_DEBUG` | `false` | Enable debug logging and OpenAPI docs |
| `HOMETRACK_HOST` | `127.0.0.1` | Bind address |
| `HOMETRACK_PORT` | `8080` | Bind port |

Copy `.env.example` to `.env` and edit as needed.

## Development
```bash
# Install pre-commit hooks (one-time)
uv run pre-commit install

# Run the test suite
uv run pytest -s -vv

# Run with coverage
uv run pytest --cov=hometrack --cov-report=term-missing

# Lint and format
uv run ruff check .
uv run ruff format .

# Type check
uv run ty check hometrack/
```
