# Tagesbegleiter - Entwicklungs-Roadmap

## 📋 Projektübersicht
Modulare Produktivitäts-Web-App mit neumorphischem Design als personalisierbare Dashboard-Lösung für Wissensarbeiter.

**Technologie-Stack:** React + TypeScript, Tailwind CSS, Firebase, Vite  
**Geschätzte Entwicklungszeit:** 8-12 Wochen (Einzelentwickler) | 4-6 Wochen (Team 2-3 Entwickler)

---

## 🚀 Phase 1: Grundlegende Infrastruktur

### ✅ Task 1.1: Projekt-Setup und Grundstruktur
**Geschätzte Zeit:** 1-2 Tage  
**Priorität:** 🔴 Kritisch

**Aufgaben:**
- [ ] Neues React-TypeScript-Projekt mit Vite erstellen
- [ ] TypeScript mit strikten Einstellungen konfigurieren
- [ ] Tailwind CSS installieren und konfigurieren
- [ ] Projektstruktur erstellen:
  - [ ] `src/components/` - UI-Komponenten
  - [ ] `src/hooks/` - Custom Hooks
  - [ ] `src/types/` - TypeScript-Definitionen
  - [ ] `src/utils/` - Hilfsfunktionen
  - [ ] `src/styles/` - CSS-Dateien
  - [ ] `src/contexts/` - React Context
- [ ] TypeScript-Interfaces definieren:
  - [ ] `Tile` - Kachel-Eigenschaften
  - [ ] `GridPosition` - Position im Grid
  - [ ] `AppState` - Haupt-App-Zustand
- [ ] Jest und React Testing Library konfigurieren
- [ ] Ersten Test für App-Komponente erstellen
- [ ] "Hello World" App-Komponente implementieren

**Akzeptanzkriterien:**
- ✅ Projekt startet ohne Fehler
- ✅ TypeScript-Strict-Mode aktiv
- ✅ Tailwind funktioniert
- ✅ Tests laufen durch
- ✅ Projektstruktur ist sauber organisiert

---

### ✅ Task 1.2: Neumorphismus Design-System
**Geschätzte Zeit:** 2-3 Tage  
**Priorität:** 🔴 Kritisch

**Aufgaben:**
- [ ] CSS-Klassen für neumorphische Elemente erstellen
- [ ] Basis-Komponenten implementieren:
  - [ ] `NeumorphicCard` - Basis-Kachel
  - [ ] `NeumorphicButton` - Schaltflächen
  - [ ] `NeumorphicInput` - Eingabefelder
- [ ] Farbpalette definieren:
  - [ ] Light Mode: Hintergrund #e0e0e0, Schatten hell/dunkel
  - [ ] Dark Mode: Hintergrund #2d3748, Schatten angepasst
- [ ] CSS-Variablen implementieren:
  - [ ] Primäre Hintergrundfarben
  - [ ] Schatten-Farben (hell/dunkel)
  - [ ] Border-Radius Werte
  - [ ] Abstände und Größen
- [ ] Interaktive Zustände erstellen:
  - [ ] Hover-Effekte
  - [ ] Active-States
  - [ ] "Pressed"-Effekt für Buttons
- [ ] Komponenten-Tests für alle neumorphischen Elemente
- [ ] Demo-Seite zur Darstellung aller Komponenten

**Design-Spezifikationen:**
- Weiche, extrudierte Elemente
- Subtile doppelte Schatten (hell und dunkel)
- Monochromatische Farbpalette
- Keine harten Ränder
- Elemente aus gleichem Material wie Hintergrund

**Akzeptanzkriterien:**
- ✅ Alle neumorphischen Komponenten funktionieren
- ✅ Light/Dark Mode wechselt korrekt
- ✅ Hover/Active-States sind implementiert
- ✅ Demo-Seite zeigt alle Komponenten
- ✅ Tests decken alle Komponenten ab

---

### ✅ Task 1.3: Grid-System und Layout-Grundlagen
**Geschätzte Zeit:** 2-3 Tage  
**Priorität:** 🔴 Kritisch

