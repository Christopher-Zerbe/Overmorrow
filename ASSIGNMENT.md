# Assignment: Ship Overmorrow as a Multi-User Web App

Your job is to take this Flutter codebase and turn it into a secure **self-hosted web application** that multiple users can access from their browsers.

## The Goal

When a grader runs a single command in the repo root, your solution must:

1. Build and start the application.
2. Serve the Overmorrow web UI on **`http://localhost:8000`**.
3. Allow the app to securely fetch real weather data using the provided API keys.

## Hard Requirements (the grading contract)

Your submission **must** satisfy all of the following. These define the interface the grader uses:

1. **Entry point.** The repo root must contain a working `docker-compose.yml`. The grader will run:
   ```
   docker compose up -d --build
   ```
   and expect it to exit 0.

2. **Port.** The web UI must be reachable at `http://localhost:8000`.

3. **Environment variables.** Your compose file must read secrets from an `.env` file at the repo root. The grader supplies this file at test time. Variable names you must support:
   - `WAPI_KEY` — WeatherAPI.com key
   - `UNSPLASH_KEY` — Unsplash access key (optional; only if your configuration uses it)
   - `TIMEZONEDB_KEY` — TimezoneDB key (optional; only if your configuration uses it)

   A template is provided in `.env.example`. **Do not commit a real `.env`.**

4**Clean teardown.** `docker compose down` must cleanly stop and remove all containers your solution starts.

## What You Have Freedom Over

- The stack: any web server, reverse proxy, or backend language (nginx, Caddy, Node, Python, Go, …).
- The number of containers/services in your compose file.
- How you build the Flutter web bundle (in a build stage, ahead of time, whatever works).

## What You Should Hand In

A single commit (or PR) on your GitHub repo containing:

- `docker-compose.yml` and any Dockerfiles / config your solution needs.
- Any source code and components you add.
- An updated `.env.example` if you introduce new variables.
- Any code changes to the Flutter app required to make it work in this setup.

## Self-Check Before Submitting

Run these yourself:

```bash
cp .env.example .env          # fill in real keys
docker compose up -d --build
curl -f http://localhost:8000 # should return the app's HTML
# open http://localhost:8000 in a browser and verify the weather loads
docker compose down
```
