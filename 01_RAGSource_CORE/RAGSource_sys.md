# RAGSource: System-Definitionen (LLM-optimiert)

**Version:** 1.0  
**Zweck:** Definitionen, Regeln, Constraints für LLM-Navigation  
**Für Details:** Siehe RAGSource_sys_reference.md (optional, on-demand)

---

## 1. Architektur - Überblick

### RAGSource Architektur

```
RAGSource_[projekt]/                  ← Basisverzeichnis
├── 01_RAGSource_CORE/                ← Generische RAGSource-Infrastruktur
│   ├── RAGSource_Masterprompt.md     ← Prompt-Vorlage für LLM
│   ├── RAGSource_sys.md              ← Systembeschreibung für LLM-Kontext
│   └── RAGSource_sys_reference.md    ← Detail-Doku (optional, on-demand)
├── 02_RAGSource_PROJECT/             
│   ├── Projektinitialisierung.md     ← Use-Case spezifische Systemerweiterungen
├── 10_REGELUNGSRAHMEN/
│   └── [Wissensmodule]/
│       └── RAG-Index.md              ← PFLICHT!
└── 20_WIKI/
    └── [Wissensmodule]/
        └── RAG-Index.md              ← PFLICHT!
        
30_LOKALE_DATEN/                      ← externes Repo (z.B. Sharepoint, NextCloud)
├── 03_RAGSource_LOCAL/
│   └── LOCAL-DATA-Index.md           ← PFLICHT! Initialisierung lokales Repo
├── [Wissensmodul]/
│   └── RAG-Index.md                  ← PFLICHT!
└── [Wissensmodul]/
    └── RAG-Index.md                  ← PFLICHT!
```

**Lokale Daten:**

- **Speicherort:** Separates Repository (vertraulich, DSGVO-geschützt)
- **Anbindung:** Sharepoint/NextCloud/OneDrive/etc.

### Wissensmodul-Registrierung

**Mechanismus:** RAG-Index-Dateien werden im Schritt 2 des Systemprompts registriert.

---

## 2. Kern-Definitionen

| Begriff              | Definition                                                 | Kennzeichen                                      |
| -------------------- | ---------------------------------------------------------- | ------------------------------------------------ |
| **Wissensmodul**     | Thematische Gruppe von Artikeln mit gemeinsamer Gültigkeit | PFLICHT: RAG-Index.md                            |
| **RAG-Index**        | Navigationsdatei im Wissensmodul                           | Keywords + Fragen + Metadaten                    |
| **Wissensartikel**   | Einzeldokument mit Fachwissen                              | Frontmatter + Content + Querverweise             |
| **Gültigkeit**       | Räumlich-rechtlicher Geltungsbereich                       | Hierarchie: Bund → Land → Kreis → Gemeinde → Org |
| **Säule**            | Hauptkategorie im Projekt                                  | Regelungsrahmen / Wiki (Lokale Daten extern)     |
| **LOCAL-DATA-Index** | Zentrale Registrierung lokaler RAG-Indizes                 | Im externen Repo `30_LOKALE_DATEN/`              |

---

## 3. Säulen - Eigenschaften-Matrix

| Säule               | Inhalt                                | Zugriff         | Änderbar              | Zitierbar            | Beispiele                   |
| ------------------- | ------------------------------------- | --------------- | --------------------- | -------------------- | --------------------------- |
| **Regelungsrahmen** | Gesetze, Verordnungen, Normen         | Öffentlich      | ❌ NIE                 | ✅ Ja                 | FwG BW, GemO, DIN           |
| **Wiki**            | Praxis, Anleitungen, Interpretationen | Öffentlich      | ⚠️ Durch Contributors | ⚠️ Mit Einschränkung | Checklisten, Best Practices |
| **Lokale Daten**    | Intern, vertraulich                   | DSGVO-geschützt | ✅ Ja                  | ❌ Nein               | Einsatzberichte, Personal   |

### Ordner-Struktur

