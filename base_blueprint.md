# Base Blueprint: Tagesbegleiter - Entwicklungsplan

Ein schrittweiser Plan für die testgetriebene Entwicklung der modularen Produktivitäts-Web-App "Tagesbegleiter".

## Entwicklungsstrategie
- **Testgetrieben (TDD):** Tests vor der Implementation.
- **Iterativ:** Kleine, funktionierende Schritte.
- **Kontinuierliche Integration:** Jeder Schritt baut nahtlos auf dem vorherigen auf.
- **Best Practices:** Clean Code, TypeScript, moderne React-Patterns.

---

## Phase 1: Projekt-Grundlagen

### Schritt 1: Projekt-Setup & Architektur
- **Ziel:** Grundlegendes React-Projekt aufsetzen.
- **Kernaufgaben:**
    - Projekt mit Vite, TypeScript, ESLint und Prettier initialisieren.
    - `styled-components` für das Styling integrieren.
    - Basis-Ordnerstruktur anlegen (`src/components`, `hooks`, `types` etc.).

### Schritt 2: Theme-System & Neumorphismus
- **Ziel:** Ein dynamisches Theme-System mit Neumorphismus-Design implementieren.
- **Kernaufgaben:**
    - Light/Dark Mode via `styled-components ThemeProvider` einrichten.
    - Wiederverwendbare neumorphe Basiskomponenten (Button, Card, Container) erstellen.
    - Funktionalität zum Umschalten des Themes implementieren.

### Schritt 3: Grid-System & Layout
- **Ziel:** Ein modulares und responsives Grid-Layout für das Dashboard erstellen.
- **Kernaufgaben:**
    - Layout mit CSS Grid aufbauen (z.B. 5/4/2 Spalten für Desktop/Tablet/Mobile).
    - Responsives Verhalten über einen Custom Hook (`useResponsive`) steuern.
    - Helper-Funktionen für Grid-Berechnungen entwickeln.

---

## Phase 2: State Management und Kachel-System

### Schritt 4: Globales State Management
- **Ziel:** Eine zentrale State-Verwaltung ohne externe Libraries aufbauen.
- **Kernaufgaben:**
    - Globalen State mit `React Context` und dem `useReducer`-Hook implementieren.
    - Typsichere State-Struktur, Actions und Reducer definieren.
    - Custom Hooks für den vereinfachten State-Zugriff (`useAppState`) bereitstellen.

### Schritt 5: Basis-Kachel-Architektur
- **Ziel:** Eine erweiterbare Architektur für Dashboard-Kacheln schaffen.
- **Kernaufgaben:**
    - Ein Basis-Interface (`TileComponent`) und eine Registry für Kachel-Typen definieren.
    - Eine erste Demo-Kachel ("Hello World") erstellen.
    - Kacheln aus dem State im Grid-System rendern.

### Schritt 6: "Shop"-Kachel & Hinzufügen-Funktion
- **Ziel:** Nutzern ermöglichen, neue Kacheln zum Dashboard hinzuzufügen.
- **Kernaufgaben:**
    - Eine "Shop"-Kachel mit Plus-Icon erstellen, die ein Modal öffnet.
    - Ein Auswahl-Modal für verfügbare (noch nicht platzierte) Kacheln implementieren.
    - State-Logik zum Hinzufügen von Kacheln (`ADD_TILE`) implementieren.

---

## Phase 3: Interaktivität und Core-Features

### Schritt 7: Entfernen-Funktion
- **Ziel:** Kacheln aus dem Dashboard entfernen können.
- **Kernaufgaben:**
    - Einen "Remove-Mode" implementieren, der z.B. per Rechtsklick aktiviert wird.
    - Visuelles Feedback (z.B. rotes "X") auf den Kacheln anzeigen.
    - State-Logik zum Entfernen von Kacheln (`REMOVE_TILE`) inklusive Bestätigungsdialog.

### Schritt 8: Lokale Speicherung (localStorage)
- **Ziel:** Den Zustand des Dashboards persistent im Browser speichern.
- **Kernaufgaben:**
    - Den App-State bei Änderungen automatisch (debounced) in `localStorage` speichern.
    - Den gespeicherten State beim Laden der App wiederherstellen (Hydration).
    - Robustes Error-Handling und ein einfaches Versionierungssystem vorsehen.

### Schritt 9: Drag & Drop System
- **Ziel:** Kacheln per Drag & Drop im Grid neu anordnen.
- **Kernaufgaben:**
    - Drag & Drop Funktionalität mit der nativen HTML5 API implementieren.
    - "Snap-to-Grid"-Logik für präzises Platzieren.
    - Visuelles Feedback während des Ziehens und eine `MOVE_TILE`-Action für das State-Update.

