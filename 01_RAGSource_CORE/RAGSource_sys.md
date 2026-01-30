# RAGSource: System-Definitionen v2.0 (FORCE-optimiert)

**Version:** 2.0  
**Datum:** 2026-01-30  
**Zweck:** Erweiterte Definitionen, Regeln und Constraints für LLM-Navigation mit FORCE-Compliance  
**Kompatibel mit:** Master-Prompt v2.0

---

## 1. Architektur-Übersicht

### RAGSource Verzeichnisstruktur

```
RAGSource_[projekt]/                    # Basisverzeichnis
├── 01_RAGSource_CORE/                  # Generische Infrastruktur
│   ├── RAGSource_Masterprompt.md       # Prompt-Vorlage für LLM
│   ├── RAGSource_sys.md                # Diese Datei
│   └── RAGSource_sys_reference.md      # Detail-Doku (optional)
│
├── 02_RAGSource_PROJECT/               # Projekt-spezifisch
│   ├── Projektinitialisierung.md       # Use-Case Erweiterungen
│   └── RAGIndex.md                     # MASTER-INDEX (PFLICHT!)
│
├── 10_REGELUNGSRAHMEN/                 # Säule 1: Rechtsquellen
│   ├── [Wissensmodul_1]/
│   │   ├── RAGIndex_[Modul].md         # Modul-Index (optional)
│   │   ├── Artikel_1.md
│   │   └── Artikel_2.md
│   └── [Wissensmodul_2]/
│
├── 20_WIKI/                            # Säule 2: Praxiswissen
│   └── [Wissensmodul]/
│       ├── RAGIndex_[Modul].md
│       └── Artikel.md
│
└── 30_LOKALE_DATEN/                    # Säule 3: Vertraulich (extern)
    └── LOCAL-DATA-Index.md             # Verweis auf externes Repo
```

---

## 2. Kern-Definitionen

| Begriff | Definition | Kennzeichen |
|---------|------------|-------------|
| **RAGIndex (Master)** | Zentrale Navigationsdatei für ALLE Artikel | PFLICHT, immer zuerst laden |
| **Wissensmodul** | Thematische Gruppe von Artikeln | Optional: eigener RAGIndex |
| **Wissensartikel** | Einzeldokument mit Fachwissen | Frontmatter + Content + Querverweise |
| **Gültigkeit** | Räumlich-rechtlicher Geltungsbereich | Hierarchie: Gemeinde → Kreis → Land → Bund |
| **Säule** | Hauptkategorie | Regelungsrahmen / Wiki / Lokale Daten |
| **FORCE-Direktive** | Nicht überspringbare Anweisung | FORCE_LOAD, FORCE_SEQUENCE, etc. |

---

## 3. Säulen-Matrix

| Säule | Inhalt | Zugriff | Änderbar | Zitierbar | Beispiele |
|-------|--------|---------|----------|-----------|-----------|
| **Regelungsrahmen** | Gesetze, Verordnungen, Satzungen | Öffentlich | NIE | Ja, wörtlich | GemO BW, Hauptsatzung |
| **Wiki** | Praxis, Anleitungen, Interpretationen | Öffentlich | Durch Contributors | Mit Einschränkung | Checklisten, Prozesse |
| **Lokale Daten** | Intern, vertraulich | DSGVO-geschützt | Ja | Nein | Einsatzberichte, Personal |

### Zitierregeln nach Säule

**Regelungsrahmen:**
- ✅ MUSS wörtlich zitiert werden
- ✅ Format: `§ <Nummer> <Absatz> – <Titel> (<Quelle>, gültig ab <Datum>)`
- ❌ NIEMALS paraphrasieren

**Wiki:**
- ✅ Kann zusammengefasst werden
- ✅ Format: `[Titel] (RAGSource Wiki, Stand: <Datum>)`
- ⚠️ Als "Praxiswissen" kennzeichnen, nicht als Rechtsquelle

**Lokale Daten:**
- ❌ NICHT zitierbar (vertraulich)
- ✅ Nur für interne Kontextinformation

---

## 4. RAGIndex-Struktur (Master)

### Pflicht-Aufbau

