# Spezifikation: Modulare Produktivitäts-Web-App "Tagesbegleiter" - Basisversion

**Version:** 1.0 (Basis)
**Datum:** 21. Juni 2025
**Status:** Entwicklungsfertig

## 1. Projektübersicht

### 1.1 Zielsetzung
Entwicklung einer clientseitigen Web-App als modulares Dashboard für Wissensarbeiter. Die Basisversion fokussiert sich auf die Kernfunktionalitäten: modulares Layout-System, grundlegende Produktivitäts-Widgets und lokale Datenpersistierung.

### 1.2 Zielgruppe
Wissensarbeiter am Desktop-PC, die eine zentrale, ästhetisch ansprechende Oberfläche zur Organisation ihres Arbeitstages suchen.

### 1.3 Kern-Features (Basisversion)
- Modulares Drag & Drop Dashboard
- Neumorphisches Design mit Light/Dark Mode
- Lokale Datenspeicherung (localStorage)
- 4 grundlegende Kachel-Typen
- Responsive Desktop-Layout

## 2. Architektur & Technologie-Stack

### 2.1 Frontend-Technologie
- **Framework:** React 18+ mit TypeScript
- **Styling:** CSS-in-JS (styled-components) für Neumorphismus
- **State Management:** React Context + useReducer für globalen State
- **Build Tool:** Vite für schnelle Entwicklung
- **Responsivität:** CSS Grid + Flexbox

### 2.2 Datenpersistierung
- **Primär:** Browser localStorage für alle Benutzerdaten
- **Auto-Save:** Automatisches Speichern bei jeder Änderung
- **Datenformat:** JSON-Strukturen mit Versionierung

### 2.3 Architektur-Prinzipien
```
src/
├── components/
│   ├── common/          # Wiederverwendbare UI-Komponenten
│   ├── tiles/           # Kachel-Komponenten
│   └── layout/          # Layout-Management
├── hooks/               # Custom React Hooks
├── utils/               # Hilfsfunktionen
├── types/               # TypeScript Definitionen
└── styles/              # Globale Styles & Themes
```

## 3. Design-System

### 3.1 Neumorphismus-Spezifikation
```css
/* Basis-Eigenschaften für alle UI-Elemente */
.neumorphic-element {
  background: var(--surface-color);
  border-radius: 12px;
  box-shadow: 
    8px 8px 16px var(--shadow-dark),
    -8px -8px 16px var(--shadow-light);
  border: none;
}

/* Gedrückt-Effekt für interaktive Elemente */
.neumorphic-pressed {
  box-shadow: 
    inset 4px 4px 8px var(--shadow-dark),
    inset -4px -4px 8px var(--shadow-light);
}
```

### 3.2 Farbschema
```typescript
const lightTheme = {
  surface: '#e0e0e0',
  shadowLight: '#ffffff',
  shadowDark: '#bebebe',
  accent: '#007bff', // Benutzer-konfigurierbar
  text: '#333333'
};

const darkTheme = {
  surface: '#2d2d2d',
  shadowLight: '#404040',
  shadowDark: '#1a1a1a',
  accent: '#66b3ff', // Benutzer-konfigurierbar
  text: '#ffffff'
};
```

### 3.3 Grid-System
- **Basis-Einheit:** 120px × 120px
- **Gap:** 16px zwischen Kacheln
- **Verfügbare Größen:** 1×1, 2×1, 3×1 Grid-Einheiten
- **Responsive Breakpoints:** 
  - Desktop: > 1200px (5 Spalten)
  - Tablet: 768px - 1199px (4 Spalten)
  - Mobile: < 768px (2 Spalten)

## 4. Kern-Komponenten

### 4.1 Layout-Management

#### Dashboard-Container
```typescript
interface DashboardState {
  tiles: PlacedTile[];
  availableTiles: TileType[];
  theme: 'light' | 'dark';
  gridConfig: GridConfig;
}

interface PlacedTile {
  id: string;
  type: TileType;
  position: { x: number; y: number };
  size: { width: number; height: number };
  config?: Record<string, any>;
}
```

