# Setup (lokal)

## Empfohlene Tools

### Java
- JDK 21 (oder 17, falls eure Umgebung das bevorzugt)
- IDE: IntelliJ IDEA oder VS Code
- Build: Maven oder Gradle (je nach Workshop/Projekt)

### Python
- Python 3.11+ (oder 3.10+)
- optional: `uv` oder `pip` + `venv`

### Datenbank / Tools
- Docker Desktop (für Postgres + Adminer via Compose)
- Optional: DBeaver / DataGrip für SQL

### Git
- Git CLI + GitHub/GitLab Account

---

## Quickstart: Postgres starten

Im Repo-Root:

```bash
docker compose up -d
```

- Postgres: `localhost:5432`
- Adminer UI: `http://localhost:8080`

Adminer Login:
- System: PostgreSQL
- Server: `postgres`
- Benutzer: `workshop`
- Passwort: `workshop`
- Datenbank: `workshopdb`

Stoppen:
```bash
docker compose down
```

---

## Empfohlene Konventionen

- Branching: `main` + Feature-Branches (`feature/<topic>`)
- Kleine Commits mit sinnvollen Messages
- Übungen: Erst `starter/` bearbeiten, dann mit `solution/` vergleichen