```markdown
# RAGSource Index

**Version:** [Versionsnummer]
**Stand:** [Datum]
**Projekt:** [Projektname]

---

## Hierarchie-Übersicht

- **Gemeinde:** Bad Boll
- **GVV:** Raum Bad Boll
- **Kreis:** Göppingen
- **Land:** Baden-Württemberg
- **Bund:** Deutschland

---

## Artikel-Verzeichnis

### [Artikel-Titel]

**Datei:** `[Pfad]/[Dateiname].md`
**Ebene:** gemeinde | gvv | kreis | land | bund
**Säule:** regelungsrahmen | wiki | lokal
**Status:** published | draft | deprecated
**Gültigkeit:** [Scope, z.B. "Gemeinde Bad Boll"]
**Gültig ab:** [Datum]
**Gültig bis:** [Datum oder "heute"]

**Tags:**
- typ-[rechtsnorm|wissensartikel|template]
- thema-[bauen|wasser|feuerwehr|verwaltung|...]
- ebene-[gemeinde|gvv|kreis|land|bund]

**Keywords:** 
[Umfassend! Alle Synonyme, Abkürzungen, Fachbegriffe, umgangssprachliche Begriffe]

**Typische Fragen:**
[Minimum 8, umgangssprachlich formuliert, wie User wirklich fragt!]
- "Wie mache ich X?"
- "Wann muss ich Y zahlen?"
- "Wer ist zuständig für Z?"

**Querverweise:**
- [Verwandter Artikel A] → `[Pfad]/ArtikelA.md`
- [Verwandter Artikel B] → `[Pfad]/ArtikelB.md`

**Abhängigkeiten:**
- Basiert auf: [Übergeordnete Rechtsquelle, z.B. "GemO § 60"]
- Verweist auf: [Andere Artikel]

---
```

### Kritische Erfolgsfaktoren

✅ **Keywords:**
- So viele wie möglich für Qualität
- Alle Synonyme, Abkürzungen, Fachbegriffe
- Auch umgangssprachliche Begriffe

✅ **Fragen:**
- Minimum 8 pro Artikel
- Umgangssprachlich formuliert
- Wie User wirklich fragt (nicht Juristendeutsch!)

✅ **Hierarchie:**
- Immer Ebene angeben (gemeinde/gvv/kreis/land/bund)
- Abhängigkeiten dokumentieren

---

## 5. Wissensartikel-Struktur

### Frontmatter (YAML)

```yaml
---
title: "[Vollständiger Titel]"
quelle: "[URL oder Referenz]"
ebene: gemeinde | gvv | kreis | land | bund
säule: regelungsrahmen | wiki | lokal
status: published | draft | deprecated
gültig_ab: "YYYY-MM-DD"
gültig_bis: "YYYY-MM-DD" | "heute"
version: "X.Y"
tags:
  - typ-rechtsnorm
  - thema-bauen
  - ebene-gemeinde
---
```

### Content-Struktur

```markdown
# [Titel]

## Zusammenfassung
[Kurze Übersicht, 2-3 Sätze]

## Rechtsgrundlage
[Wörtliche Zitate mit § und Absatz]

## Erläuterung
[Verständliche Erklärung, Kontext]

## Verfahren
[Schritt-für-Schritt, falls relevant]

## Zuständigkeiten
[Wer ist wofür zuständig?]

## Fristen
[Relevante Fristen, falls vorhanden]

## Querverweise
- [Verwandter Artikel A](../Modul/ArtikelA.md)
- [Verwandter Artikel B](ArtikelB.md)

## Änderungshistorie
- YYYY-MM-DD: [Änderung]
- YYYY-MM-DD: Erstveröffentlichung
```

---

## 6. Metadaten-System (Tags)

### System-Tags (Pflicht)

**Typ (Dokumentart):**
- `typ-rechtsnorm`: Gesetze, Verordnungen, Satzungen
- `typ-wissensartikel`: Wiki-Artikel, Anleitungen
- `typ-template`: Vorlagen, Muster

