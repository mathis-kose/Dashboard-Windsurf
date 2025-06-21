Selbstverständlich! Hier ist eine vollständige und gründliche Roadmap im `TODO.md`-Format, die jeden der 19 Schritte aus dem Blueprint in konkrete, abhakbare Aufgaben zerlegt.

---

# Tagesbegleiter - Projekt-Roadmap (TODO)

Dies ist die detaillierte Aufgabenliste für die Entwicklung der "Tagesbegleiter"-Anwendung, basierend auf dem Entwicklungs-Blueprint. Jeder Punkt repräsentiert eine konkrete Aufgabe.

---

## Phase 1: Projekt-Grundlagen

### ☐ Schritt 1: Projekt-Setup & Architektur
- **Setup & Konfiguration**
    - [ ] Neues Vite-Projekt mit dem `react-ts` Template erstellen.
    - [ ] ESLint und Prettier installieren und konfigurieren (`.eslintrc`, `.prettierrc`).
- **Abhängigkeiten**
    - [ ] `styled-components` und `@types/styled-components` installieren.
- **Struktur & Code**
    - [ ] Basis-Ordnerstruktur anlegen: `src/components`, `src/hooks`, `src/types`, `src/utils`, `src/styles`.
    - [ ] `tsconfig.json` mit strikten TypeScript-Regeln (`strict: true`) konfigurieren.
    - [ ] `App.tsx` erstellen, die den Titel "Tagesbegleiter" rendert.
- **Testing & Validierung**
    - [ ] Basis-Test-Setup (z.B. Vitest) konfigurieren.
    - [ ] Sicherstellen, dass die App fehlerfrei startet (`npm run dev`).
    - [ ] Überprüfen, ob der Build-Prozess erfolgreich durchläuft (`npm run build`).

### ☐ Schritt 2: Theme-System & Neumorphismus
- **Theme-Definition**
    - [ ] `src/styles/themes.ts`: Light- und Dark-Theme-Objekte sowie ein TypeScript-Interface für die Theme-Struktur definieren.
    - [ ] `src/styles/GlobalStyle.ts`: Globale CSS-Regeln (Reset, Body-Background, Font) erstellen.
- **Integration**
    - [ ] Den `ThemeProvider` von `styled-components` in `App.tsx` integrieren.
    - [ ] Die `GlobalStyle`-Komponente in `App.tsx` einbinden.
- **Neumorphe Komponenten**
    - [ ] `src/components/ui/neumorphic.ts` (o.ä.) für wiederverwendbare Styled-Components erstellen.
    - [ ] `NeumorphicCard`, `NeumorphicContainer` und `NeumorphicButton` mit `hover`- und `active`-States implementieren.
- **Funktionalität & Testing**
    - [ ] Eine Funktion/Hook zum Umschalten des Themes implementieren.
    - [ ] Einen temporären Button in die UI einbauen, um den Theme-Wechsel zu testen.
    - [ ] Visuell prüfen, ob die neumorphen Schatten und Farben im Light/Dark-Mode korrekt sind.

### ☐ Schritt 3: Grid-System & Layout
- **Komponenten & Styling**
    - [ ] `GridContainer.tsx`-Komponente erstellen, die CSS Grid verwendet.
    - [ ] Media Queries für die Breakpoints (Desktop 5 Spalten, Tablet 4, Mobile 2) definieren.
- **Hooks & Utilities**
    - [ ] `src/hooks/useResponsive.ts`: Custom Hook zur Erkennung des aktuellen Breakpoints erstellen.
    - [ ] `src/types/grid.ts`: TypeScript-Interfaces für Grid-Position und -Größe anlegen.
    - [ ] `src/utils/gridHelpers.ts`: Helper-Funktionen für Grid-Berechnungen (z.B. Snap-to-Grid) vorbereiten.
- **Integration & Testing**
    - [ ] `GridContainer` in `App.tsx` integrieren.
    - [ ] Eine (optional toggelbare) Grid-Visualisierung zur einfacheren Entwicklung hinzufügen.
    - [ ] Testen, dass sich das Layout bei Größenänderung des Fensters korrekt anpasst.

---

## Phase 2: State Management und Kachel-System

### ☐ Schritt 4: Globales State Management
- **Context & Reducer Setup**
    - [ ] `src/context/AppContext.tsx`: React Context und Provider-Komponente erstellen.
    - [ ] `src/types/state.ts`: Interfaces für `AppState`, `AppAction` und den initialen State definieren.
    - [ ] `src/reducers/appReducer.ts`: Reducer-Funktion mit `switch`-Statement für Actions implementieren.
- **Hooks & Integration**
    - [ ] Custom Hooks `useAppState` und `useAppDispatch` für den einfachen Zugriff erstellen.
    - [ ] Die gesamte Anwendung in `App.tsx` mit dem `AppContext.Provider` umschließen.
