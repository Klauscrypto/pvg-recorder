# PVG Recorder

Universeller Gesprächs-Recorder für Pilsner Vertriebs GmbH.

## Features
- 🎙 Aufnahme (Mikrofon oder Datei-Upload, bis 90 Min)
- 📝 Automatische Transkription via Claude AI
- 👥 Sprecher-Erkennung (Klaus vs. Kunde)
- 📊 Plaud-Struktur: Überblick, Hintergrund, Kennzahlen, Schmerzpunkte, Erwartungen
- ☑️ Aufgabenliste mit Fristen & Stakeholdern
- 💡 Verkaufstipps & Angebotsbrief-Generator
- 💬 WhatsApp + E-Mail Entwurf
- 🤖 Ask AI – Chat zum Gespräch
- ☁ Google Drive Backup (automatisch)
- 📄 Word & PDF Export
- 🌍 Deutsch / English
- 📱 PWA – als iPhone-App installierbar

## Deployment

### Option 1: Direkt per FTP
```
index.html → pilsner-vertrieb.de/rmn/index.html
```

### Option 2: Hetzner VPS (Nginx)
```bash
# Auf dem Server
mkdir -p /var/www/html/rmn
scp index.html user@server:/var/www/html/rmn/

# Nginx config
location /rmn/ {
    root /var/www/html;
    index index.html;
}
```

### Option 3: GitHub Pages
```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/dein-repo/pvg-recorder.git
git push -u origin main
# GitHub Pages aktivieren → Branch: main
```

## Einrichten nach Deployment

1. **Anthropic API Key**: App öffnen → Einstellungen → API Key eintragen
2. **Google Drive** (optional):
   - console.cloud.google.com → Neues Projekt → APIs & Services → Credentials
   - OAuth 2.0 Client ID erstellen → Authorized Origins: `https://pilsner-vertrieb.de`
   - Client-ID in App eintragen → "Mit Google Drive verbinden"
3. **Als iPhone-App**: Safari → Teilen → "Zum Home-Bildschirm"

## Entwicklung mit Claude Code

```bash
# Repo klonen
git clone https://github.com/dein-repo/pvg-recorder.git
cd pvg-recorder

# Lokal testen (Python HTTP Server)
python3 -m http.server 8080
# → http://localhost:8080

# Oder mit Node
npx serve .
```

## Wichtige Dateien
| Datei | Zweck |
|---|---|
| `index.html` | Die gesamte App |
| `CLAUDE.md` | Technische Dokumentation für Claude Code |
| `AUFGABEN.md` | Roadmap & offene Features |
| `README.md` | Diese Datei |