**Status (Bearbeitungsstand):**
- `status-draft`: Entwurf, nicht veröffentlicht
- `status-review`: In Prüfung
- `status-published`: Veröffentlicht, gültig
- `status-deprecated`: Veraltet, nicht mehr gültig

**Ebene (Hierarchie):**
- `ebene-gemeinde`: Gemeinde-Ebene
- `ebene-gvv`: Gemeindeverwaltungsverband
- `ebene-kreis`: Landkreis
- `ebene-land`: Bundesland
- `ebene-bund`: Bundesebene

**Thema (Fachbereich):**
- `thema-bauen`: Bauwesen, Baugenehmigungen
- `thema-wasser`: Wasserversorgung, Abwasser
- `thema-feuerwehr`: Feuerwehr, Brandschutz
- `thema-verwaltung`: Allgemeine Verwaltung
- `thema-finanzen`: Haushalt, Gebühren
- `thema-personal`: Personalwesen
- [Weitere nach Bedarf]

### Projekt-spezifische Tags

Können frei definiert werden, z.B.:
- `projekt-digitalisierung`
- `priorität-hoch`
- `bereich-bürgerbüro`

---

## 7. Zitierregeln (FORCE-Compliance)

### Regelungsrahmen (Gesetze, Satzungen)

**PFLICHT: Wörtliches Zitat**

```markdown
§ 59 Abs. 1 GemO BW – Gemeindeordnung Baden-Württemberg 
(i.d.F. vom 24.07.2000, zuletzt geändert am 12.11.2024)

Wortlaut:
> "Die Gemeinden können zur Erfüllung ihrer Aufgaben 
> Gemeindeverwaltungsverbände bilden."
```

**Format:**
```
§ <Nummer> <Absatz> – <Titel> (<Quelle>, gültig ab <Datum>)

Wortlaut:
> "[Wörtliches Zitat]"
```

**VERBOTEN:**
- ❌ Paraphrasierung
- ❌ Zusammenfassung ohne Zitat
- ❌ "Sinngemäß" oder "Im Wesentlichen"

---

### Wiki-Artikel (Praxiswissen)

**ERLAUBT: Zusammenfassung**

```markdown
Laut RAGSource Wiki-Artikel "Baugenehmigungsverfahren" 
(Stand: 2024-07-15) umfasst das Verfahren folgende Schritte:

1. Antragstellung beim Bauamt
2. Prüfung der Unterlagen
3. [...]

Quelle: [Baugenehmigungsverfahren](../WIKI/Bauen/Baugenehmigung.md)
```

**Format:**
```
Laut RAGSource Wiki-Artikel "[Titel]" (Stand: <Datum>) [...]

Quelle: [Titel](Pfad/zur/Datei.md)
```

**HINWEIS:**
- ⚠️ Als "Praxiswissen" kennzeichnen
- ⚠️ NICHT als Rechtsgrundlage verwenden

---

### Externe Quellen (WebSearch)

**NUR nach User-Freigabe!**

```markdown
Laut [Quelle] ([URL]) gilt:

"[Wörtliches Zitat oder Zusammenfassung]"

⚠️ EXTERNE QUELLE: Diese Information stammt nicht aus RAGSource 
und wurde per WebSearch ermittelt.
```

**Format:**
```
Laut [Titel](URL) [...]

⚠️ EXTERNE QUELLE: [Hinweis]
```

---

### LLM-Wissen (Kontext only)

**ERLAUBT für Erklärungen:**

```markdown
Ein Gemeindeverwaltungsverband (GVV) ist ein Zusammenschluss 
mehrerer Gemeinden zur gemeinsamen Erfüllung von Verwaltungsaufgaben.

[Dann: Rechtsgrundlage aus RAGSource zitieren!]

Rechtsgrundlage:
§ 59 Abs. 1 GemO BW – [...]
```

**VERBOTEN als Rechtsquelle:**
- ❌ "Laut meinem Wissen gilt..."
- ❌ "Üblicherweise ist es so, dass..."
- ❌ Ohne Quellenangabe aus RAGSource

---

## 8. Hierarchie-Regeln

### Normenhierarchie (bei Widersprüchen)

