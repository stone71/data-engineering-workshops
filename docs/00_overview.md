# Überblick

Dieses Repo bündelt eine Workshop-Reihe zu:

- Java (OOP, Tests, APIs)
- SQL (Querying, Cleaning, Transformation)
- Python (ETL/ELT, Datenpipelines)
- DevOps Basics (Docker, CI/CD)
- Überblick über Kafka, Spark, Cloud
- Power BI (Reporting/Visualisierung)

## Lernprinzip

1) **Erst Grundlagen sauber** (OOP + SQL), dann API/ETL, dann DevOps/Streaming/BI.  
2) **Roter Faden**: Ein durchgehendes Projekt, das in jedem Workshop erweitert wird.  
3) **Hands-on**: Kurzer Input → Guided Coding → Challenge → Review.

## Wie Workshops aufgebaut sind

Jeder Workshop-Ordner enthält typischerweise:

- `README.md` – Lernziele, Ablauf, Setup, Aufgabenübersicht
- `exercises/` – Aufgaben (meist als Markdown), inkl. Teilaufgaben
- `starter/` – Startcode/Material, das Studierende direkt ausführen können
- `solution/` – Musterlösung
- optional: `slides/`

## Durchgehendes Projekt

Im Ordner `project/` liegt das Langzeitprojekt.
Ziel: ein kleines System aus API + DB + ETL, das reale Themen abbildet:
- Datenmodell & Domain
- Datenqualität, Transformation, Reporting
- Reproduzierbare Ausführung mit Docker
- Basics zu CI/CD
- optional Events (Kafka) & verteilte Verarbeitung (Spark)