**Aufgaben:**
- [ ] Grid-System mit festen Einheiten implementieren (1x1, 2x1, 3x1)
- [ ] `GridContainer` für Basis-Layout erstellen
- [ ] `GridCell`-Komponenten für einzelne Grid-Positionen
- [ ] Kachel-Größen als Enum/Konstanten definieren
- [ ] Grid-Logik implementieren:
  - [ ] Berechnung der Grid-Dimensionen basierend auf Viewport
  - [ ] Automatisches Umbrechen bei schmalen Fenstern
  - [ ] Kollisionserkennung beim Platzieren von Kacheln
- [ ] Responsive Verhalten:
  - [ ] Desktop: Feste Grid-Struktur
  - [ ] Tablet/Mobile: Automatisches Umbrechen
- [ ] Utility-Funktionen erstellen:
  - [ ] Grid-Position-Berechnung
  - [ ] Verfügbare Plätze finden
  - [ ] Kachel-Überlappung prüfen
- [ ] `GridContext` für Zustandsverwaltung
- [ ] Visuelle Gitter-Linien (optional ein-/ausblendbar)
- [ ] Unit-Tests für Grid-Berechnungen und Collision-Detection

**Akzeptanzkriterien:**
- ✅ Grid-System funktioniert auf allen Bildschirmgrößen
- ✅ Kollisionserkennung verhindert Überlappungen
- ✅ Responsive Verhalten funktioniert korrekt
- ✅ Alle Utility-Funktionen sind getestet
- ✅ GridContext verwaltet Zustand korrekt

---

### ✅ Task 1.4: Basis-Kachel-System
**Geschätzte Zeit:** 3-4 Tage  
**Priorität:** 🔴 Kritisch

**Aufgaben:**
- [ ] Abstrakte Tile-Basisklasse/Interface erstellen
- [ ] `TileWrapper`-Komponente für konsistente Darstellung
- [ ] `TileManager` für Kachel-Verwaltung
- [ ] Kachel-Typen als Enum definieren:
  - [ ] `CLOCK` - Uhr
  - [ ] `THEME_TOGGLE` - Design-Umschalter
  - [ ] `DAY_PROGRESS` - Tagesleiste
  - [ ] `PROMPT_LIBRARY` - Prompt-Bibliothek
  - [ ] `DATA_ANALYSIS` - Daten-Analyse
  - [ ] `SHOP` - Kachel-Shop
- [ ] Kachel-Eigenschaften implementieren:
  - [ ] Eindeutige ID
  - [ ] Typ
  - [ ] Größe (1x1, 2x1, 3x1)
  - [ ] Position im Grid
  - [ ] Konfiguration (spezifisch pro Kachel-Typ)
- [ ] `TileRegistry` für verfügbare Kachel-Typen
- [ ] Kachel-Operationen implementieren:
  - [ ] Kachel hinzufügen
  - [ ] Kachel entfernen
  - [ ] Kachel verschieben
  - [ ] Kachel konfigurieren
- [ ] Factory Pattern für Kachel-Erstellung
- [ ] Serialisierung für Persistierung
- [ ] `TileContext` für globalen Zustand
- [ ] Error Boundaries für Kachel-Fehler
- [ ] Mock-Implementierungen für jeden Kachel-Typ
- [ ] Interaktionstests

**Akzeptanzkriterien:**
- ✅ Alle Kachel-Typen sind definiert
- ✅ Factory Pattern funktioniert korrekt
- ✅ Serialisierung/Deserialisierung funktioniert
- ✅ Error Boundaries fangen Kachel-Fehler ab
- ✅ Mock-Implementierungen sind funktional

---

## 🎯 Phase 2: Kern-Dashboard-Funktionalität

### ✅ Task 2.1: Drag & Drop Funktionalität
**Geschätzte Zeit:** 3-4 Tage  
**Priorität:** 🟠 Hoch

**Aufgaben:**
- [ ] Drag & Drop-System ohne externe Bibliotheken implementieren
- [ ] Drag-Funktionalität:
  - [ ] Kacheln vom aktuellen Platz aufnehmen
  - [ ] Visueller Feedback während Dragging
  - [ ] Ghost-Image folgt Mauszeiger
