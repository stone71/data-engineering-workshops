# HTTPS / TLS / PKI Cheat Sheet — Teacher/Projekt (erweitert)
Stand: 2026-01-06

## 1) TLS: worauf es ankommt
- **Server-Identität**: Zertifikat passt zur Domain (SAN/CN)
- **Trust Chain**: Leaf → Intermediate → Root (im Truststore)
- **Gültigkeit**: NotBefore/NotAfter, Rotation rechtzeitig planen

## 2) Browser-Checks
- Issuer/Subject/SAN prüfen
- Gültigkeitszeitraum + Kette (Chain) prüfen
- Mixed Content vermeiden (HTTPS-Seite lädt HTTP-Ressourcen)

## 3) CLI/Debug (Standard)
```bash
curl -v https://example.com
openssl s_client -connect example.com:443 -servername example.com
```

## 4) Interne PKI / Zertifikatsverteilung (Praxis)
- Root offline, Intermediate signiert
- Clients müssen Root/Intermediate im Truststore haben (OS/Browser/Java/Container)
- Rotation/Automatisierung einplanen

## 5) Java Truststore (typisch)
```bash
keytool -list -keystore <truststore.jks>
keytool -importcert -alias myca -file myca.crt -keystore <truststore.jks>
```

## 6) Häufige Ursachen bei TLS-Fehlern
- Hostname mismatch (SAN fehlt)
- Chain incomplete (Intermediate fehlt)
- alte TLS-Version/Cipher
- Uhrzeit falsch → „not yet valid“
