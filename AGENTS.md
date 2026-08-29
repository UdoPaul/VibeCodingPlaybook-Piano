# AGENTS.md — VibeCodingPlaybook-Piano

Diese Datei definiert, wie sich die KI bei der Arbeit an diesem Projekt verhalten soll.

## KI-Verhaltensregeln

### Grundprinzipien
- **Transparenz**: Jede Änderung muss dokumentiert werden
- **Konsistenz**: Halte die definierten Strukturen und Konventionen ein
- **No Silent Evolution**: Keine stillschweigende Weiterentwicklung des Projekts
- **Dokumentations-Pflicht**: Jede Code-Änderung muss entsprechende Dokumentations-Updates auslösen

### Was die KI beibehalten muss
1. **Projektstruktur**: Die definierte Ordnerstruktur (`src/`, `.memory/`, `docs/`)
2. **Tech-Stack**: Vanilla JavaScript, HTML5, CSS3 ohne Frameworks
3. **Zustandsmodell**: Das in `.memory/state-transitions.md` definierte Zustandsmodell
4. **Logging-Konventionen**: Die unten definierten Logging-Standards
5. **Dokumentations-Sync**: Synchronisation zwischen Code, .memory/, docs/ und README.md

### Was die KI aktualisieren muss
Bei jeder Code-Änderung müssen folgende Dateien aktualisiert werden:

#### Pflicht-Updates bei Code-Änderungen
1. **`.memory/`**: Aktualisiere die relevante .memory-Datei (overview.md, state-transitions.md, tech-stack.md)
2. **`docs/`**: Aktualisiere die entsprechende Dokumentationsdatei (architecture.md, api.md, etc.)
3. **`README.md`**: Aktualisiere Schnellstart, Features oder Struktur wenn relevant
4. **`docs/changelog.md`**: Füge die Änderung zum Changelog hinzu

#### Update-Workflow
```markdown
Bei Code-Änderung:
1. Code ändern
2. .memory/ aktualisieren (falls Systemverhalten sich ändert)
3. docs/ aktualisieren (falls Architektur/API sich ändert)
4. README.md aktualisieren (falls für Benutzer relevant)
5. docs/changelog.md aktualisieren (immer)
```

## Logging-Konventionen

### Grundregeln
- **Jede Funktion muss Logging enthalten**: DEBUG oder höher
- **Zustandsänderungen**: INFO mit Vorher- und Nachher-Werten
- **Fehlerpfade**: ERROR mit vollständigem Kontext
- **Keine unterdrückten Ausnahmen**: Alle Exceptions müssen geloggt werden
- **Korrelations-IDs**: Müssen weitergegeben werden, niemals verwerfen
- **Strukturierte Logs**: Schlüssel-Wert-Paare, keine interpolierten Zeichenfolgen

### Log-Level-Verwendung

#### DEBUG
```javascript
// Für Funktions-Eintritt, Parameter-Inspektion, Debug-Informationen
console.log({
  level: 'DEBUG',
  timestamp: new Date().toISOString(),
  function: 'playNote',
  parameters: { note: 'C4', duration: 0.5 },
  correlationId: correlationId
});
```

#### INFO
```javascript
// Für Zustandsänderungen mit Vorher- und Nachher-Werten
console.log({
  level: 'INFO',
  timestamp: new Date().toISOString(),
  event: 'state_transition',
  previousState: 'IDLE',
  newState: 'KEY_PRESSING',
  trigger: 'mouse_click',
  actor: 'user',
  correlationId: correlationId
});
```

#### ERROR
```javascript
// Für Fehler mit vollständigem Kontext
console.log({
  level: 'ERROR',
  timestamp: new Date().toISOString(),
  error: 'audio_context_failed',
  message: 'AudioContext could not be created',
  context: {
    browser: navigator.userAgent,
    previousState: currentState,
    attemptedAction: 'initialize_audio'
  },
  correlationId: correlationId,
  stackTrace: error.stack
});
```

### Korrelations-ID-Handling
```javascript
// Korrelations-ID muss durch gesamte Call-Chain weitergegeben werden
function handleKeyPress(correlationId, key) {
  console.log({
    level: 'DEBUG',
    timestamp: new Date().toISOString(),
    function: 'handleKeyPress',
    correlationId: correlationId,
    key: key
  });
  
  // Weitergabe an Unterfunktionen
  playNote(correlationId, key);
  updateVisuals(correlationId, key);
}
```

### Strukturierte Logs vs. Interpolation
```javascript
// ❌ FALSCH - Interpolierte Zeichenfolgen
console.log(`Playing note ${note} at ${timestamp} for user ${userId}`);

// ✅ RICHTIG - Strukturierte Schlüssel-Wert-Paare
console.log({
  level: 'INFO',
  timestamp: new Date().toISOString(),
  event: 'note_played',
  note: note,
  playedAt: timestamp,
  userId: userId,
  correlationId: correlationId
});
```