- [ ] Drop-Funktionalität:
  - [ ] Gültige Drop-Zonen hervorheben
  - [ ] Kollisionsprüfung vor Drop
  - [ ] Automatisches Snap-to-Grid
- [ ] `DragDropContext` für Zustandsverwaltung
- [ ] Drag-States implementieren:
  - [ ] `IDLE` - Ruhezustand
  - [ ] `DRAGGING` - Wird gezogen
  - [ ] `DROPPING` - Wird abgelegt
- [ ] Visuelles Feedback:
  - [ ] Kachel halbtransparent während Drag
  - [ ] Gültige Drop-Bereiche hervorheben
  - [ ] Ungültige Bereiche rot markieren
- [ ] Touch-Support für Mobile-Geräte
- [ ] Native HTML5 Drag & Drop API als Fallback
- [ ] Custom Mouse/Touch-Events für bessere Kontrolle
- [ ] `DragPreview`-Komponente für Ghost-Image
- [ ] Drag-Constraints (nur innerhalb Grid)
- [ ] Drag-Throttling für Performance
- [ ] Tests für Drag & Drop-Szenarien und Touch-Interaktionen

**Akzeptanzkriterien:**
- ✅ Kacheln können per Drag & Drop bewegt werden
- ✅ Visuelles Feedback funktioniert korrekt
- ✅ Touch-Unterstützung funktioniert auf Mobile
- ✅ Kollisionserkennung verhindert ungültige Drops
- ✅ Performance ist auch bei vielen Kacheln gut

---

### ✅ Task 2.2: Kachel-Shop (Hinzufügen/Entfernen)
**Geschätzte Zeit:** 3-4 Tage  
**Priorität:** 🟠 Hoch

**Aufgaben:**
- [ ] Shop-Kachel als spezielle Kachel-Typ erstellen
- [ ] Shop-Overlay/Modal implementieren:
  - [ ] Zeigt alle verfügbaren, nicht-platzierten Kachel-Typen
  - [ ] Kachel-Vorschau mit Beschreibung
  - [ ] "Heften"-Funktionalität (Kachel folgt Mauszeiger)
- [ ] Kachel-Hinzufügen:
  - [ ] Klick auf Shop-Kachel öffnet Shop-Overlay
  - [ ] Klick auf verfügbare Kachel "heftet" sie an Mauszeiger
  - [ ] Klick auf freie Grid-Position platziert Kachel
  - [ ] Escape-Taste bricht Platzierung ab
- [ ] Kachel-Entfernen:
  - [ ] Rechtsklick auf Kachel aktiviert "Entfernen-Modus"
  - [ ] Rotes X-Icon erscheint auf Kachel
  - [ ] Klick auf X entfernt Kachel und gibt sie im Shop frei
  - [ ] Klick außerhalb deaktiviert Entfernen-Modus
- [ ] `ShopContext` für Shop-Zustandsverwaltung
- [ ] Kachel-Eindeutigkeit implementieren:
  - [ ] Jede Kachel-Art nur einmal platzierbar
  - [ ] Bereits platzierte Kacheln im Shop ausgrauen
- [ ] Portal für Shop-Overlay
- [ ] Mauszeiger-Verfolgung für "geheftete" Kacheln
- [ ] Animations-Effekte für Kachel-Übergänge
- [ ] Keyboard-Shortcuts (Escape, Delete)
- [ ] Accessible-Support (ARIA-Labels, Fokus-Management)
- [ ] Tests für Shop-Workflows und Kachel-Lebenszyklus

**Akzeptanzkriterien:**
- ✅ Shop-System funktioniert intuitiv
- ✅ Kacheln können einfach hinzugefügt/entfernt werden
- ✅ Eindeutigkeit wird korrekt durchgesetzt
- ✅ Keyboard-Navigation funktioniert
- ✅ Animationen sind smooth und performant

---

## 🎨 Phase 3: Grundlegende Kacheln

