# JWT Cheat Sheet — Teacher/Projekt (erweitert)
Stand: 2026-01-06

## 1) JWT: was es ist (und was nicht)
- JWT ist **signiert** (Integrität), normalerweise **nicht verschlüsselt**
- Payload ist Base64URL-encodiert → leicht lesbar

## 2) Standard-Claims (empfohlen)
- `iss`, `aud`, `sub`
- `exp`, `iat`, optional `nbf`
- Rollen/Scopes: `roles`, `scope`

## 3) Lebensdauer & Refresh (Praxis)
- Access Token kurz (Minuten), Refresh Token länger (Tage/Wochen)
- Bei `401` prüfen: exp / aud / iss / Clock skew

## 4) Algorithmen & Key Rotation
- **HS256**: shared secret → Secret-Handling kritisch
- **RS256/ES256**: asymmetrisch → Verifier braucht nur Public Key
- Rotation: `kid` im Header + Key-Set (JWKS)

## 5) Praktische Checks (ohne Verifikation)
```bash
echo "<JWT>" | cut -d '.' -f2 | base64 -d 2>/dev/null
curl -H "Authorization: Bearer <JWT>" https://api.example.com/me
```

## 6) Typische Fehlerbilder
- invalid signature → falscher Key / manipuliert
- token expired → `exp`
- 403 → Auth ok, aber keine Berechtigung