#### Drag & Drop System
- **Bibliothek:** react-dnd für Drag & Drop
- **Verhalten:** Kacheln "snappen" zu Grid-Positionen
- **Feedback:** Visueller Schatten beim Hovern über gültige Drop-Zonen

### 4.2 Kachel-Verwaltung

#### Shop-Kachel
```typescript
interface ShopTile {
  type: 'shop';
  size: { width: 1, height: 1 };
  config: {
    availableTiles: TileType[];
  };
}
```

**Funktionalität:**
- Klick öffnet Overlay mit verfügbaren Kacheln
- Kachel-Auswahl "heftet" Kachel an Cursor
- Platzierung durch Klick auf freie Grid-Position
- Einzigartigkeits-Prüfung vor Platzierung

#### Entfernen-System
- Rechtsklick aktiviert Entfernen-Modus
- Rotes X-Icon erscheint auf Kachel
- Bestätigung durch Klick auf X
- Kachel wird zu verfügbaren Kacheln zurückgegeben

### 4.3 Basis-Kacheln (4 Typen)

#### 4.3.1 Tagesleiste-Kachel
```typescript
interface DayBarTile {
  type: 'daybar';
  size: { width: 3, height: 1 };
  config: {
    startTime?: string; // HH:MM Format
    workDuration: number; // Stunden
    events: Event[];
    breaks: Break[];
  };
}

interface Event {
  id: string;
  title: string;
  startTime: string;
  duration: number; // Minuten
  triggered: boolean;
}

interface Break {
  id: string;
  startTime: string;
  endTime: string;
}
```

**Kern-Features:**
- Setup: Startzeit + Arbeitszeit eingeben
- Fortschrittsbalken zeigt Tagesfortschritt
- Events: Manuell hinzufügen (Titel + Dauer)
- Pausen: Nachträglich erfassen (Start + Ende)
- Alarm: Bildschirm blinkt bei Event-Start
- Auto-Reset um Mitternacht

**Berechnungen:**
```typescript
// Gehen-Zeit Berechnung
const calculateEndTime = (startTime: string, workDuration: number, totalBreakTime: number) => {
  const start = parseTime(startTime);
  const workMinutes = workDuration * 60;
  const endMinutes = start.minutes + workMinutes + totalBreakTime;
  return formatTime(endMinutes);
};
```

#### 4.3.2 Neumorphische Uhr
```typescript
interface ClockTile {
  type: 'clock';
  size: { width: 1, height: 1 };
  config: {
    startColor: string; // HEX
    endColor: string;   // HEX
  };
}
```

**Funktionalität:**
- Digitale Zeitanzeige (HH:MM)
- Sekundengenauer Farbverlauf
- Klick öffnet Farbwähler-Modal
- Smooth Transition zwischen Farben

**Farbverlauf-Algorithmus:**
```typescript
const calculateGradientColor = (startColor: string, endColor: string, seconds: number) => {
  const progress = seconds / 59;
  return interpolateColor(startColor, endColor, progress);
};
```

#### 4.3.3 Design-Umschalter
```typescript
interface ThemeTile {
  type: 'theme';
  size: { width: 1, height: 1 };
  config: {
    currentTheme: 'light' | 'dark';
  };
}
```

**Funktionalität:**
- Toggle zwischen Light/Dark Mode
- Sonnen-/Mond-Icon je nach Modus
- Sofortige Theme-Anwendung
- Persistierung in localStorage

#### 4.3.4 Schnellnotizen-Kachel
```typescript
interface QuickNotesTile {
  type: 'quicknotes';
  size: { width: 2, height: 1 };
  config: {
    notes: string;
    lastModified: Date;
  };
}
```

**Funktionalität:**
- Einfaches Textfeld für schnelle Notizen
- Auto-Save bei Änderungen
- Minimalistisches Design
- Character-Counter (optional)

## 5. Datenmodell & Persistierung

### 5.1 localStorage Schema
```typescript
interface AppData {
  version: string;
  dashboard: {
    tiles: PlacedTile[];
    theme: 'light' | 'dark';
    lastModified: Date;
  };
  daybar: {
    currentDay: string; // YYYY-MM-DD
    startTime?: string;
    workDuration: number;
    events: Event[];
    breaks: Break[];
  };
  clock: {
    startColor: string;
    endColor: string;
  };
  quicknotes: {
    content: string;
    lastModified: Date;
  };
}
```