### ✅ Task 3.1: Uhr-Kachel mit Farbverlauf
**Geschätzte Zeit:** 2-3 Tage  
**Priorität:** 🟠 Hoch

**Aufgaben:**
- [ ] `ClockTile`-Komponente erstellen (1x1 Größe)
- [ ] Aktuelle Zeit in digitalem Format anzeigen (HH:MM)
- [ ] Sekundengenauen Farbverlauf implementieren:
  - [ ] Sekunde 0: Startfarbe
  - [ ] Sekunde 59: Endfarbe
  - [ ] Lineare Interpolation zwischen Farben
- [ ] Konfigurationsdialog erstellen:
  - [ ] Farbwähler für Startfarbe (visuell + HEX-Input)
  - [ ] Farbwähler für Endfarbe (visuell + HEX-Input)
  - [ ] Live-Vorschau der Farbänderung
  - [ ] Speichern/Abbrechen-Buttons
- [ ] Farbinterpolation implementieren:
  - [ ] RGB-Farbinterpolation
  - [ ] HSL-Farbinterpolation als Alternative
  - [ ] Unterstützung für HEX, RGB, HSL-Eingaben
- [ ] `useTime`-Hook für Zeit-Updates
- [ ] Konfiguration-Persistierung
- [ ] Update-Intervall: 1 Sekunde
- [ ] `requestAnimationFrame` für smooth Updates
- [ ] Farbberechnungen als Utility-Funktionen
- [ ] `ColorPicker`-Komponente (wiederverwendbar)
- [ ] Farbvalidierung
- [ ] Accessibility für Farbwähler
- [ ] Tests für Farbinterpolation, Zeit-Updates und Konfiguration

**Akzeptanzkriterien:**
- ✅ Uhr zeigt korrekte Zeit an
- ✅ Farbverlauf ändert sich sekundengenau
- ✅ Konfigurationsdialog funktioniert intuitiv
- ✅ Alle Farbformate werden unterstützt
- ✅ Performance ist bei kontinuierlichen Updates gut

---

### ✅ Task 3.2: Design-Umschalter (Light/Dark Mode)
**Geschätzte Zeit:** 2 Tage  
**Priorität:** 🟠 Hoch

**Aufgaben:**
- [ ] `ThemeToggleTile`-Komponente erstellen (1x1 Größe)
- [ ] Theme-Switching implementieren:
  - [ ] Light Mode: Sonnen-Icon
  - [ ] Dark Mode: Mond-Icon
  - [ ] Smooth Transition zwischen Modi
- [ ] `ThemeContext` für globales Theme-Management
- [ ] Theme-Persistence implementieren:
  - [ ] Speichern in localStorage
  - [ ] Systemweite Theme-Anwendung
- [ ] CSS-Variablen für beide Modi aktualisieren:
  - [ ] Hintergrundfarben
  - [ ] Schatten-Farben
  - [ ] Text-Farben
  - [ ] Accent-Farben
- [ ] Icon-Komponenten erstellen:
  - [ ] `SunIcon` (für Light Mode)
  - [ ] `MoonIcon` (für Dark Mode)
  - [ ] Smooth Icon-Transitions
- [ ] CSS-Variablen für Theme-Werte
- [ ] `useTheme`-Hook
- [ ] Theme-Definitionen als Konstanten
- [ ] System-Theme-Detection (prefers-color-scheme)
- [ ] Theme-Übergangs-Animationen
- [ ] Tests für Theme-Switching, Persistierung und System-Theme

**Akzeptanzkriterien:**
- ✅ Theme-Wechsel funktioniert sofortig
- ✅ Alle UI-Elemente wechseln korrekt das Theme
- ✅ System-Theme wird respektiert
- ✅ Theme bleibt nach Reload erhalten
- ✅ Transitions sind smooth

---

### ✅ Task 3.3: Basis-Tagesleiste
**Geschätzte Zeit:** 3 Tage  
**Priorität:** 🟠 Hoch

**Aufgaben:**
- [ ] `DayProgressTile`-Komponente erstellen (2x1 oder 3x1 Größe)
- [ ] Setup-Dialog implementieren:
  - [ ] Startzeit-Eingabe (HH:MM)
  - [ ] Arbeitszeit-Eingabe (Stunden)
  - [ ] Berechnung der initialen Endzeit