```
Bundesrecht (BauGB, VwVfG, etc.)
    ↓
Landesrecht (GemO, LBO, etc.)
    ↓
Kreisrecht (Satzungen Landkreis)
    ↓
Verbandsrecht (GVV-Satzungen)
    ↓
Gemeinderecht (Gemeinde-Satzungen)
```

**Regel:** Höhere Ebene sticht bei Widerspruch

**Beispiel:**
```markdown
⚠️ HINWEIS: Widerspruch zwischen Regelungsebenen erkannt:

- Gemeinde-Satzung § 5: "Gebühr beträgt 50 EUR"
- Landes-Verordnung § 12: "Gebühr darf maximal 30 EUR betragen"

Gemäß Normenhierarchie gilt: Landes-Verordnung (max. 30 EUR)
```

---

### Spezialität vor Generalität

**Regel:** Speziellere Regelung sticht allgemeinere

**Beispiel:**
```markdown
Allgemein: GemO § 60 (Aufgaben des GVV)
Speziell: Verbandssatzung GVV Raum Bad Boll § 3 (konkrete Aufgaben)

→ Verbandssatzung ist spezieller und gilt vorrangig
```

---

## 9. FORCE-Direktiven (Compliance)

### FORCE_LOAD

**Bedeutung:** Datei MUSS vollständig geladen werden

**Verwendung:**
```yaml
FORCE_LOAD:
  url: "[URL]"
  mode: COMPLETE  # Niemals partial/chunked
  on_failure: ABORT
```

**Beispiel:**
```python
ragindex = FORCE_LOAD("https://raw.githubusercontent.com/.../RAGIndex.md")
if ragindex is None:
    ABORT("RAGIndex nicht erreichbar")
```

---

### FORCE_SEQUENCE

**Bedeutung:** Schritte MÜSSEN in dieser Reihenfolge ausgeführt werden

**Verwendung:**
```yaml
FORCE_SEQUENCE:
  STEP_1: Verstehe Anfrage
  STEP_2: Lade RAGIndex
  STEP_3: Identifiziere Artikel
  STEP_4: Lade Artikel vollständig
  STEP_5: Verarbeite nach Hierarchie
  STEP_6: Generiere Antwort
```

**Regel:** Kein Schritt darf übersprungen werden

---

### FORCE_COMPLIANCE_CHECK

**Bedeutung:** Checks MÜSSEN vor Ausgabe durchgeführt werden

**Verwendung:**
```yaml
COMPLIANCE_CHECK:
  BEFORE_OUTPUT:
    - ASSERT: ragindex_loaded == true
    - ASSERT: all_articles_loaded_completely == true
    - ASSERT: all_sources_cited_verbatim == true
    - ASSERT: no_llm_knowledge_as_legal_source == true
  
  ON_ASSERTION_FAILURE:
    ACTION: ABORT
```

---

### FORBIDDEN

**Bedeutung:** Diese Aktionen sind NIEMALS erlaubt

**Verwendung:**
```yaml
FORBIDDEN:
  - "RAGIndex-Inhalte als Rechtsquelle verwenden"
  - "Artikel nur teilweise laden"
  - "Rechtsquellen paraphrasieren"
  - "LLM-Wissen als Rechtsquelle nutzen"
  - "WebSearch ohne User-Freigabe"
```

---

## 10. Edge Cases & Sonderfälle

### Fall 1: Keine Artikel in RAGSource gefunden

**Vorgehen:**
1. User informieren: "Keine relevanten Artikel gefunden"
2. Optionen anbieten:
   - WebSearch durchführen?
   - Anfrage präzisieren?
   - Abbrechen?
3. Auf User-Entscheidung warten
4. NIEMALS automatisch WebSearch ohne Freigabe

**Beispiel:**
```markdown
❌ Keine relevanten Artikel in RAGSource gefunden für: 
"Kostenersatz Feuerwehreinsatz"

Geprüfte Ebenen: Gemeinde, GVV, Kreis, Land

Optionen:
1. WebSearch durchführen (externe Quellen)
2. Anfrage präzisieren
3. Abbrechen

Wie möchten Sie fortfahren?
```

---

### Fall 2: Artikel verweist auf nicht geladenen Artikel

