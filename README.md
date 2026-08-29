# VibeCodingPlaybook-Piano

Ein interaktives virtuelles Musikinstrument – ein digitales Klavier, das direkt im Browser funktioniert.

## Was ist das?

Dies ist ein interaktives virtuelles Musikinstrument – ein digitales Klavier, das direkt im Browser funktioniert. Es besteht aus acht visuellen Tasten, die die Töne der C-Dur-Tonleiter darstellen. Benutzer können diese Tasten entweder mit der Maus anklicken oder über die Computertastatur bedienen.

## Für wen ist es gedacht?

Das System ist für Musikbegeisterte, Anfänger und alle gedacht, die spielerisch in die Musikwelt eintauchen möchten. Es eignet sich besonders für Menschen, die:
- Erste Erfahrungen mit Musik machen wollen
- Interaktive und visuelle Musikinstrumente bevorzugen
- Eine einfache, unterhaltsame Art suchen, Klänge zu erkunden
- Keine externen Geräte oder Installationsaufwand betreiben möchten

## Projekt-Dokumentation

### Systemverständnis
- [`.memory/overview.md`](.memory/overview.md) - Was das System ist, wofür es gedacht ist, was es leistet (und was nicht)
- [`.memory/state-transitions.md`](.memory/state-transitions.md) - Systemzustände, gültige/ungültige Übergänge, Mermaid-Diagramm
- [`.memory/tech-stack.md`](.memory/tech-stack.md) - Empfohlener Tech-Stack, Projektstruktur, Technologien

### Entwickler-Dokumentation
- [`docs/`](docs/) - Interne Dokumentation, Architektur, API-Referenz, Changelog

## Schnellstart

### Voraussetzungen
- Ein moderner Webbrowser (Chrome, Firefox, Safari, Edge)
- Keine Installation oder Abhängigkeiten erforderlich

### Starten der Anwendung
1. Öffne `src/index.html` in deinem Browser
2. Das Klavier ist sofort einsatzbereit

### Bedienung
- **Maus**: Klicke auf die Tasten, um Töne zu erzeugen
- **Tastatur**: Drücke die Tasten A bis K für die acht Klaviertasten
- **Visuelles Feedback**: Der Hintergrund leuchtet in passenden Farben auf

## Features

- **Tonerzeugung**: Spielt bei jedem Tastendruck einen klaren, synthetischen Ton der entsprechenden Note
- **Doppelte Steuerung**: Funktioniert sowohl über Mausklicks als auch über Tastatureingaben (Tasten A bis K)
- **Visuelles Feedback**: Der Bildschirmhintergrund leuchtet in passenden, coolen Farben auf, die zur gespielten Note passen
- **Sofortige Nutzung**: Benötigt keine Installation, keine externen Sounddateien und keine zusätzliche Hardware
- **Intuitive Bedienung**: Die acht Tasten sind klar angeordnet und leicht verständlich

## Was es NICHT bietet

- Keine Aufnahmefunktion für gespielte Musik
- Keine Möglichkeit zur Komposition komplexer Stücke
- Keine professionellen Musikproduktions-Features
- Keine Speicherung oder Exportfunktion von Musik
- Keine erweiterten musiktheoretischen Funktionen
- Keine Verbindung zu externen Musikinstrumenten oder MIDI-Geräten
- Keine Lernprogramme oder Musikunterricht

## Projektstruktur

```
VibeCodingPlaybook-Piano/
├── src/
│   ├── index.html         # Hauptanwendung
│   ├── css/
│   │   └── styles.css    # Alle Styles
│   └── js/
│       └── piano.js      # Haupt-Logik
├── .memory/
│   ├── overview.md       # Systemübersicht
│   ├── state-transitions.md  # Zustandsübergänge
│   └── tech-stack.md     # Tech-Stack Empfehlung
├── docs/                 # Entwickler-Dokumentation
│   ├── index.md
│   ├── getting-started.md
│   ├── architecture.md
│   ├── api.md
│   ├── troubleshooting.md
│   └── changelog.md
└── README.md             # Diese Datei
```

## Tech-Stack

- **HTML5**: Semantisches Markup
- **CSS3**: Vanilla CSS mit Flexbox/Grid
- **Vanilla JavaScript (ES6+)**: Web Audio API für Tonerzeugung
- **Keine Frameworks**: Reine Web-Technologien
- **Keine Build-Tools**: Direkte Ausführung im Browser
- **Keine Abhängigkeiten**: Null externe Libraries

## Entwicklung

Für Entwicklungsdetails siehe [`docs/`](docs/) und [`.memory/tech-stack.md`](.memory/tech-stack.md).

## Lizenz

Dies ist ein Lehr- und Lernprojekt aus dem Vibe Coding Playbook.
