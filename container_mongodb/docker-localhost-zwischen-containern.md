# Docker-Container: Schaubild, Beispiel-Netzwerk und warum `localhost` nicht zwischen Containern funktioniert

## Schaubild: Host, Docker-Netzwerk, Container

```text
                        (Dein Rechner / Host-System)
                 +----------------------------------------+
                 |  OS: Linux / macOS / Windows           |
                 |                                        |
Browser/Client -->|  http://localhost:8080                |
                 |          │                             |
                 |          │ Port-Mapping (-p 8080:80)    |
                 |          ▼                             |
                 |     Docker Engine                      |
                 |        │                               |
                 |        │  virtuelles Netz (Bridge)      |
                 |        ▼                               |
                 |   docker0 / compose_default_network     |
                 |   z.B. 172.18.0.0/16                   |
                 +------------------┬---------------------+
                                    │
                 +------------------+---------------------+
                 |                                        |
     Container A  |   Container B                          |
   (web/app)      |   (api/db)                             |
+--------------+  |  +------------------+                  |
| eth0: .2     |  |  | eth0: .3         |                  |
| Port 80      |  |  | Port 5000 / 5432 |                  |
|              |  |  |                  |                  |
| localhost -> |  |  | localhost ->     |                  |
| A selbst     |  |  | B selbst         |                  |
+--------------+  |  +------------------+                  |
       │          |          ▲
       └----------+----------┘
          Kommunikation im Docker-Netz:
          - per DNS-Name:  http://api:5000
          - oder per IP:   http://172.18.0.3:5000
```

---

## Warum `localhost` zwischen Containern nicht funktioniert

`localhost` bedeutet immer: **„dieser Rechner“** – und in Docker ist „dieser Rechner“ **der jeweilige Container selbst**.

- In **Container A** zeigt `localhost` auf **Container A**
- In **Container B** zeigt `localhost` auf **Container B**

Wenn also deine App in Container A versucht, `http://localhost:5000` aufzurufen, sucht sie **Port 5000 in Container A** – nicht in Container B.

> **Merksatz:** `localhost` ist kein „Docker-weites localhost“, sondern pro Container separat.

---

## Wie Container stattdessen miteinander kommunizieren

### 1) Über Service-/Containernamen (empfohlen, z. B. Docker Compose)

Docker stellt im gemeinsamen Netzwerk ein internes DNS bereit.

Beispiel:
- Service heißt im Compose `api`
- Web/App ruft auf: `http://api:5000`

```yaml
services:
  web:
    build: ./web
    depends_on: [api]
  api:
    build: ./api
```

In `web`:
- ✅ `http://api:5000`
- ❌ `http://localhost:5000`

### 2) Über Container-IP (geht, aber nicht stabil)

IPs können sich ändern → eher nur zum Debuggen sinnvoll.

### 3) Vom Container zum Host

Wenn ein Container etwas auf dem Host erreichen soll:

- **Linux:** oft `http://172.17.0.1:<port>` (Gateway des docker0-Interfaces, je nach Setup)
- **macOS/Windows (Docker Desktop):** meist `http://host.docker.internal:<port>`

---

## Sonderfall: Host Network

Wenn ein Container mit `--network host` läuft (Linux), teilt er sich das Netzwerk des Hosts.  
Dann kann `localhost` „wie gewohnt“ funktionieren.

**Aber:**
- weniger Isolation
- Port-Konflikte wahrscheinlicher
- in Compose nicht immer sinnvoll