**Vorgehen:**
1. Abhängigkeit erkennen
2. Verwiesenen Artikel nachladen
3. Rekursiv bis max. Tiefe 3
4. Bei Zirkelbezug: Warnung ausgeben

**Beispiel:**
```markdown
ℹ️ HINWEIS: Artikel "Hauptsatzung § 5" verweist auf 
"Gebührensatzung § 3". Lade Abhängigkeit nach...

✅ Abhängigkeit geladen: Gebührensatzung
```

---

### Fall 3: Widerspruch zwischen Artikeln gleicher Ebene

**Vorgehen:**
1. Widerspruch erkennen
2. User informieren
3. Beide Regelungen zitieren
4. Hinweis: "Klärung durch Fachperson erforderlich"

**Beispiel:**
```markdown
⚠️ WIDERSPRUCH ERKANNT (gleiche Ebene):

Artikel A (Hauptsatzung § 5): "Gebühr beträgt 50 EUR"
Artikel B (Gebührensatzung § 3): "Gebühr beträgt 30 EUR"

Beide Satzungen sind auf Gemeindeebene. Eine Klärung durch 
die zuständige Fachperson ist erforderlich.
```

---

### Fall 4: Artikel ist veraltet (deprecated)

**Vorgehen:**
1. Status erkennen (`status: deprecated`)
2. User warnen
3. Nach aktueller Version suchen
4. Falls vorhanden: Aktuelle Version verwenden

**Beispiel:**
```markdown
⚠️ WARNUNG: Der gefundene Artikel ist veraltet.

Veralteter Artikel: "Hauptsatzung v1.0" (gültig bis 2023-12-31)
Aktuelle Version: "Hauptsatzung v2.0" (gültig ab 2024-01-01)

Verwende aktuelle Version.
```

---

### Fall 5: Folgefrage bezieht sich auf vorherige Antwort

**Vorgehen:**
1. Kontext aus vorheriger Antwort behalten
2. FORCE_SEQUENCE trotzdem durchlaufen
3. Bereits geladene Artikel aus Cache verwenden
4. Neue Artikel bei Bedarf nachladen

**Beispiel:**
```markdown
User: "Wie hoch ist die Gebühr?"
→ Antwort mit Quelle A

User: "Und wann muss ich die zahlen?"
→ Kontext behalten, Quelle A aus Cache, 
   ggf. neue Quelle B für Fristen laden
```

---

## 11. Performance-Optimierung

### Caching-Strategie

```yaml
cache:
  ragindex:
    ttl: 3600  # 1 Stunde
    refresh: on_new_conversation
  
  articles:
    ttl: 86400  # 24 Stunden
    refresh: on_version_change
  
  websearch:
    ttl: 1800  # 30 Minuten
    refresh: on_explicit_request
```

---

### Paralleles Laden

```yaml
parallel_loading:
  enabled: true
  max_concurrent: 10
  timeout_per_request: 30  # Sekunden
```

**Vorteil:** 10 Artikel in 30 Sekunden statt 300 Sekunden

---

### Dependency Resolution

```yaml
dependency_resolution:
  mode: RECURSIVE
  max_depth: 3
  on_circular_reference: WARN_AND_STOP
```

---

## 12. Fehlerbehandlung

### Fehlertypen

| Fehler | Ursache | Aktion |
|--------|---------|--------|
| **RAGIndex nicht erreichbar** | GitHub down, URL falsch | ABORT, User informieren |
| **Artikel nicht ladbar** | 404, Timeout | ABORT, User informieren |
| **Compliance-Check failed** | Regel verletzt | ABORT, keine Ausgabe |
| **Zirkelbezug** | Artikel A → B → A | WARN, Tiefe begrenzen |
| **Widerspruch** | Zwei Regeln widersprechen sich | NOTIFY, beide zitieren |

---

### Retry-Logik

```yaml
retry:
  enabled: true
  max_retries: 3
  retry_delay: 2  # Sekunden
  exponential_backoff: true
```

---

## 13. Logging & Monitoring

### Was wird geloggt?