- [ ] Fortschritts-Visualisierung erstellen:
  - [ ] Horizontaler Fortschrittsbalken
  - [ ] Prozentuale Anzeige des Tagesfortschritts
  - [ ] Verbleibende Zeit bis Feierabend
- [ ] Zeit-Berechnungen implementieren:
  - [ ] Aktuelle Arbeitszeit
  - [ ] Verbleibende Arbeitszeit
  - [ ] Prozentsatz des Tagesfortschritts
- [ ] Zeitanzeige-Komponenten erstellen:
  - [ ] Startzeit-Anzeige
  - [ ] Aktuelle Zeit
  - [ ] Geplante Endzeit
- [ ] Automatisches Tagesende-Reset implementieren:
  - [ ] Um Mitternacht Reset der Tagesleiste
  - [ ] Speicherung der Tagesdaten
- [ ] Date-Objekte für Zeitberechnungen
- [ ] Time-Utility-Funktionen
- [ ] `useDayProgress`-Hook
- [ ] Validierung für Zeit-Eingaben
- [ ] Fehlerzustände (ungültige Zeiten)
- [ ] Intervall-Timer für Live-Updates
- [ ] Tests für Zeit-Berechnungen, Validierung und automatisches Reset

**Akzeptanzkriterien:**
- ✅ Tagesfortschritt wird korrekt berechnet und angezeigt
- ✅ Setup-Dialog ist benutzerfreundlich
- ✅ Live-Updates funktionieren zuverlässig
- ✅ Mitternacht-Reset funktioniert automatisch
- ✅ Validierung verhindert ungültige Eingaben

---

## 🚀 Phase 4: Erweiterte Funktionalitäten

### ✅ Task 4.1: Erweiterte Tagesleiste mit Terminen
**Geschätzte Zeit:** 4-5 Tage  
**Priorität:** 🟡 Mittel

**Aufgaben:**
- [ ] `DayProgressTile` um Termin-Visualisierung erweitern
- [ ] Event-Management implementieren:
  - [ ] Termine als Blöcke auf dem Zeitstrahl
  - [ ] Manuelle Termin-Eingabe (Titel, Startzeit, Dauer)
  - [ ] Termin-Bearbeitung und -Löschung
- [ ] Event-Dialog erstellen:
  - [ ] Titel-Eingabe
  - [ ] Startzeit-Picker
  - [ ] Dauer-Eingabe (Minuten/Stunden)
  - [ ] Farb-Auswahl für Termin-Block
- [ ] Pausen-Management implementieren:
  - [ ] Pausen-Eingabe (Startzeit, Endzeit)
  - [ ] Dynamische Anpassung der Gesamtarbeitszeit
  - [ ] Aktualisierung der geplanten Endzeit
- [ ] Alarm-Funktionalität erstellen:
  - [ ] Bildschirm-Blinken bei Termin-Start
  - [ ] Browser-Notification (optional)
  - [ ] Snooze-Funktionalität
- [ ] Timeline-Visualisierung implementieren:
  - [ ] Termine als farbige Blöcke
  - [ ] Überlappende Termine-Darstellung
  - [ ] Aktuelle Zeit-Indikator
- [ ] DayProgress-Datenmodell erweitern
- [ ] Event-Scheduling-Logik
- [ ] Timeline-Komponente
- [ ] Notification API für Browser-Benachrichtigungen
- [ ] Termin-Konflikte-Erkennung
- [ ] Drag & Drop für Termine (optional)
- [ ] Tests für Termin-Management, Pausen-Berechnungen und Alarm-Funktionalität

**Akzeptanzkriterien:**
- ✅ Termine können einfach erstellt und verwaltet werden
- ✅ Timeline zeigt alle Termine übersichtlich an
- ✅ Alarm-System funktioniert zuverlässig
- ✅ Pausen werden korrekt in Arbeitszeit eingerechnet
- ✅ Konflikte werden erkannt und angezeigt

---