- **Testing**
    - [ ] Testfall implementieren, der eine Action dispatched und die State-Änderung verifiziert.

### ☐ Schritt 5: Basis-Kachel-Architektur
- **Typen & Interfaces**
    - [ ] `src/types/tiles.ts`: Interfaces für `TileDefinition` (Metadaten) und `PlacedTile` (instanziierte Kachel mit Position/Größe) erstellen.
- **Komponenten**
    - [ ] `src/components/tiles/BaseTile.tsx`: Wrapper-Komponente, die Grid-Positionierung und Styling handhabt.
    - [ ] `src/components/tiles/DemoTile.tsx`: Eine erste einfache "Hello World"-Kachel erstellen.
- **Architektur & Integration**
    - [ ] `src/utils/tileRegistry.ts`: Ein Objekt/Map, das Kachel-IDs auf ihre React-Komponenten abbildet.
    - [ ] `DemoTile` in der `tileRegistry` registrieren.
    - [ ] `GridContainer.tsx` anpassen, um die `placedTiles` aus dem State zu lesen und die Kacheln dynamisch zu rendern.

### ☐ Schritt 6: Shop-Kachel und Add-Funktionalität
- **Komponenten**
    - [ ] `src/components/tiles/ShopTile.tsx`: Eine Kachel mit Plus-Icon erstellen.
    - [ ] `src/components/modals/TileSelectionModal.tsx`: Ein Modal, das verfügbare (nicht platzierte) Kacheln anzeigt.
- **State & Logik**
    - [ ] `ADD_TILE` Action im Reducer implementieren.
    - [ ] Logik in `ShopTile` implementieren, um das `TileSelectionModal` zu öffnen.
    - [ ] Logik im Modal implementieren, die bei Auswahl einer Kachel die `ADD_TILE`-Action auslöst.
- **Hooks & Integration**
    - [ ] `useTileManager.ts` Hook erstellen, der die Logik kapselt (verfügbare Kacheln filtern, hinzufügen).
    - [ ] `ShopTile` in die `tileRegistry` eintragen.
- **Testing**
    - [ ] Workflow testen: Klick auf Shop -> Modal öffnet -> Klick auf Kachel -> Modal schließt -> Neue Kachel erscheint im Grid.

---

## Phase 3: Interaktivität und Core-Features

### ☐ Schritt 7: Remove-Funktionalität
- **UI & UX**
    - [ ] `BaseTile.tsx` erweitern, um auf Rechtsklick zu reagieren.
    - [ ] Einen `removeMode` Flag im UI-State des globalen States einführen.
    - [ ] Ein "X"-Icon auf Kacheln rendern, wenn `removeMode` aktiv ist.
    - [ ] `src/components/ui/ConfirmDialog.tsx` für die Sicherheitsabfrage erstellen.
- **State & Logik**
    - [ ] `REMOVE_TILE` Action im Reducer implementieren.
    - [ ] Klick-Handler für das "X"-Icon implementieren, der den Dialog anzeigt und bei Bestätigung die Action auslöst.
- **Hooks & Testing**
    - [ ] `useContextMenu.ts` Hook für die Rechtsklick-Logik erstellen.
    - [ ] Workflow testen: Rechtsklick -> Remove-Mode aktiv -> Klick "X" -> Dialog -> Bestätigen -> Kachel verschwindet.
    - [ ] Testen: Entfernte Kachel erscheint wieder im `TileSelectionModal`.

### ☐ Schritt 8: localStorage Integration
- **Hooks & Utilities**
    - [ ] `src/utils/storage.ts`: `saveState` und `loadState` mit `try-catch`-Blöcken implementieren.
    - [ ] `src/hooks/useAutoSave.ts`: Hook, der den State überwacht und debounced speichert.
- **Integration**
    - [ ] `loadState` beim App-Start aufrufen, um den initialen State zu hydratisieren.
    - [ ] `useAutoSave` Hook in der Haupt-App-Komponente aufrufen.
    - [ ] Ein Versionierungsfeld zum gespeicherten State-Objekt hinzufügen.
- **Testing**
    - [ ] Testen: Layout ändern -> Seite neu laden -> Änderungen sind persistent.
    - [ ] Testen: `localStorage` leeren -> App startet mit Default-Zustand.

### ☐ Schritt 9: Drag & Drop System
- **Event Handling**
    - [ ] `BaseTile.tsx`: `draggable=true` und `onDragStart`-Handler hinzufügen.
    - [ ] `GridContainer.tsx`: `onDragOver` (mit `preventDefault`) und `onDrop`-Handler hinzufügen.