### Keine unterdrückten Ausnahmen
```javascript
// ❌ FALSCH - Unterdrückte Exception
try {
  playNote(note);
} catch (error) {
  // Exception ignoriert
}

// ✅ RICHTIG - Geloggte Exception
try {
  playNote(note);
} catch (error) {
  console.log({
    level: 'ERROR',
    timestamp: new Date().toISOString(),
    error: 'note_playback_failed',
    message: error.message,
    note: note,
    correlationId: correlationId,
    stackTrace: error.stack
  });
  // Fehlerbehandlung oder Weiterleitung
}
```

## No Silent Evolution

### Was "No Silent Evolution" bedeutet
- Keine Änderungen an der Projektstruktur ohne Dokumentation
- Keine neuen Features ohne Changelog-Eintrag
- Keine API-Änderungen ohne Update der Dokumentation
- Keine Tech-Stack-Änderungen ohne Update von tech-stack.md
- Keine Zustandsmodell-Änderungen ohne Update von state-transitions.md

### Beispiel für korrekte Vorgehensweise
```markdown
Wenn du ein neues Feature hinzufügst:

1. Code implementieren
2. .memory/overview.md aktualisieren (wenn Funktionalität sich ändert)
3. docs/architecture.md aktualisieren (wenn Architektur sich ändert)
4. docs/api.md aktualisieren (wenn API sich ändert)
5. README.md aktualisieren (wenn für Benutzer relevant)
6. docs/changelog.md aktualisieren (immer - "Added: Neues Feature X")
```

## Projekt-Regeln

### Tech-Stack-Compliance
- ❌ Keine Frameworks (React, Vue, Angular, etc.)
- ❌ Keine Build-Tools (Webpack, Vite, etc.)
- ❌ Keine npm-Abhängigkeiten
- ❌ Keine TypeScript-Konvertierung ohne explizite Anweisung
- ✅ Vanilla JavaScript ES6+
- ✅ HTML5 semantisches Markup
- ✅ CSS3 mit Flexbox/Grid

### Dateistruktur-Compliance
- HTML-Dateien nur in `src/`
- CSS-Dateien nur in `src/css/`
- JavaScript-Dateien nur in `src/js/`
- Dokumentation nur in `docs/`
- System-Dokumentation nur in `.memory/`

### Code-Stil
- Konsistente Benennung (camelCase für JavaScript, kebab-case für CSS)
- Kommentare für komplexe Logik
- Vermeidung von Magischen Zahlen (Konstanten definieren)
- Modularisierung (Funktionen statt Monolith)

## Dokumentations-Sync-Checkliste

Bevor eine Änderung als abgeschlossen gilt:

- [ ] Code implementiert
- [ ] `.memory/` aktualisiert (falls relevant)
- [ ] `docs/` aktualisiert (falls relevant)
- [ ] `README.md` aktualisiert (falls relevant)
- [ ] `docs/changelog.md` aktualisiert (immer)
- [ ] Logging-Konventionen eingehalten
- [ ] Korrelations-IDs durchgehend verwendet
- [ ] Keine unterdrückten Exceptions

## Fehlerbehandlung

### Wenn unsicher bei einer Änderung
1. Prüfe `.memory/overview.md` für Systemverständnis
2. Prüfe `.memory/state-transitions.md` für Zustandsmodell
3. Prüfe `.memory/tech-stack.md` für Tech-Stack-Compliance
4. Prüfe `docs/architecture.md` für Architektur-Verständnis
5. Frage bei Unsicherheit

### Bei Tech-Stack-Änderungen
- Tech-Stack-Änderungen benötigen explizite Benutzer-Anweisung
- Updates müssen in `.memory/tech-stack.md` dokumentiert werden
- Changelog muss den Grund und die Auswirkungen enthalten

## Qualitätssicherung

### Code-Review-Checkliste
- [ ] Logging-Konventionen eingehalten
- [ ] Korrelations-IDs durchgehend verwendet
- [ ] Keine unterdrückten Exceptions
- [ ] Strukturierte Logs statt Interpolation
- [ ] Zustandsübergänge korrekt protokolliert
- [ ] Dokumentation synchronisiert

### Test-Checkliste (falls Tests implementiert werden)
- [ ] Tests für neue Funktionen
- [ ] Tests für Fehlerpfade
- [ ] Tests für Zustandsübergänge
- [ ] Logging-Integration getestet

## Notfall-Regeln

### Bei kritischen Fehlern
1. Fehler sofort mit ERROR-Level loggen
2. Vollständigen Kontext aufnehmen
3. Benutzer informieren (wenn relevant)
4. In `docs/troubleshooting.md` dokumentieren
5. In Changelog aufnehmen

### Bei Breaking Changes
1. Vorher dokumentieren, was sich ändert
2. Alle betroffenen Dokumentationen aktualisieren
3. Changelog mit "BREAKING" markieren
4. README.md mit Warnung aktualisieren

## Zusammenfassung

Diese AGENTS.md stellt sicher, dass:
- Die KI konsistent und transparent arbeitet
- Dokumentation immer synchron mit Code bleibt
- Logging-Konventionen strikt eingehalten werden
- Keine stillschweigenden Evolutionen stattfinden
- Das Projekt übersichtlich und wartbar bleibt

Bei jeder Änderung: **Denke an den Sync zwischen Code, .memory/, docs/ und README.md!**