---

## Phase 4: Kern-Kacheln Implementation

### Schritt 10: Theme-Switcher-Kachel
- **Ziel:** Eine Kachel zum Umschalten des Themes.
- **Kernaufgaben:**
    - Eine 1x1 Kachel erstellen, die per Klick das Light/Dark-Theme ändert.
    - Passende Icons (Sonne/Mond) je nach aktivem Theme anzeigen.
    - Den gewählten Theme-Status persistent speichern.

### Schritt 11: Schnellnotizen-Kachel
- **Ziel:** Eine Kachel für einfache Textnotizen.
- **Kernaufgaben:**
    - Eine Kachel (z.B. 2x1) mit einem `textarea` für die Texteingabe erstellen.
    - Änderungen automatisch (debounced) speichern.
    - Placeholder-Text und optionalen Zeichenzähler implementieren.

### Schritt 12: Neumorphische Uhr-Kachel
- **Ziel:** Eine visuell ansprechende Uhr-Kachel.
- **Kernaufgaben:**
    - Eine 1x1 Kachel mit digitaler Zeitanzeige implementieren.
    - Einen sekundengenauen Farbverlauf für die Ziffern realisieren.
    - Die Farben über ein Modal konfigurierbar und persistent machen.

### Schritt 13: Tagesleiste-Kachel (Grundstruktur)
- **Ziel:** Die Basis für eine Arbeitstag-Timeline schaffen.
- **Kernaufgaben:**
    - Eine Kachel (z.B. 3x1) mit Setup-Modal für Arbeitsbeginn und -dauer erstellen.
    - Eine einfache Fortschrittsanzeige und die "Gehen-Zeit" berechnen.
    - Einen automatischen Reset um Mitternacht implementieren.

### Schritt 14: Tagesleiste - Event Management
- **Ziel:** Events/Termine zur Tagesleiste hinzufügen.
- **Kernaufgaben:**
    - CRUD-Funktionalität für Events (Titel, Start, Dauer) über ein Modal.
    - Events auf der Timeline visualisieren.
    - Ein einfaches Alarmsystem (z.B. Screen-Flash) bei Event-Start.

### Schritt 15: Tagesleiste - Pausen-System
- **Ziel:** Die Tagesleiste mit Pausen-Management vervollständigen.
- **Kernaufgaben:**
    - Funktionalität zum Hinzufügen von Pausen (Start, Ende).
    - Pausen auf der Timeline visualisieren.
    - Die "Gehen-Zeit"-Berechnung anpassen, um Pausenzeiten zu berücksichtigen.

---

## Phase 5: Polish und Finalisierung

### Schritt 16: Responsive Design Finalisierung
- **Ziel:** Eine optimale Darstellung und Bedienung auf allen Geräten sicherstellen.
- **Kernaufgaben:**
    - Alle Kacheln und Modals für mobile Endgeräte optimieren.
    - Touch-freundliche Interaktionen sicherstellen.
    - Typografie und Abstände für alle Breakpoints anpassen.

### Schritt 17: Performance-Optimierung
- **Ziel:** Die Anwendung schnell und ressourcenschonend machen.
- **Kernaufgaben:**
    - Unnötige Re-Renders mit `React.memo`, `useMemo` und `useCallback` minimieren.
    - Code-Splitting und Lazy Loading für Modals und schwere Komponenten einsetzen.
    - Die Bundle-Größe analysieren und optimieren.

### Schritt 18: Error Handling & Robustheit
- **Ziel:** Die App widerstandsfähig gegen Fehler machen.
- **Kernaufgaben:**
    - `Error Boundaries` zur Isolation von Komponentenfehlern implementieren.
    - Ein globales System für nutzerfreundliche Fehlermeldungen (z.B. Toasts) einrichten.
    - Wiederherstellungsmechanismen für kritische Fehlerzustände schaffen.

### Schritt 19: Testing-Suite Vervollständigung
- **Ziel:** Eine hohe Testabdeckung für langfristige Stabilität gewährleisten.
- **Kernaufgaben:**
    - Unit-Tests für alle Hooks und Utility-Funktionen schreiben.
    - Component-Tests (React Testing Library) für alle UI-Komponenten.
    - Integrationstests für kritische User-Workflows (Kachel hinzufügen/verschieben).
    - Test-Coverage-Reporting in der CI/CD-Pipeline integrieren.