- **10_REGELUNGSRAHMEN/**: Verbindliche Quellen
- **20_WIKI/**: Praxiswissen
- **Lokale Daten**: Über Schritt 2 "Systemdaten laden" eingebunden

---

## 4. RAG-Index - Pflicht-Struktur

**Speicherort:** `[Wissensmodul]/RAG-Index.md`

**Aufbau pro Artikel:**

```markdown
### [Artikel-Titel]

**Datei:** `Artikelname.md`
**Quelle:** [URL/Referenz]
**Status:** published
**Gültigkeit:** [Scope]

**Tags:**
- typ-rechtsnorm
- thema-recht
- ebene-land

**Keywords:** [umfassend! Alle Synonyme, Abkürzungen, Fachbegriffe]

**Typische Fragen:** [Minimum 8, umgangssprachlich!]
- "Wie mache ich X?"
- "Wann muss ich Y zahlen?"
- "Kostenersatz Feuerwehr?"

**Querverweise:**
- [Verwandter Artikel A](../ModulX/ArtikelA.md)
- [Verwandter Artikel B](ArtikelB.md)
```

**Kritisch:** 
- Keywords = Findbarkeit (so viele wie möglich für Qualität, so wenig wie nötig für Performance)
- Fragen = RAG-Performance (umgangssprachlich, wie User wirklich fragt!)

---

## 5. Metadaten - Tag-System

### System-Tags (Basis-Set)

**Typ (Dokumentart):**
- `typ-rechtsnorm`: Gesetze, Verordnungen
- `typ-wissensartikel`: Wiki-Artikel
- `typ-template`: Vorlagen

**Status (Bearbeitungsstand):**
- `status-draft`: Entwurf
- `status-review`: In Prüfung
- `status-published`: Veröffentlicht ✅
- `status-deprecated`: Veraltet ⚠️

**Ebene (Gültigkeitsbereich):**
- `ebene-bund`: Bundesebene
- `ebene-land`: Landesebene
- `ebene-kreis`: Kreisebene
- `ebene-gemeinde`: Gemeindeebene
- `ebene-org`: Organisationsebene

**Thema (Fachbereich):**
- `thema-recht`: Rechtliche Themen
- `thema-verwaltung`: Verwaltung
- `thema-feuerwehr`: Feuerwehrspezifisch
- etc. (projekt-spezifisch in Taxonomie.md)

**Quelle (Herkunft):**
- `quelle-gesetz`: Gesetzestext
- `quelle-satzung`: Satzung
- `quelle-verordnung`: Verordnung
- `quelle-wiki`: Wiki-Artikel

### Projekt-Tags

Definiert in: `[Projekt]/02_RAGSource_PROJECT/Taxonomie.md`

**Regel:** Gleicher Begriff = gleiche Schreibweise! Tags konsistent verwenden.

---

## 6. Hierarchien - Prioritäten

### Quellen-Hierarchie

```
1. Regelungsrahmen (10_REGELUNGSRAHMEN/)
   ├─ Verbindlich
   ├─ Originaltext 1:1
   └─ NIE paraphrasieren!
   
2. Lokale Daten (30_LOKALE_DATEN/ - externes Repo) 
   ├─ Zugriffsprüfung erforderlich 
   ├─ Org-spezifisch verbindlich 
   └─ Enthält vertrauliche und personenbezogene Daten
   
3. Wiki (20_WIKI/)
   ├─ Interpretation
   ├─ Beispiele erlaubt
   └─ Eigene Formulierung möglich
   
4. LLM-Wissen
   ├─ Nur ergänzend
   └─ Immer kennzeichnen
   
5. WebSearch
   ├─ Nur bei RAGSource-Lücken
   └─ Quellen angeben
```

### Rechts-Hierarchie (bei Widersprüchen)

```
Bundesrecht
    ↓
Landesrecht
    ↓
Kreisrecht
    ↓
Gemeinderecht
    ↓
Organisationsrecht
```

**Regel:** Höhere Ebene schlägt niedrigere Ebene

---

## 7. Constraints - MUSS-Regeln

| ID | Regel | Anwendung | Bei Verstoß |
|----|-------|-----------|-------------|
| **C1** | Originaltext-Pflicht | Regelungsrahmen: NIE paraphrasieren | Antwort ungültig |
| **C2** | Gültigkeit explizit | Immer im Frontmatter angeben | Artikel invalid |
| **C3** | Tag-Konsistenz | Taxonomie.md verwenden | Findbarkeit broken |
| **C4** | Chunk-Friendly | Jeder Abschnitt eigenständig verständlich | RAG ineffizient |
| **C5** | Quellen-Pflicht | IMMER angeben oder "unsicher" sagen | Nicht vertrauenswürdig |
| **C6** | DSGVO | Lokale Daten: Zugriff prüfen | Datenschutzverstoß |
| **C7** | Status-Prüfung | Nur `published` verwenden (außer explizit anders) | Veraltete Info |

---

## 8. Wissensartikel - Frontmatter

### Pflicht-Felder

```yaml
---
titel: [String]
gueltigkeit: [Bund|Land|Kreis|Gemeinde|Organisation]
quelle: [URL|Referenz]
veroeffentlicht: [YYYY-MM-DD]
tags: [Array von System-Tags + Projekt-Tags]
status: [draft|review|published|deprecated]
---
```

### Optional (empfohlen)

```yaml
autor: [Name]
version: [X.Y]
review-datum: [YYYY-MM-DD]
naechstes-review: [YYYY-MM-DD]
```

---

## 9. Navigation - Workflow-Logik

```
┌──────────────────────────────────────────────────────┐
│ User-Anfrage                                         │
└──────────────┬───────────────────────────────────────┘
               ↓
┌──────────────────────────────────────────────────────┐
│ Scanne ALLE vorgeladenen RAG-Index-Dateien           │
│ (inkl. LOCAL-DATA-Index falls konfiguriert)          │
└──────────────┬───────────────────────────────────────┘
               ↓
┌──────────────────────────────────────────────────────┐
│ Match: Keywords + Typische Fragen                    │
└──────────────┬───────────────────────────────────────┘
               ↓
┌──────────────────────────────────────────────────────┐
│ Identifiziere relevante Artikel                      │
│ (2-20 Stück)                                         │
└──────────────┬───────────────────────────────────────┘
               ↓
┌──────────────────────────────────────────────────────┐
│ Lade NUR identifizierte Artikel                      │
│ → Falls nicht im Kontext: Filesystem-Zugriff via MCP │ 
│ → Pfad aus RAG-Index entnehmen                       │
└──────────────┬───────────────────────────────────────┘
               ↓
┌──────────────────────────────────────────────────────┐
│ Verarbeite nach Quellen-Hierarchie                   │
│ (Regelungsrahmen > Lokale Daten > Wiki > LLM)        │
└──────────────┬───────────────────────────────────────┘
               ↓
┌──────────────────────────────────────────────────────┐
│ Ausgabe mit Quellen + Disclaimer                     │
└──────────────────────────────────────────────────────┘
```

---

## 10. Output - Format-Schema

**Template (IMMER verwenden):**

```markdown
**[DISCLAIMER]**
Die Antwort basiert auf einer RAGSource-Wissensdatenbank...

---

**[ANTWORT]**
[Persona-gerecht, kompakt]

---

**[QUELLEN aus RAGSource]**
1. [Dok-Titel § X]
2. [Dok-Titel Abschnitt Y]

---

**[WEITERE INFORMATIONSQUELLEN]**
ℹ️ LLM-Wissen: [was]
🌐 WebSearch: [was, Links]

---

**[NÄCHSTE SCHRITTE]**
[Optional]
```

---

## 11. Fehlerbehandlung - Entscheidungsbaum

### Nicht gefunden

```
WENN keine relevanten Artikel:
├─ Alle RAG-Indizes gescannt? → Ja
├─ Keywords erweitert? → Ja
└─ DANN: "Keine Quelle in RAGSource"
    └─ Angebot: WebSearch
```

### Widerspruch

```
WENN widersprüchliche Quellen:
├─ Rechtshierarchie prüfen
├─ Beide Quellen nennen
└─ User entscheiden lassen
```

### Veraltet

```
WENN status = deprecated:
├─ Warnung ausgeben
├─ Nach aktueller Version suchen
└─ Falls nicht: WebSearch anbieten
```

### Zugriff verweigert

```
WENN Lokale Daten benötigt: 
├─ Zugriff möglich? 
├─ NEIN → "Zugriff nicht verfügbar" 
│ "Diese Information befindet sich in geschützten Lokalen Daten" 
└─ JA → Lade LOCAL-DATA-Index 
        └─ Prüfe RAG-Indizes der Wissensmodule 
            └─ Vertraulich kennzeichnen in Ausgabe
```

---

## 12. Lokale Daten - Besonderheiten

**Eigenschaften:**
- Separater Speicherort (z.B. Sharepoint)
- Zugriffsprüfung erforderlich
- DSGVO-geschützt
- Vertraulich in Ausgabe kennzeichnen

**Struktur:** Wie RAGSource-Wissensmodule
- RAG-Index.md (Pflicht!)
- Wissensartikel.md

**Verwendung:**
- Prüfe Zugriff VOR Laden
- Falls Zugriff verweigert: Alternative anbieten
- In Ausgabe: "🔒 Vertraulich: [Info]"

---

## 13. Templates & Workflows

Projekt-spezifische Templates und Workflows können im Wiki bereitgestellt werden:
- `20_WIKI/[Modul]/Templates/`
- `20_WIKI/[Modul]/Workflows/`

**Wenn vorhanden:** Für passende Aufträge verwenden

## 14. Pfad-Auflösung - Best Practices

**Problem:** RAG-Index enthält nur Dateinamen, keine Pfade

**Lösung:**

Option A: Relative Pfade im RAG-Index
- `**Datei:** Unterordner/Artikel.md`

Option B: Metadaten-Header im RAG-Index
- Definiere `**Artikel-Verzeichnis:**` am Anfang
- Alle Artikel liegen dort

Option C: LLM exploriert
- Bei Fehler: Nutze list_directory auf Wissensmodul
- Suche Artikel rekursiv

---

**Für ausführliche Konzepte, Beispiele und Best Practices:**  
→ Siehe `RAGSource_sys_reference.md` (optional, on-demand laden)

---

**Version:** 1.0  
**Optimiert für:** Claude, Langdock, lokale LLMs  
