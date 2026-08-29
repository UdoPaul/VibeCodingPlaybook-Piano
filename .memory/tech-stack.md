# VibeCodingPlaybook-Piano Tech-Stack Empfehlung

## Empfohlener Tech-Stack

### Frontend (Hauptsprache: JavaScript)
- **HTML5**: Semantisches Markup für die Klaviertasten und UI-Elemente
- **CSS3**: Vanilla CSS mit Flexbox/Grid für Layout, CSS Variables für Themen
- **Vanilla JavaScript (ES6+)**: Web Audio API für Tonerzeugung, Event-Handling für Interaktion
- **Keine Frameworks**: Reine Web-Technologien ohne React, Vue, Angular etc.

### Build-Tools
- **Kein Build-Prozess**: Direktes Ausführen im Browser, kein npm/webpack/vite
- **Keine Abhängigkeiten**: Kein package.json, keine node_modules
- **Simple File Structure**: HTML, CSS und JS in separaten Dateien im src/ Ordner

### Dokumentation
- **Markdown**: Einfache Markdown-Dateien im docs/ Ordner
- **Ordner docs/**: Interne Dokumentation, Changelog, API-Referenz
- **Kein Build-Prozess**: Direktes Lesen der .md Dateien

## Empfehlungen

### Der einfachste praktikable Stack
- **Native Web Audio API**: Keine externen Audio-Libraries, built-in Browser-Funktionalität
- **Vanilla JavaScript**: Keine Framework-Overhead, direkter DOM-Zugriff
- **Separate CSS-Datei**: Stile in src/css/styles.css, keine CSS-Frameworks
- **LocalStorage**: Für einfache Persistenz (falls benötigt), keine externe Datenbank

### Minimale Abhängigkeiten
- **Null externe Libraries**: Alles mit built-in Browser APIs
- **Kein npm**: Keine Paketmanager-Abhängigkeiten, keine package.json
- **Keine CDNs**: Alles lokal oder inline, keine externen Ressourcen
- **Keine Icons**: Unicode-Symbole oder einfache CSS-Formen statt Icon-Libraries
- **Keine Dokumentations-Tools**: Reine Markdown-Dateien ohne Build-Prozess

### Maximale Übersichtlichkeit
- **Transparenter Code**: Klare, lesbare JavaScript-Funktionen ohne Magie
- **Einfache Struktur**: HTML, CSS, JS in separaten Dateien oder gut organisiert
- **Direktes Debugging**: Keine Build-Steps, Browser DevTools direkt nutzbar
- **Selbsterklärend**: Code-Kommentare und konsistente Benennung

## Zu vermeiden

### Ausgefallene Frameworks
- ❌ React, Vue, Angular, Svelte - unnötig für einfache Interaktion
- ❌ jQuery - veraltet, Vanilla JS ist ausreichend
- ❌ CSS-Frameworks (Bootstrap, Tailwind) - Overhead für einfaches Styling
- ❌ Web Components - zu komplex für diesen Anwendungsfall

### Starke Abstraktion
- ❌ State-Management Libraries (Redux, Zustand) - überflüssig
- ❌ Observable Patterns - für einfache DOM-Manipulation nicht nötig
- ❌ Dependency Injection - keine komplexe Architektur benötigt
- ❌ Design Patterns aus MVC/MVVM - zu abstrakt für direkte DOM-Interaktion

### Vorzeitig eingesetzte Skalierungstools
- ❌ TypeScript - für einfaches JavaScript-Projekt nicht notwendig
- ❌ Build-Tools (Webpack, Vite, Rollup) - kein Build-Prozess benötigt
- ❌ Testing-Frameworks (Jest, Cypress) - für MVP nicht erforderlich
- ❌ CI/CD Pipelines - für einzelne HTML-Datei übertrieben
- ❌ Containerisierung (Docker) - Browser-basiert, keine Server-Komponente
- ❌ Dokumentations-Frameworks (VitePress, Docusaurus) - einfache Markdown-Dateien ausreichend

## Dokumentationsstruktur

### Ordner docs/
```
docs/
├── index.md              # Startseite der Dokumentation
├── getting-started.md    # Schnellstart-Anleitung
├── architecture.md       # Systemarchitektur
├── api.md                # API-Referenz (falls benötigt)
├── troubleshooting.md    # Fehlerbehebung
└── changelog.md          # Änderungshistorie
```

### Dokumentations-Workflow
- Markdown-Dateien direkt im Editor erstellen und bearbeiten
- Für Vorschau: Markdown-Viewer im Editor oder Online-Tools nutzen
- Kein Build-Prozess oder Entwicklungsserver erforderlich

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
│   └── tech-stack.md     # Diese Datei
├── docs/                 # Markdown Dokumentation
│   ├── index.md
│   ├── getting-started.md
│   ├── architecture.md
│   ├── api.md
│   ├── troubleshooting.md
│   └── changelog.md
└── README.md             # Projekt-README
```

## Technologien im Detail

### Web Audio API
- **Warum**: Native Browser-API für Tonerzeugung, keine externen Audio-Dateien
- **Features**: OscillatorNodes, GainNodes, AudioContext
- **Browser-Support**: Alle modernen Browser, weit verbreitet

### CSS Variables & Flexbox
- **Warum**: Native CSS ohne Frameworks, responsive Design möglich
- **Features**: CSS Custom Properties für Themen, Flexbox für Layout
- **Browser-Support**: Alle modernen Browser

### Vanilla JavaScript ES6+
- **Warum**: Keine Build-Schritte, direkte Ausführung im Browser
- **Features**: Arrow Functions, Template Literals, Classes, Modules
- **Browser-Support**: Alle modernen Browser

## Changelog-Format

### docs/changelog.md
```markdown
# Changelog

## [Unreleased]

### Added
- Initial MVP implementation
- 8 piano keys (C4 to C5)
- Mouse and keyboard interaction
- Visual feedback system

### Changed
- None

### Fixed
- None

## [1.0.0] - 2026-08-29

### Added
- First release
- Basic piano functionality
```

## Performance & Deployment

### Performance
- **Keine Ladezeit**: Inline oder minimale externe Ressourcen
- **Keine Bundle-Größe**: Kein JavaScript-Bundle, native Ausführung
- **Schnelle Interaktion**: Direkter DOM-Zugriff ohne Virtual DOM

### Deployment
- **Static Hosting**: Jeder statische Web-Host (GitHub Pages, Netlify, Vercel)
- **Kein Server**: Reine Client-seitige Anwendung
- **Kein Build-Prozess**: Direktes Hochladen der src/ Dateien
- **Dokumentation**: Markdown-Dateien können mitgehostet oder separat bereitgestellt werden

## Warum dieser Stack?

### Einfachheit
- **Lernkurve**: Minimal - Standard Web-Technologien
- **Wartbarkeit**: Klare, transparente Code-Struktur
- **Debugging**: Direkt im Browser möglich

### Performance
- **Ladezeit**: Sofortige Verfügbarkeit, keine Build-Schritte
- **Laufzeit**: Native Performance, keine Framework-Overhead
- **Speicher**: Minimal, keine Heavy Dependencies

### Zukunftssicherheit
- **Browser-Standards**: Basierend auf stabilen Web-Standards
- **Keine Vendor-Lock-in**: Keine Framework-spezifischen Konzepte
- **Portabilität**: Läuft in jedem modernen Browser

## Alternativen (nicht empfohlen)

### React + Web Audio API
- ❌ Overhead für einfache DOM-Manipulation
- ❌ Build-Prozess erforderlich
- ❌ Bundle-Größe unnecessarily large

### Tone.js (Audio Library)
- ❌ Externe Abhängigkeit
- ❌ Native Web Audio API ist ausreichend
- ❌ Zusätzliche Lernkurve

### Vue.js
- ❌ Reactive System unnötig für einfache Interaktion
- ❌ Build-Prozess für optimalen Einsatz
- ❌ Komplexität ohne Mehrwert

## Fazit

Der empfohlene Stack maximiert Einfachheit, Performance und Wartbarkeit während er Komplexität und Abhängigkeiten minimiert. Er ist perfekt geeignet für:
- Lehr- und Lernzwecke
- Schnelle Prototypenentwicklung
- Langfristige Wartbarkeit ohne Framework-Upgrades
- Direktes Verständnis der zugrundeliegenden Web-Technologien
