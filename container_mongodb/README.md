# MongoDB mit Docker Compose

## Voraussetzungen

- Docker Desktop installiert (für macOS, Windows, Linux)
- Docker Compose (in Docker Desktop enthalten)

## Installation

### 1. Docker Desktop installieren

- **macOS/Windows**: [Docker Desktop herunterladen](https://www.docker.com/products/docker-desktop)
- **Linux**: Docker Engine und Docker Compose installieren

### 2. Container starten

Im Ordner `container_mongodb` ausführen:

```bash
docker-compose up -d
```

Der Parameter `-d` startet die Container im Hintergrund.

## Zugriff

### MongoDB Datenbank
- **Host**: `localhost`
- **Port**: `27017`
- **Username**: `admin`
- **Password**: `password`

**Connection String**:
```
mongodb://admin:password@localhost:27017
```

### Mongo Express (Web-UI)
- **URL**: http://localhost:8081
- Öffne die URL im Browser für die visuelle Verwaltung

## Befehle

### Container starten
```bash
docker-compose up -d
```

### Container stoppen
```bash
docker-compose down
```

### Container stoppen und Daten löschen
```bash
docker-compose down -v
```

### Logs anzeigen
```bash
docker-compose logs -f
```

### Status prüfen
```bash
docker-compose ps
```

## Sicherheitshinweis

⚠️ Die Standard-Credentials (`admin`/`password`) sind nur für Entwicklungsumgebungen geeignet. Für Produktionsumgebungen bitte sichere Passwörter verwenden!