### 5.2 Speicher-Strategien
```typescript
// Auto-Save Hook
const useAutoSave = (data: any, key: string, delay: number = 500) => {
  const debouncedSave = useMemo(
    () => debounce((data) => localStorage.setItem(key, JSON.stringify(data)), delay),
    [key, delay]
  );
  
  useEffect(() => {
    debouncedSave(data);
  }, [data, debouncedSave]);
};
```

### 5.3 Daten-Migration
```typescript
const migrateData = (currentVersion: string, targetVersion: string, data: any) => {
  // Versionsbasierte Datenmigration für zukünftige Updates
  const migrations = {
    '1.0-to-1.1': (data) => { /* Migration Logic */ }
  };
  
  return migrations[`${currentVersion}-to-${targetVersion}`]?.(data) || data;
};
```

## 6. State Management

### 6.1 Globaler State
```typescript
interface AppState {
  dashboard: DashboardState;
  tiles: Record<string, any>; // Kachel-spezifische States
  ui: {
    dragMode: boolean;
    removeMode: boolean;
    activeModal?: string;
  };
}

type AppAction = 
  | { type: 'ADD_TILE'; payload: { tileType: TileType; position: Position } }
  | { type: 'REMOVE_TILE'; payload: { tileId: string } }
  | { type: 'MOVE_TILE'; payload: { tileId: string; position: Position } }
  | { type: 'UPDATE_TILE_CONFIG'; payload: { tileId: string; config: any } }
  | { type: 'TOGGLE_THEME' }
  | { type: 'SET_REMOVE_MODE'; payload: boolean };
```

### 6.2 Custom Hooks
```typescript
// Kachel-Management
const useTileManager = () => {
  const { state, dispatch } = useAppContext();
  
  const addTile = (type: TileType, position: Position) => {
    dispatch({ type: 'ADD_TILE', payload: { tileType: type, position } });
  };
  
  const removeTile = (id: string) => {
    dispatch({ type: 'REMOVE_TILE', payload: { tileId: id } });
  };
  
  return { addTile, removeTile, tiles: state.dashboard.tiles };
};

// Tagesleiste-Management
const useDayBar = () => {
  const [dayBarData, setDayBarData] = useState<DayBarData>();
  
  const addEvent = (event: Event) => { /* Logic */ };
  const addBreak = (breakData: Break) => { /* Logic */ };
  const calculateProgress = () => { /* Logic */ };
  
  return { dayBarData, addEvent, addBreak, calculateProgress };
};
```

## 7. Fehlerbehandlung & Validierung

### 7.1 Eingabe-Validierung
```typescript
const validateTimeInput = (time: string): boolean => {
  return /^([0-1]?[0-9]|2[0-3]):[0-5][0-9]$/.test(time);
};

const validateBreakTimes = (start: string, end: string): ValidationResult => {
  if (!validateTimeInput(start) || !validateTimeInput(end)) {
    return { valid: false, error: 'Ungültiges Zeitformat' };
  }
  
  if (parseTime(end) <= parseTime(start)) {
    return { valid: false, error: 'Endzeit muss nach Startzeit liegen' };
  }
  
  return { valid: true };
};
```

### 7.2 Error Boundaries
```typescript
const TileErrorBoundary: React.FC<{ children: React.ReactNode }> = ({ children }) => {
  const [hasError, setHasError] = useState(false);
  
  if (hasError) {
    return (
      <div className="tile-error">
        <p>Diese Kachel konnte nicht geladen werden.</p>
        <button onClick={() => setHasError(false)}>Erneut versuchen</button>
      </div>
    );
  }
  
  return <>{children}</>;
};
```

### 7.3 localStorage Fehlerbehandlung
```typescript
const safeLocalStorageOperation = (operation: () => void, fallback?: () => void) => {
  try {
    operation();
  } catch (error) {
    console.warn('localStorage operation failed:', error);
    fallback?.();
    // Optional: Nutzer über eingeschränkte Funktionalität informieren
  }
};
```

