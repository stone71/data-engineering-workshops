# HTTP & curl Cheat Sheet — Teacher/Projekt (erweitert)
Stand: 2026-01-06

## 1) Request/Response: was man wirklich liest
- Methode + URL (GET/POST/PUT/PATCH/DELETE)
- Statuscode + ggf. Fehlermeldung im Body
- Header: `Content-Type`, `Accept`, `Authorization`, `Location`, `Set-Cookie`
- Body: JSON (häufig), Form-Data (Uploads), Text/HTML

## 2) curl: nützliche Patterns
### Header/Status ansehen
```bash
curl -i https://example.com
curl -I https://example.com
```

### Verbose Debug (TLS/Redirect/Headers)
```bash
curl -v https://example.com
curl -L -v https://example.com
```

### JSON API Calls
```bash
curl -sS -i -X POST https://api.example.com/items \
  -H "Content-Type: application/json" \
  -H "Accept: application/json" \
  -d '{"title":"Todo","done":false}'
```

### Bearer Token
```bash
curl -sS -i https://api.example.com/me \
  -H "Authorization: Bearer <JWT>"
```

### Query Params
```bash
curl -G -i https://api.example.com/search \
  --data-urlencode "q=docker" \
  --data-urlencode "limit=10"
```

## 3) Häufige Fehlerbilder
- **401 Unauthorized**: Token fehlt/abgelaufen/ungültig
- **403 Forbidden**: Token ok, aber keine Rechte
- **415 Unsupported Media Type**: `Content-Type` fehlt/falsch
- **400 Bad Request**: JSON/Validierung falsch
- **502/503**: Upstream/Service down, Gateway/Proxy

## 4) Quick JSON Pretty Print (optional)
```bash
curl -s https://api.example.com/items | python -m json.tool
# oder:
curl -s https://api.example.com/items | jq .
```
