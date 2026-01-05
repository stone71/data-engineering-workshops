# Setup (Docker-first)

## Minimal
- Docker Desktop
- Git
- IDE nach Wahl (IntelliJ / VS Code)

## OOP Workshop ausführen (ohne Java lokal)

```bash
cd workshops/01_java_oop/starter/oop-kata
docker run --rm -v "$PWD":/ws -w /ws maven:3.9-eclipse-temurin-21 mvn test
```

## Datenbank (für JSF/JPA später)

```bash
docker compose up -d
```
Adminer: http://localhost:8080

Login:
- System: PostgreSQL
- Server: postgres
- User: workshop
- Password: workshop
- Database: workshopdb
