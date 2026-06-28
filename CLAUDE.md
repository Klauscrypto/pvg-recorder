# PVG Recorder – Claude Code Handover

## Projektübersicht
Universeller Gesprächs-Recorder für Pilsner Vertriebs GmbH.
Single-File PWA (HTML/CSS/JS) – kein Build-System, kein Framework.

## Dateistruktur
```
pvg_recorder/
├── index.html        # Die gesamte App (HTML + CSS + JS in einer Datei)
├── CLAUDE.md         # Diese Datei
├── AUFGABEN.md       # Offene Aufgaben & Roadmap
└── README.md         # Deployment-Anleitung
```

## Tech Stack
- Vanilla HTML/CSS/JavaScript – kein Node, kein Build
- Anthropic API (claude-sonnet-4-6) für Transkription, Analyse, Chat
- Google Identity Services für Drive OAuth
- Google Drive API v3 für Cloud Backup
- JSZip (CDN) für Word-Export
- localStorage für Datenspeicherung

## Wichtige Funktionen
| Funktion | Implementierung |
|---|---|
| Aufnahme | MediaRecorder API, 1s Chunks |
| Lange Aufnahmen | transcribeChunked() – teilt Base64 auf |
| Transkription | claude-sonnet-4-6 mit document type |
| Sprecher-Erkennung | diarize() – separater API Call |
| Streaming | fetch() mit stream:true, SSE parsing |
| Google Drive | driveUploadNote() – multipart upload |
| Word Export | buildDocx() + JSZip |
| DE/EN Switch | I18N Objekt + applyLang() |
| Angebotsbrief | generateAngebot() |

## API Keys (werden im Browser gespeichert)
- Anthropic: localStorage['pvg_api'] = 'sk-ant-...'
- Google Drive Client-ID: localStorage['pvg_drive_client_id']
- Drive Token: sessionStorage['pvg_drive_token'] (nur Session)

## Deployment
- Zielserver: Hetzner CPX22 VPS
- Domain: pilsner-vertrieb.de/rmn/
- Einfach index.html in den Webserver-Ordner legen
- Kein Build-Schritt notwendig

## Gesprächstypen
Erstgespräch, Beratung, Verhandlung, Vor-Ort-Termin,
Nachfassgespräch, Angebotsbesprechung, Meeting, Interview, Sonstiges

## Datenstruktur (localStorage 'pvg_notes')
```json
[{
  "id": 1234567890,
  "kind": "gespräch" | "notiz",
  "title": "Familie Hägele – Beratung",
  "type": "Beratungstermin",
  "date": "2024-06-18T14:30:00.000Z",
  "duration": 1234,
  "raw": "vollständiges Transkript...",
  "spkLines": [{"speaker": "Klaus", "text": "..."}],
  "uberblick": "...",
  "hintergrund": "...",
  "kennzahlen": [{"label": "Angebotspreis", "value": "40.449 €"}],
  "schmerzpunkte": [{"titel": "...", "text": "..."}],
  "erwartungen": [{"titel": "...", "zeitrahmen": "...", "stakeholder": "..."}],
  "actions": "1. Angebot erstellen...",
  "tasks": [{"titel": "...", "frist": "...", "stakeholder": "...", "prio": "HOCH"}],
  "tips": "...",
  "whatsapp": "...",
  "emailSubject": "...",
  "emailBody": "...",
  "angebot": "vollständiger Angebotsbrief..."
}]
```

## Bekannte Limitierungen
- Sehr lange Aufnahmen (>60 Min) können beim Chunking ungenau werden
- Google Drive Token läuft nach ~1h ab (sessionStorage)
- localStorage Limit: ~5MB – bei sehr vielen Notizen exportieren

## Nächste Schritte → AUFGABEN.md