### ✅ Task 4.2: Prompt-Bibliothek - Grundstruktur
**Geschätzte Zeit:** 3-4 Tage  
**Priorität:** 🟡 Mittel

**Aufgaben:**
- [ ] `PromptLibraryTile`-Komponente erstellen (2x1 Größe)
- [ ] Kategorie-Management implementieren:
  - [ ] Kategorie-Übersicht als Kachel-Grid
  - [ ] Neue Kategorie erstellen (+Kachel)
  - [ ] Kategorie umbenennen/löschen
- [ ] Kategorie-Ansicht erstellen:
  - [ ] Prompt-Übersicht innerhalb einer Kategorie
  - [ ] Neuen Prompt erstellen (+Kachel)
  - [ ] Zurück zur Kategorie-Übersicht
- [ ] Navigation implementieren:
  - [ ] Breadcrumb-Navigation
  - [ ] Back-Button
  - [ ] Kategorie-zu-Prompt-Navigation
- [ ] Datenstrukturen erstellen:
  - [ ] `Category`-Interface (ID, Name, Prompts)
  - [ ] `Prompt`-Interface (ID, Title, Content, CategoryID)
- [ ] CRUD-Operationen implementieren:
  - [ ] Kategorien erstellen, bearbeiten, löschen
  - [ ] Prompts erstellen, bearbeiten, löschen
- [ ] `PromptLibraryContext` für Zustandsverwaltung
- [ ] Reducer für komplexe Zustandsänderungen
- [ ] Navigation-Stack für Ansichten
- [ ] Wiederverwendbare Card-Komponenten
- [ ] Bestätigungsdialoge für Löschoperationen
- [ ] Suchfunktionalität für Prompts
- [ ] Leere Zustände für neue Kategorien
- [ ] Tests für Navigation, CRUD-Operationen und Zustandsverwaltung

**Akzeptanzkriterien:**
- ✅ Kategorie-Management funktioniert intuitiv
- ✅ Navigation zwischen Ansichten ist flüssig
- ✅ CRUD-Operationen funktionieren zuverlässig
- ✅ Suchfunktionalität findet Prompts schnell
- ✅ Leere Zustände sind benutzerfreundlich

---

### ✅ Task 4.3: Prompt-Bibliothek - Editor und Platzhalter
**Geschätzte Zeit:** 4-5 Tage  
**Priorität:** 🟡 Mittel

**Aufgaben:**
- [ ] `PromptEditor`-Komponente erstellen:
  - [ ] Titel-Eingabe
  - [ ] Rich-Text-Editor für Prompt-Inhalt
  - [ ] Platzhalter-Erstellung durch Textmarkierung
- [ ] Platzhalter-System implementieren:
  - [ ] Text markieren und zu Platzhalter konvertieren
  - [ ] Platzhalter-Namen eingeben
  - [ ] Platzhalter-Syntax: [PLATZHALTER_NAME]
  - [ ] Platzhalter visuell hervorheben
- [ ] Platzhalter-Verwaltung erstellen:
  - [ ] Liste aller Platzhalter im Prompt
  - [ ] Platzhalter umbenennen/löschen
  - [ ] Platzhalter-Validierung (keine Duplikate)
- [ ] Text-Parsing implementieren:
  - [ ] Platzhalter aus Text extrahieren
  - [ ] Text mit Platzhaltern rendern
  - [ ] Platzhalter-Highlighting im Editor
- [ ] Vorschau-Funktionalität erstellen:
  - [ ] Live-Vorschau mit hervorgehobenen Platzhaltern
  - [ ] Syntax-Highlighting für Platzhalter
- [ ] Editor-Funktionen implementieren:
  - [ ] Undo/Redo
  - [ ] Textformatierung (optional)
  - [ ] Speichern/Abbrechen
- [ ] contentEditable oder Text-Area mit Syntax-Highlighting
- [ ] Platzhalter-Regex für Parsing
- [ ] Platzhalter-Utility-Funktionen
- [ ] Editor-Keyboard-Shortcuts
- [ ] Autosave-Funktionalität
- [ ] Platzhalter-Validierung
- [ ] Tests für Platzhalter-Parsing, Editor-Funktionen und Validierung