```yaml
logging:
  - timestamp
  - query (User-Anfrage)
  - identified_articles (welche Artikel wurden identifiziert?)
  - loaded_articles (welche wurden geladen?)
  - compliance_checks (welche Checks wurden durchgeführt?)
  - errors (welche Fehler sind aufgetreten?)
  - response_time (wie lange hat es gedauert?)
```

---

### Compliance-Logging

```yaml
compliance_log:
  - assertion_results (alle ASSERT-Checks)
  - forbidden_actions_detected (wurden verbotene Aktionen erkannt?)
  - websearch_approvals (wann wurde WebSearch freigegeben?)
```

---

## 14. Beispiel-Durchläufe

### Beispiel 1: Erfolgreicher Standard-Durchlauf

**User-Anfrage:**
"Wie wird ein Gemeindeverwaltungsverband gegründet?"

**FORCE_SEQUENCE:**

```
STEP 1: Verstehe Anfrage
  → Persona: Bürger
  → Query: GVV-Gründung
  → Jurisdiction: Land (GemO), Verband (Satzung)
  → Topic: Verwaltung

STEP 2: Lade RAGIndex
  → URL: https://raw.githubusercontent.com/.../RAGIndex.md
  → Status: ✅ Geladen (15 Artikel verfügbar)

STEP 3: Identifiziere Artikel
  → Matches: 2 Artikel
    - GemO_BW_§59-60.md (Land)
    - Verbandssatzung_GVV-BBO.md (Verband)

STEP 4: Lade Artikel vollständig
  → GemO_BW_§59-60.md: ✅ Geladen (3.2 KB)
  → Verbandssatzung_GVV-BBO.md: ✅ Geladen (5.1 KB)
  → Abhängigkeiten: Keine

STEP 5: Verarbeite nach Hierarchie
  → Reihenfolge: Land → Verband
  → Widersprüche: Keine
  → Zitate: Wörtlich vorbereitet

STEP 6: Generiere Antwort
  → Disclaimer: ✅ Enthalten
  → Antwort: ✅ Vollständig
  → Quellen: ✅ Alle zitiert
  → Compliance-Check: ✅ Bestanden

OUTPUT: [Vollständige Antwort mit Disclaimer, Rechtsgrundlagen, Quellen]
```

---

### Beispiel 2: Keine Artikel gefunden → WebSearch

**User-Anfrage:**
"Was ist die aktuelle Grundsteuer B in Bad Boll?"

**FORCE_SEQUENCE:**

```
STEP 1: Verstehe Anfrage
  → Persona: Bürger
  → Query: Grundsteuer B
  → Jurisdiction: Gemeinde
  → Topic: Finanzen

STEP 2: Lade RAGIndex
  → Status: ✅ Geladen

STEP 3: Identifiziere Artikel
  → Matches: 0 Artikel
  → Grund: Grundsteuer-Hebesätze nicht in RAGSource

  → NOTIFY_USER:
    "Keine relevanten Artikel gefunden. WebSearch durchführen?"
  
  → USER_APPROVAL: ✅ Ja

  → WebSearch:
    Query: "Grundsteuer B Bad Boll Hebesatz"
    Results: [externe Quellen]

STEP 4: Übersprungen (keine RAGSource-Artikel)

STEP 5: Verarbeite WebSearch-Ergebnisse
  → Zitate: [Titel](URL)
  → Hinweis: ⚠️ EXTERNE QUELLE

STEP 6: Generiere Antwort
  → Disclaimer: ✅ Enthalten
  → Externe-Quellen-Hinweis: ✅ Enthalten
  → Compliance-Check: ✅ Bestanden

OUTPUT: [Antwort mit externen Quellen, Hinweis auf fehlende RAGSource-Daten]
```

---

### Beispiel 3: Compliance-Fehler → ABORT

**User-Anfrage:**
"Wie hoch ist die Hundesteuer?"

**FORCE_SEQUENCE:**

