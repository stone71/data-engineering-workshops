# Data Engineering Workshops (Java • Python • SQL)

Dieses Repository ist ein **Monorepo** für eine Workshop-Reihe, mit dem Ziel Studierenden praxisnah
**Software-Engineering** (Java/OOP, APIs) und **Data Engineering** (SQL, ETL/ELT, Kafka/Spark, BI, DevOps)
beizubringen — inklusive eines **durchgehenden Projekts** als roter Faden.

## Idee & Leitgedanke

Wir bauen Schritt für Schritt ein kleines, aber realistisches System („StudentHub Analytics“ als Beispiel):
- **Java API** (CRUD + Analytics-Endpunkte)
- **Postgres** als Datenbasis
- **SQL** für Abfragen, Bereinigung und Transformation
- **Python ETL/ELT** (Rohdaten → Staging → Curated)
- **Docker / Compose** für reproduzierbares Setup
- **CI/CD Basics** für Qualität & Automatisierung
- optional: **Kafka** (Events) & **Spark** (verteilte Verarbeitung)
- **Power BI** für Visualisierung und Reporting

Jeder Workshop ist **für sich lauffähig**, zahlt aber in das gemeinsame Projekt ein.

---

## Repository-Struktur

- `docs/`  
  Übersicht, Setup-Anleitungen, Konventionen und Cheatsheets.

- `workshops/`  
  Der Lernpfad. Jeder Workshop-Ordner enthält:
  - `README.md` (Agenda, Lernziele, How-to-run)
  - `exercises/` (Aufgaben)
  - `starter/` (Startcode/Material für Studierende)
  - `solution/` (Musterlösungen)
  - optional `slides/`

- `project/`  
  Das durchgehende Projekt (StudentHub Analytics). Enthält:
  - `services/` (Java API, Python ETL, DB, optional Streaming)
  - `data/` (Beispieldaten, Schemas)
  - `dashboards/` (Power BI + SQL Views fürs Reporting)
  - `ops/` (Docker, CI, Scripts)
  - `architecture/` (Kontext, Diagramme, ADRs)

- `shared/`  
  Wiederverwendbare SQL-Snippets, Fixtures und Tools.

---

## Quickstart (lokal)

### 1) Voraussetzungen
Siehe: `docs/01_setup.md`

### 2) Datenbank starten (Postgres + Adminer)
```bash
docker compose up -d
```

- Postgres: `localhost:5432`
- Adminer: `http://localhost:8080`

**Adminer Login**
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

## Workshop-Index (geplant)

- `workshops/01_java_oop_basics/` – Java Grundlagen, OOP, Tests
- `workshops/02_sql_querying/` – SQL Abfragen, Joins, Aggregationen, Window Functions
- `workshops/03_java_rest_api/` – REST API mit Java
- `workshops/04_python_etl/` – ETL/ELT mit Python
- `workshops/05_docker_compose/` – Docker Basics + Compose
- `workshops/06_cicd_basics/` – CI/CD Grundlagen
- `workshops/07_kafka_intro/` – Kafka Intro (Events, Producer/Consumer)
- `workshops/08_spark_intro/` – Spark Intro (Batch/Big Data)
- `workshops/09_powerbi_reporting/` – Power BI Reporting & Visualisierung

---

## Konventionen (Kurz)

- Workshop-Ordner werden **nummeriert** (`01_...`, `02_...`) damit Sortierung stabil bleibt.
- Übungen sind klein & inkrementell, Lösungen liegen separat in `solution/`.
- Ziel ist „production-ish“: saubere Struktur, Logging, Tests, reproduzierbare Ausführung.

---

## Lizenz
Siehe `LICENSE`.
