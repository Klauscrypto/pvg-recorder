# AUFGABEN & ROADMAP – PVG Recorder

## 🔥 Priorität HOCH

### A1 – Kunden-Datenbank
Jede Aufnahme einem Kunden zuordnen. Komplette Gesprächshistorie pro Kunde.
- [ ] Kunden-CRUD (Anlegen, Bearbeiten, Löschen)
- [ ] Dropdown bei Aufnahme: "Welchem Kunden zuordnen?"
- [ ] Kundendetail-Seite mit allen Gesprächen
- [ ] Suche nach Kundenname

### A2 – Push-Erinnerungen / Wiedervorlage
- [ ] Web Push API Notification einbauen
- [ ] Nach Gespräch: "Wiedervorlage in X Tagen?" setzen
- [ ] Dashboard mit fälligen Wiedervorlagen
- [ ] Service Worker für Offline + Push

### A3 – Google Drive Token Refresh
Aktuell läuft der Token nach ~1h ab.
- [ ] Token-Ablauf erkennen
- [ ] Automatisch neu anfordern (silent refresh)
- [ ] Nutzer informieren wenn Drive nicht erreichbar

## 💡 Priorität MITTEL

### B1 – Tagesreport per E-Mail
Jeden Abend automatische Zusammenfassung aller Gespräche des Tages.
- [ ] Benötigt: kleinen Cron-Job auf Hetzner oder Zapier
- [ ] Oder: manueller "Tagesreport" Button in der App

### B2 – Bessere Sprecher-Erkennung
- [ ] Nutzer kann Sprecher-Namen manuell vergeben
- [ ] Lernfunktion: "Klaus" immer als Hauptsprecher markieren

### B3 – Statistik-Dashboard
- [ ] Gespräche pro Woche/Monat
- [ ] Häufigste Einwände (aus Tasks/Schmerzpunkten)
- [ ] Durchschnittliche Gesprächsdauer

### B4 – Export-Verbesserungen
- [ ] Alle Notizen als ZIP exportieren
- [ ] CSV-Export für Excel
- [ ] Direkter Share-Button für iOS

## 🛠 Priorität NIEDRIG

### C1 – Multi-User / Team
- [ ] Mehrere Nutzer mit eigenem Login
- [ ] Gemeinsamer Notizen-Pool
- [ ] Benötigt: Backend (Node.js + DB auf Hetzner)

### C2 – CRM-Integration
- [ ] HubSpot API
- [ ] Pipedrive API
- [ ] Kontakt anlegen, Notiz eintragen, Task erstellen

### C3 – Real-Time Transkription
- [ ] Text erscheint während der Aufnahme
- [ ] Benötigt: WebSocket oder EventSource zur API

## 🐛 Bekannte Bugs
- [ ] Bei sehr langen Aufnahmen (>45 Min) kann Chunking-Join Satzbrüche erzeugen
- [ ] Google Drive Button im Header verschwindet auf kleinen iPhones
- [ ] Timer-Warnung bei 90 Min wird nicht immer angezeigt

## 📝 Deployment-Checkliste Hetzner
- [ ] SSH-Zugang einrichten
- [ ] Nginx/Apache konfigurieren
- [ ] /rmn/ Verzeichnis anlegen
- [ ] index.html hochladen
- [ ] HTTPS (Let's Encrypt) aktivieren
- [ ] Google OAuth Redirect URI auf pilsner-vertrieb.de/rmn/ setzen