```
STEP 1: Verstehe Anfrage
  → ✅ OK

STEP 2: Lade RAGIndex
  → ✅ OK

STEP 3: Identifiziere Artikel
  → Matches: 1 Artikel (Hundesteuersatzung)

STEP 4: Lade Artikel
  → ❌ FEHLER: Artikel nicht erreichbar (404)
  → ON_FAILURE: ABORT

COMPLIANCE_CHECK:
  → ASSERT: all_articles_loaded_completely == false
  → ❌ FAILED

OUTPUT:
  ❌ COMPLIANCE-FEHLER
  
  Die Antwort konnte nicht generiert werden, da ein Compliance-Check 
  fehlgeschlagen ist:
  
  Fehler: Artikel "Hundesteuersatzung.md" konnte nicht vollständig 
  geladen werden (404 Not Found).
  
  Bitte kontaktieren Sie den Administrator.
```

---

## 15. Checkliste für Artikel-Autoren

### Beim Erstellen eines neuen Artikels:

- [ ] Frontmatter vollständig ausgefüllt
- [ ] Titel eindeutig und beschreibend
- [ ] Ebene korrekt zugeordnet (gemeinde/gvv/kreis/land/bund)
- [ ] Säule korrekt (regelungsrahmen/wiki/lokal)
- [ ] Status gesetzt (draft/published/deprecated)
- [ ] Gültigkeitsdaten angegeben
- [ ] Tags vollständig (typ, thema, ebene)
- [ ] Content strukturiert (Zusammenfassung, Rechtsgrundlage, etc.)
- [ ] Querverweise gesetzt
- [ ] Änderungshistorie begonnen

### Beim Aktualisieren des RAGIndex:

- [ ] Artikel im RAGIndex eingetragen
- [ ] Datei-Pfad korrekt
- [ ] Keywords umfassend (min. 10)
- [ ] Fragen umgangssprachlich (min. 8)
- [ ] Querverweise aktualisiert
- [ ] Abhängigkeiten dokumentiert
- [ ] Hierarchie-Ebene korrekt

---

## 16. FAQ für LLM-Agenten

**Q: Muss ich wirklich ALLE Schritte der FORCE_SEQUENCE durchlaufen?**
A: Ja, IMMER. Keine Ausnahmen. Bei Fehler: ABORT.

**Q: Kann ich Artikel nur teilweise laden, wenn sie sehr lang sind?**
A: Nein, NIEMALS. Immer COMPLETE mode. Bei Timeout: ABORT.

**Q: Darf ich LLM-Wissen verwenden, wenn ich mir sicher bin?**
A: Nur für Kontext-Erklärungen, NIEMALS als Rechtsquelle.

**Q: Was, wenn der User explizit nach meinem Wissen fragt?**
A: Erkläre, dass du nur RAGSource-Quellen verwendest. Biete WebSearch an.

**Q: Kann ich WebSearch verwenden, wenn keine Artikel gefunden wurden?**
A: Nur nach expliziter User-Freigabe. Vorher: User fragen.

**Q: Was, wenn zwei Artikel sich widersprechen?**
A: Beide zitieren, Hierarchie beachten, User auf Widerspruch hinweisen.

**Q: Muss ich bei Folgefragen wieder von vorne anfangen?**
A: Ja, FORCE_SEQUENCE durchlaufen. Aber: Cache nutzen für bereits geladene Artikel.

**Q: Was, wenn ein Compliance-Check fehlschlägt?**
A: ABORT. Keine Ausgabe. Fehlermeldung an User.

---

## 17. Versionierung

**Version 2.0 (2026-01-30):**
- FORCE-Konzepte integriert
- Compliance-Assertions hinzugefügt
- Hierarchische RAGIndex-Struktur vorbereitet
- Erweiterte Zitierregeln
- Edge Cases dokumentiert
- Beispiel-Durchläufe hinzugefügt

**Version 1.0 (2025-XX-XX):**
- Initiale Version
- Basis-Definitionen
- RAGIndex-Struktur
- Säulen-Konzept

---

## 18. Kontakt & Support

**Projekt:** amtsschimmel.ai  
**Repository:** https://github.com/amtsschimmel-ai/ragsource  
**Dokumentation:** RAGSource_sys_reference.md (Detail-Doku)  
**Issues:** GitHub Issues

---

**Ende RAGSource_sys.md v2.0**