**Akzeptanzkriterien:**
- ✅ Platzhalter können einfach erstellt und verwaltet werden
- ✅ Editor bietet gute Benutzerfreundlichkeit
- ✅ Syntax-Highlighting funktioniert korrekt
- ✅ Validierung verhindert Duplikate und Fehler
- ✅ Autosave funktioniert zuverlässig

---

### ✅ Task 4.4: Prompt-Bibliothek - Verwendung und Formular
**Geschätzte Zeit:** 3-4 Tage  
**Priorität:** 🟡 Mittel

**Aufgaben:**
- [ ] `PromptUsageForm`-Komponente erstellen:
  - [ ] Dynamisches Formular basierend auf Platzhaltern
  - [ ] Ein Eingabefeld pro Platzhalter
  - [ ] Kontext-Anzeige für jeden Platzhalter
- [ ] Kontext-Hilfe implementieren:
  - [ ] Umgebender Satz wird über leerem Eingabefeld angezeigt
  - [ ] Platzhalter-Name farblich hervorgehoben
  - [ ] Hilfe verschwindet bei Eingabe
- [ ] Prompt-Ersetzung erstellen:
  - [ ] Platzhalter durch Benutzereingaben ersetzen
  - [ ] Generierung des finalen Textes
  - [ ] Kopieren in Zwischenablage
- [ ] Formular-Validierung implementieren:
  - [ ] Pflichtfelder-Validierung
  - [ ] Eingabe-Validierung (falls spezifiziert)
  - [ ] Fehler-Anzeige
- [ ] Prompt-Vorschau erstellen:
  - [ ] Live-Vorschau des generierten Textes
  - [ ] Hervorhebung eingefügter Werte
  - [ ] Vor-/Nach-Vergleich
- [ ] Clipboard-Integration implementieren:
  - [ ] Kopieren-Button für generierten Text
  - [ ] Erfolgsmeldung nach Kopieren
  - [ ] Fallback für ältere Browser
- [ ] Clipboard API für Kopieren
- [ ] Formular-Zustandsverwaltung
- [ ] Prompt-Replacement-Engine
- [ ] Formular-Persistence (Draft-Speicherung)
- [ ] Keyboard-Shortcuts (Ctrl+Enter für Kopieren)
- [ ] Eingabe-Komponenten für verschiedene Datentypen
- [ ] Tests für Formular-Generierung, Prompt-Ersetzung und Clipboard-Integration

**Akzeptanzkriterien:**
- ✅ Formular wird automatisch basierend auf Platzhaltern generiert
- ✅ Kontext-Hilfe ist hilfreich und nicht störend
- ✅ Prompt-Ersetzung funktioniert fehlerfrei
- ✅ Clipboard-Integration funktioniert in allen Browsern
- ✅ Live-Vorschau zeigt Ergebnis sofort an

---

### ✅ Task 4.5: Daten-Analyse-Kachel
**Geschätzte Zeit:** 3 Tage  
**Priorität:** 🟡 Mittel

**Aufgaben:**
- [ ] `DataAnalysisTile`-Komponente erstellen (2x1 Größe)
- [ ] Datenerfassung implementieren:
  - [ ] Tägliche Speicherung von Startzeit und Endzeit
  - [ ] Automatische Erfassung bei Tagesende
  - [ ] Datenstruktur mit Datum, Startzeit, Endzeit
- [ ] Statistik-Berechnungen erstellen:
  - [ ] Durchschnittliche Startzeit
  - [ ] Durchschnittliche Endzeit
  - [ ] Durchschnittliche Arbeitszeit
  - [ ] Trend-Analyse (optional)
- [ ] Zeitraum-Filter implementieren:
  - [ ] "Maximal" (alle verfügbaren Daten)
  - [ ] "30 Tage" (letzten 30 Tage)
  - [ ] Tab-Navigation zwischen Filtern
- [ ] Datenvisualisierung erstellen:
  - [ ] Textuelle Anzeige der Durchschnittswerte
  - [ ]