## 8. Performance-Optimierung

### 8.1 Rendering-Optimierung
- React.memo für Kachel-Komponenten
- useMemo für teure Berechnungen
- useCallback für Event Handler
- Lazy Loading für Modal-Komponenten

### 8.2 Debouncing
```typescript
// Auto-Save Debouncing
const debouncedSave = useCallback(
  debounce((data) => saveToLocalStorage(data), 500),
  []
);
```

## 9. Testplan

### 9.1 Unit Tests
```typescript
describe('DayBar Calculations', () => {
  test('calculates end time correctly with breaks', () => {
    const result = calculateEndTime('09:00', 8, 60); // 1h Pause
    expect(result).toBe('18:00');
  });
  
  test('validates time input format', () => {
    expect(validateTimeInput('09:30')).toBe(true);
    expect(validateTimeInput('25:00')).toBe(false);
  });
});

describe('Color Interpolation', () => {
  test('interpolates colors correctly', () => {
    const result = interpolateColor('#ff0000', '#0000ff', 0.5);
    expect(result).toBe('#800080');
  });
});
```

### 9.2 Integration Tests
```typescript
describe('Tile Management', () => {
  test('adds tile to dashboard', () => {
    render(<Dashboard />);
    
    // Shop-Kachel klicken
    fireEvent.click(screen.getByTestId('shop-tile'));
    
    // Uhr-Kachel auswählen
    fireEvent.click(screen.getByTestId('clock-tile-option'));
    
    // Auf freie Position klicken
    fireEvent.click(screen.getByTestId('grid-position-1-1'));
    
    expect(screen.getByTestId('clock-tile')).toBeInTheDocument();
  });
});
```

### 9.3 E2E Test Szenarien
1. **Tagesablauf-Test:**
   - App öffnen
   - Startzeit eingeben (09:00)
   - Arbeitszeit festlegen (8h)
   - Event hinzufügen ("Meeting", 10:00, 60min)
   - Pause eintragen (12:00-13:00)
   - Gehen-Zeit prüfen (sollte 18:00 sein)
   - Page Reload → Daten sollten erhalten bleiben

2. **Layout-Test:**
   - Verschiedene Kacheln hinzufügen
   - Drag & Drop zwischen Positionen
   - Kachel entfernen
   - Theme wechseln
   - Browser-Größe ändern → Layout sollte responsive reagieren

## 10. Entwicklungs-Roadmap

### Phase 1: Grundgerüst (Woche 1-2)
- [ ] Projekt-Setup (React + TypeScript + Vite)
- [ ] Neumorphismus Design System
- [ ] Grid-Layout System
- [ ] Basis State Management

### Phase 2: Kachel-System (Woche 3-4)
- [ ] Shop-Kachel mit Add/Remove Funktionalität
- [ ] Drag & Drop Implementation
- [ ] localStorage Integration
- [ ] Theme-System

### Phase 3: Basis-Kacheln (Woche 5-7)
- [ ] Tagesleiste-Kachel (ohne Outlook)
- [ ] Neumorphische Uhr mit Farbverlauf
- [ ] Design-Umschalter
- [ ] Schnellnotizen-Kachel

### Phase 4: Polish & Testing (Woche 8)
- [ ] Responsive Design verfeinern
- [ ] Error Handling implementieren
- [ ] Tests schreiben
- [ ] Performance-Optimierung

## 11. Technische Anforderungen

### 11.1 Browser-Kompatibilität
- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

### 11.2 Performance-Ziele
- Initial Load: < 3 Sekunden
- Kachel-Interaktion: < 100ms Response
- Drag & Drop: 60fps
- Bundle Size: < 500KB (gzipped)

### 11.3 Accessibility
- ARIA-Labels für alle interaktiven Elemente
- Keyboard-Navigation Support
- High Contrast Mode Unterstützung
- Screen Reader Kompatibilität

---

**Diese Basisversion bildet das solide Fundament für Ihre modulare Produktivitäts-App. Nach erfolgreicher Implementierung können die geplanten Updates (Prompt-Bibliothek, Cloud-Sync, Outlook-Integration, Daten-Analyse) schrittweise hinzugefügt werden.**