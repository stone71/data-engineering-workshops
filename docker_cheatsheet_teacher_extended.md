# Docker Cheat Sheet — Teacher/Projekt (erweitert)
Stand: 2026-01-06

## 1) Kernbegriffe
- Image (immutable) vs Container (runtime)
- Tags (`repo:tag`), Registry
- Ports (`-p`) und Volumes (`-v`) als wichtigste Hebel

## 2) Run Patterns
```bash
docker run --name web -p 8080:80 nginx
docker run -d --restart unless-stopped --name api -p 8081:8080 myapp:latest
docker stop api
docker rm api
```

## 3) Debugging/Inspection
```bash
docker logs -f <container>
docker exec -it <container> sh
docker inspect <container>
docker stats
```

## 4) Images/Registry
```bash
docker images
docker pull <image>:<tag>
docker tag myapp:latest registry.example.com/myapp:1.0.0
docker push registry.example.com/myapp:1.0.0
docker rmi <image>
```

## 5) Volumes & Bind Mounts
```bash
docker volume ls
docker volume create mydata
docker run -v mydata:/var/lib/app/data myapp:latest

docker run -v "$(pwd)/data:/data" alpine ls -la /data
```

## 6) Docker Compose (Team-Standard)
```bash
docker compose up -d
docker compose ps
docker compose logs -f
docker compose down
docker compose down -v   # inkl. Volumes
```

## 7) Dockerfile Quick-Reminders
- kleine Base Images, Multi-Stage Builds
- `.dockerignore` nutzen
- möglichst nicht als root laufen (wenn machbar)