- **Logik & State**
    - [ ] `onDragStart`: ID der gezogenen Kachel speichern (z.B. via `dataTransfer`).
    - [ ] `onDrop`: Mauskoordinaten in die neue Grid-Position umrechnen.
    - [ ] `MOVE_TILE` Action und Reducer-Logik implementieren, um die Position zu aktualisieren.
- **UI & UX**
    - [ ] CSS für visuelles Feedback während des Drag-Vorgangs (z.B. Opazität) hinzufügen.
    - [ ] CSS-Transitions für eine flüssige Bewegung der Kachel nach dem Drop einrichten.
- **Testing**
    - [ ] Testen: Kachel kann an eine neue, leere Position gezogen werden. Die Position wird im State aktualisiert.

---

## Phase 4: Kern-Kacheln Implementation

### ☐ Schritt 10: Theme-Switcher-Kachel
- **Komponente & UI**
    - [ ] `src/components/tiles/ThemeSwitcherTile.tsx` erstellen (Größe 1x1).
    - [ ] SVG-Icons für Sonne und Mond integrieren.
    - [ ] Logik zum bedingten Rendern des richtigen Icons basierend auf dem aktiven Theme.
- **Funktionalität & State**
    - [ ] `onClick`-Handler implementieren, der die Theme-Umschaltfunktion aufruft.
    - [ ] Den Theme-Status im `localStorage` persistieren (z.B. als Teil des UI-States).
    - [ ] Kachel in `tileRegistry` registrieren.
- **Testing**
    - [ ] Testen: Klick auf Kachel wechselt Theme. Icon ändert sich. Nach Neuladen bleibt das Theme erhalten.

### ☐ Schritt 11: Schnellnotizen-Kachel
- **Komponente & UI**
    - [ ] `src/components/tiles/QuickNotesTile.tsx` (Größe 2x1) mit `<textarea>` erstellen.
    - [ ] Styling für Placeholder-Text und optionalen Zeichenzähler hinzufügen.
- **Funktionalität & State**
    - [ ] Den Notizinhalt im State der jeweiligen `PlacedTile` speichern (Interface in `types/tiles.ts` erweitern).
    - [ ] `onChange`-Handler mit debounced Auto-Save für die `<textarea>` implementieren.
    - [ ] Kachel in `tileRegistry` registrieren.
- **Testing**
    - [ ] Testen: Text eingeben -> kurz warten -> Seite neu laden -> Text ist noch da.

### ☐ Schritt 12: Neumorphische Uhr-Kachel
- **Komponente & Logik**
    - [ ] `src/components/tiles/ClockTile.tsx` (Größe 1x1) erstellen.
    - [ ] `useEffect` mit `setInterval` verwenden, um die Zeit sekundengenau zu aktualisieren.
    - [ ] `src/utils/colorUtils.ts`: Funktion zur Interpolation zwischen zwei Farben implementieren.
- **Konfiguration & UI**
    - [ ] `src/components/modals/ColorPickerModal.tsx` erstellen.
    - [ ] Einen Button auf der Kachel hinzufügen, der das Modal öffnet.
    - [ ] Start- und Endfarbe im State der Kachel speichern und persistieren.
- **Integration & Testing**
    - [ ] Kachel in `tileRegistry` registrieren.
    - [ ] Testen: Uhrzeit ist korrekt. Farbverlauf ändert sich. Farbkonfiguration wird gespeichert.

### ☐ Schritt 13: Tagesleiste-Kachel - Grundstruktur
- **Komponenten & UI**
    - [ ] `src/components/tiles/DayBarTile.tsx` (Größe 3x1) erstellen.
    - [ ] `src/components/modals/DayBarSetupModal.tsx` für Startzeit und Arbeitsdauer erstellen.
    - [ ] Eine einfache Progress-Bar-Komponente implementieren.
- **Logik & State**
    - [ ] `src/utils/timeUtils.ts` für Zeitberechnungen anlegen.
    - [ ] `useDayBar.ts` Hook zur Kapselung der Logik erstellen (Fortschritt, "Gehen-Zeit").
    - [ ] Kachel-State für Konfiguration (Start, Dauer) definieren und persistieren.
    - [ ] `useEffect`-Logik für den Reset um Mitternacht implementieren.
- **Testing**
    - [ ] Testen: Setup-Modal speichert Daten korrekt. Fortschrittsanzeige und "Gehen-Zeit" sind plausibel.

### ☐ Schritt 14: Tagesleiste - Events Management
- **Komponenten & UI**
    - [ ] `src/components/modals/EventModal.tsx` für das Hinzufügen/Bearbeiten von Events.
    - [ ] `src/components/ui/Timeline.tsx` zur Visualisierung der Events auf der Leiste.
