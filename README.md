# Java Workshops (OOP → JSF) — Monorepo (minimal)

Dieses Repository ist bewusst **minimal gehalten**, damit der Einstieg leicht bleibt.
Wir starten mit **Java Objektorientierung + Tests** und erweitern danach um **JSF**.

## Struktur

- `docs/` – kurze Übersicht & Setup (Docker-first)
- `workshops/01_java_oop/` – OOP + Unit-Tests (Starter + Lösung)
- `workshops/02_java_jsf/` – JSF-Workshop (Skeleton, wird als Nächstes ausgebaut)

## Quickstart (ohne lokale Java-Installation)

### Tests im OOP-Workshop ausführen (Docker)
```bash
cd workshops/01_java_oop/starter/oop-kata
docker run --rm -v "$PWD":/ws -w /ws maven:3.9-eclipse-temurin-21 mvn test
```

### Lokal starten (optional)
Wenn du Java 21 + Maven lokal hast:
```bash
mvn test
```

## Datenbank (für JSF/Persistence später)
```bash
docker compose up -d
```
Adminer: http://localhost:8080
