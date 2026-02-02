# MariaDB Docker Container

Dieses Setup stellt eine MariaDB-Datenbank mit phpMyAdmin als Web-Interface bereit.

## Services

- **MariaDB**: Relationale Datenbank (Port 3306)
- **phpMyAdmin**: Web-Interface zur Datenbankverwaltung (Port 8082)

## Zugangsdaten

- **Root-Passwort**: `password`
- **Datenbank**: `mydb`
- **Benutzer**: `admin`
- **Passwort**: `password`

## Verwendung

Container starten:
```bash
docker-compose up -d
```

Container stoppen:
```bash
docker-compose down
```

Logs anzeigen:
```bash
docker-compose logs -f
```

## Zugriff

- **phpMyAdmin**: http://localhost:8082
- **MariaDB**: localhost:3306

## Verbindung zur Datenbank

```bash
docker exec -it mariadb mysql -u admin -p
```

Oder mit einem MySQL-Client:
```
Host: localhost
Port: 3306
User: admin
Password: password
Database: mydb
```

## Plattformen

Läuft auf macOS, Linux und Windows.