- **Logik & State**
    - [ ] `useDayBar.ts` Hook erweitern, um ein Array von Events zu verwalten (CRUD-Operationen).
    - [ ] Event-Daten im State der `DayBarTile` persistieren.
    - [ ] `src/utils/alarmUtils.ts`: Logik für einen visuellen Alarm bei Event-Start implementieren.
- **Testing**
    - [ ] Testen: Events können hinzugefügt, bearbeitet und gelöscht werden. Sie erscheinen korrekt auf der Timeline.

### ☐ Schritt 15: Tagesleiste - Pausen-System
- **Komponenten & UI**
    - [ ] `src/components/modals/BreakModal.tsx` zum Erfassen von Pausen.
    - [ ] `Timeline.tsx` erweitern, um Pausenblöcke darzustellen.
- **Logik & State**
    - [ ] `useDayBar.ts` und `timeUtils.ts` erweitern, um Pausen in der "Gehen-Zeit"-Berechnung zu berücksichtigen.
    - [ ] Pausen-Daten im State der Kachel persistieren.
    - [ ] Tagesstatistiken (Gesamtarbeitszeit, Pausenzeit etc.) berechnen und anzeigen.
- **Testing**
    - [ ] Testen: Hinzugefügte Pausen verschieben die "Gehen-Zeit" korrekt nach hinten.

---

## Phase 5: Polish und Finalisierung

### ☐ Schritt 16: Responsive Design Finalisierung
- **Anpassungen**
    - [ ] Jede einzelne Kachel und Komponente auf Mobile- und Tablet-Breakpoints prüfen und stylen.
    - [ ] Alle Modals für eine gute Bedienbarkeit auf kleinen Bildschirmen optimieren.
    - [ ] Schriftgrößen und Abstände responsiv gestalten.
- **Interaktionen**
    - [ ] Sicherstellen, dass Drag & Drop auch auf Touch-Geräten (ggf. mit polyfill/Anpassung) funktioniert oder eine Alternative angeboten wird.
    - [ ] Alle Klick-Bereiche ausreichend groß für Touch-Bedienung gestalten.
- **Testing**
    - [ ] Manuelle Tests auf echten Geräten oder mit den Entwicklertools des Browsers für alle Breakpoints durchführen.

### ☐ Schritt 17: Performance-Optimierung
- **Memoization**
    - [ ] Komponenten, die sich nicht oft ändern, mit `React.memo` umschließen (z.B. Kacheln).
    - [ ] `useMemo` für teure Berechnungen und `useCallback` für als Prop übergebene Funktionen verwenden.
- **Code-Splitting & Bundling**
    - [ ] Modals und ggf. selten genutzte Kacheln mit `React.lazy()` und `<Suspense>` nachladen.
    - [ ] Bundle-Analyse-Tool (z.B. `vite-plugin-visualizer`) einrichten und große Abhängigkeiten identifizieren/optimieren.
- **Testing**
    - [ ] Mit React DevTools Profiler die Anzahl der Re-Renders vor und nach der Optimierung vergleichen.

### ☐ Schritt 18: Error Handling und Robustheit
- **Implementierung**
    - [ ] `src/components/ErrorBoundary.tsx` erstellen und an strategischen Stellen (z.B. um den `GridContainer`) platzieren.
    - [ ] `src/components/ui/Toast.tsx` für nicht-kritische Fehlermeldungen erstellen.
    - [ ] `try-catch`-Blöcke um kritische Operationen (z.B. `localStorage`-Zugriff, State-Parsing) legen.
- **Integration**
    - [ ] Ein System schaffen, um Fehler an den Nutzer zu kommunizieren (z.B. über Toasts oder Error-Boundary-Fallback-UI).
    - [ ] Einen "Reset"-Button in der Error-Fallback-UI anbieten, der z.B. den `localStorage` leert.
- **Testing**
    - [ ] Manuell Fehler provozieren (z.B. ungültige Daten in `localStorage` schreiben), um das Verhalten zu testen.

### ☐ Schritt 19: Testing-Suite Vervollständigung
- **Unit & Integration Tests**
    - [ ] Unit-Tests für alle Funktionen in `src/utils/` und alle komplexen Hooks in `src/hooks/` schreiben.
    - [ ] Component-Tests (mit React Testing Library) für jede Kachel und jede UI-Komponente erstellen.
    - [ ] Integrationstests schreiben, die ganze User-Flows abdecken (z.B. Kachel hinzufügen -> verschieben -> Inhalt ändern -> löschen).
- **E2E & CI/CD**
    - [ ] (Optional) Ein E2E-Test-Framework (Cypress, Playwright) einrichten und kritische Pfade testen.
    - [ ] Test-Skripte und Coverage-Report in die CI/CD-Pipeline (z.B. GitHub Actions) integrieren.
- **Validierung**
    - [ ] Sicherstellen, dass die Test-Coverage ein vordefiniertes Ziel (z.B. >85%) erreicht.
