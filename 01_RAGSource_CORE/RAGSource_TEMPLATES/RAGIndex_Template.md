# RAGIndex: TEMPLATE - Verbindliche Vorlage für alle Wissensmodule

**STATUS:** Dies ist das **verbindliche Template** für ALLE RAG-Indizes im RAGSource-System.

**FÜR LLMs:** Diese Datei enthält die **verpflichtenden Strukturvorgaben** für das Erstellen und Optimieren von RAG-Indizes. Der untenstehende **Landkreis Göppingen (LKR-GP)** dient als **lebendes Beispiel** und zeigt die exakte Umsetzung aller Prinzipien.

---

## 📋 ANWEISUNGEN FÜR LLMs: So erstellst/optimierst Du RAG-Indizes

### 1️⃣ GRUNDPRINZIP: Token-Effizienz bei maximaler Findbarkeit

**Ziel:**

- Jeder Wissensartikel muss über relevante User-Anfragen **sicher gefunden** werden
- Der RAG-Index wird bei **jeder** User-Anfrage geladen → Token-Effizienz ist **kritisch**
- **80% Token-Reduktion** ist realistisch und **notwendig**

**Faustregel:**

```
Unkomprimierter Index: 30.000-40.000 Tokens
Optimierter Index:      6.000-8.000 Tokens
```

---

### 2️⃣ PFLICHT-STRUKTUR: Diese Elemente MÜSSEN vorhanden sein

```markdown
# RAGIndex: [Modulname]

**Gültigkeit:** [Räumlicher/rechtlicher Geltungsbereich]
**Stand:** [Datum]
**Version:** [X.Y]

---

## Navigationshinweise für KI-Agenten

[Kurze Anleitung zur Verwendung]

---

## [THEMATISCHE GLIEDERUNG]

### [Artikelnummer] [Artikeltitel]

**Datei:** `Dateiname.md`
**§§:** [falls zutreffend]

**Keywords:** [20-50 Begriffe, kommagetrennt]

**Fragen:**
- "[Frage 1]"
- "[Frage 2]"
[5-10 Fragen total]

**Tags:** [Tags kommagetrennt]

**→** [Querverweise]

---

[... weitere Artikel ...]
```

**WICHTIG:** KEIN separater Tag-Index am Ende! Keywords sind bereits vollständig integriert.

---

### 3️⃣ KEYWORD-OPTIMIERUNG: Qualität vor Quantität

**✅ WAS GEHÖRT IN KEYWORDS:**

1. **Kern-Suchbegriffe (Substantive)**
    - Hauptbegriffe: "Baugenehmigung", "Waffenbesitzkarte", "Müllabfuhr"
    - Fachbegriffe: "Erdwärmesonde", "Abgeschlossenheitsbescheinigung"
2. **Häufigste Synonyme (max. 2-3 pro Konzept)**
    - "Waffenbesitzkarte, WBK" ✅
    - NICHT: "Waffenbesitzkarte, WBK, Waffenbesitzkarten, Besitzkarte für Waffen..." ❌
3. **Abkürzungen**
    - "ÖPNV, AWB, SBBZ, VVS, BImSchG"
4. **Rechtliche/administrative Begriffe**
    - "Genehmigung, Erlaubnis, Gebühr, Antrag, Befreiung, Ausnahme"
5. **Thematische Begriffe**
    - "Arbeitsschutz, Naturschutz, Denkmalschutz, Tierschutz"

**❌ WAS NICHT IN KEYWORDS GEHÖRT:**

1. **Spezifische Beträge/Zahlen**
    - ❌ "3,50 Euro", "78 Euro/Stunde", "Gebühr 25 Euro"
    - ✅ "Gebühr, Stundensatz, Kosten"
2. **Hunderte Variationen**
    - ❌ "Waffenbesitzkarte, WBK, Waffenbesitzkarten, Besitzkarte Waffen, Karte Waffenbesitz, Erlaubnis Waffenbesitz, Waffenschein, kleiner Waffenschein, Waffenerlaubnis..."
    - ✅ "Waffenbesitzkarte, WBK, Waffenschein"
3. **Verben (außer substantiviert)**
    - ❌ "beglaubigen, beantragen, genehmigen"
    - ✅ "Beglaubigung, Antrag, Genehmigung"
4. **Vollständige Sätze**
    - ❌ "Was kostet eine Baugenehmigung in Baden-Württemberg"
    - ✅ "Baugenehmigung, Kosten, Baden-Württemberg"
5. **Inhaltliche Details (gehören in den Artikel!)**
    - ❌ Liste aller Gebührenpositionen im Keyword-Feld
    - ✅ "Gebührenverzeichnis, Verwaltungsgebühren"

**📊 RICHTWERTE FÜR KEYWORD-ANZAHL:**

|Artikel-Größe|Empfohlene Keywords|Beispiel|
|---|---|---|
|Klein (1-3 §§)|15-25|Bekanntmachungssatzung|
|Mittel (4-10 §§)|25-35|Hauptsatzung|
|Groß (10+ §§)|30-50|GemO-BW Teil|
|Gebührenverzeichnis|30-45|Gebührenverzeichnis Teil 1|

---

### 4️⃣ FRAGEN: Wie User WIRKLICH suchen

**Zweck:**

- Zeigen typische umgangssprachliche Anfragen
- Helfen dem LLM, natürliche Sprache mit Artikeln zu matchen
- **Qualität vor Quantität!**

**✅ GUTE FRAGEN:**

```markdown
- "Waffenbesitzkarte Kosten?"
- "Wie beantrage ich Baugenehmigung?"
- "Sperrmüll abholen lassen?"
- "Wann Müllgebühren bezahlen?"
- "Arbeitszeit Ausnahme Sonntag?"
```

**Eigenschaften guter Fragen:**

- Kurz (3-7 Wörter)
- Umgangssprachlich
- Verschiedene Fragetypen:
    - "Was kostet...?"
    - "Wie beantrage...?"
    - "Wann muss...?"
    - "Wer ist zuständig...?"
    - "Wo finde ich...?"

**❌ SCHLECHTE FRAGEN:**

```markdown
- "Was ist das?" (zu vage)
- "Welche Gebühren fallen gemäß § 12 Abs. 3 der Verordnung XY an?" (zu formal)
- "Gibt es sowas?" (nicht konkret)
```

**📊 RICHTWERTE:**

- **5-10 Fragen pro Artikel**
- Kleine Artikel: 5-7 Fragen
- Große Artikel: 8-10 Fragen

---

### 5️⃣ TAGS: Systematisch und konsistent

**System-Tags (IMMER verwenden):**

**Dokumenttyp:**

- `typ-rechtsnorm` (Gesetze, Verordnungen, Satzungen)
- `typ-wissensartikel` (Wiki-Artikel)
- `typ-richtlinie` (Richtlinien, Leitfäden)
- `typ-konzept` (Konzepte, Leitbilder)

**Quelle:**

- `quelle-gesetz` (Bundesgesetz, Landesgesetz)
- `quelle-satzung` (Kommunale Satzung)
- `quelle-verordnung` (Verordnung)
- `quelle-richtlinie` (Richtlinie)
- `quelle-wiki` (Wiki-Artikel)

**Gültigkeitsebene:**

- `ebene-bund` (Bundesebene)
- `ebene-land` (Landesebene)
- `ebene-kreis` (Kreisebene)
- `ebene-gemeinde` (Gemeindeebene)
- `ebene-org` (Organisationsebene)

**Status:**

- `status-published` (veröffentlicht, aktuell gültig)
- `status-draft` (Entwurf)
- `status-review` (in Prüfung)
- `status-deprecated` (veraltet, aufgehoben)

**Projekt-spezifische Tags:**

**Bereich:**

- `bereich-bauamt`, `bereich-ordnungsamt`, `bereich-sozialamt`, etc.

**Thema:**

- `thema-bauen`, `thema-umwelt`, `thema-feuerwehr`, `thema-abgaben`, etc.

**Zielgruppe:**

- `zg-buerger`, `zg-unternehmen`, `zg-bauherren`, `zg-gemeinderat`, etc.

**📋 BEISPIEL:**

```markdown
**Tags:** typ-rechtsnorm, quelle-satzung, ebene-kreis, bereich-verwaltungsgebuehren, thema-waffen, thema-gewerbe, zg-buerger, zg-unternehmen, status-published
```

---

### 6️⃣ QUERVERWEISE: Kurz und prägnant

**Format:**

```markdown
**→** Artikel1, Artikel2, Gesetz-Kürzel
```

**✅ GUTE QUERVERWEISE:**

```markdown
**→** Hauptsatzung, Geschäftsordnung, LKrO-BW
**→** Gebührenverordnung, WaffG, GastG, GewO
**→** Abfallwirtschaftssatzung Teil 2, Betriebssatzung AWB, KrWG
```

**❌ SCHLECHTE QUERVERWEISE:**

```markdown
**→** Die Hauptsatzung des Landkreises Göppingen vom 15.05.2024
**→** Siehe auch die Geschäftsordnung für weitere Details
**→** /10_REGELUNGSRAHMEN/Regelungsmodul-LKR-GP/LKR-GP_Hauptsatzung.md
```

**Prinzip:**

- Nur Titel/Kurzbezeichnungen
- Keine Pfade
- Keine Erklärungen
- Maximal 5-6 Querverweise pro Artikel

---

### 7️⃣ LLM-PERSPEKTIVE: So denkt ein LLM

**Wichtig zu verstehen:**

1. **LLMs verstehen Kontext**
    
    - User: "Ich will nen Brunnen bohren"
    - LLM erkennt: Brunnen → Grundwasser → Genehmigung → Wasserrecht
    - **Du brauchst NICHT:** "Brunnen, Brunnenbohren, Brunnenbau, Brunnenbohrung, Wasserbrunnen, Grundwasserbrunnen..."
    - **Du brauchst:** "Brunnen, Grundwasserentnahme, Genehmigung"
2. **Synonyme sind bereits im LLM**
    
    - LLM kennt: "Müll" = "Abfall" = "Restmüll" = "Hausmüll"
    - **Du brauchst NICHT alle Varianten**
    - **Du brauchst:** Die 2-3 häufigsten
3. **Jedes Keyword kostet Tokens**
    
    - Index wird bei JEDER Anfrage geladen
    - 1000 überflüssige Keywords = 1000 verschwendete Tokens PRO Anfrage
    - Bei 100 Anfragen/Tag = 100.000 verschwendete Tokens/Tag!
4. **Weniger ist mehr**
    
    - 30 präzise Keywords > 300 redundante Keywords
    - LLM matched besser bei fokussierten Keywords

---

### 8️⃣ OPTIMIERUNGS-WORKFLOW: Schritt für Schritt

**SCHRITT 1: Analyse**

```
□ Wieviele Artikel hat das Modul?
□ Wie viele Tokens hat der aktuelle Index?
□ Sind alle Keywords notwendig?
□ Gibt es Redundanzen?
```

**SCHRITT 2: Keywords komprimieren**

```
□ Pro Artikel: Streiche alle Variationen, behalte nur 2-3 Synonyme
□ Entferne alle spezifischen Beträge/Zahlen
□ Entferne alle Verben (außer substantiviert)
□ Reduziere auf 20-50 Keywords pro Artikel
```

**SCHRITT 3: Fragen optimieren**

```
□ Pro Artikel: 5-10 prägnante Fragen
□ Umgangssprachlich formuliert
□ Verschiedene Fragetypen abdecken
```

**SCHRITT 4: Tags prüfen**

```
□ Alle System-Tags vorhanden?
□ Tags konsistent mit Taxonomie?
□ Projekt-Tags sinnvoll?
```

**SCHRITT 5: Struktur validieren**

```
□ Alle Pflicht-Elemente vorhanden?
□ Thematische Gliederung logisch?
□ Querverweise korrekt?
□ Datei-Pfade vollständig?
```

**SCHRITT 6: Qualitätskontrolle**

```
□ Können typische User-Fragen beantwortet werden?
□ Sind alle Artikel findbar?
□ Token-Count reduziert (Ziel: -60% bis -80%)?
□ Keine Information verloren?
```

---

### 9️⃣ ANTI-PATTERNS: Das sollst Du VERMEIDEN

**❌ ANTI-PATTERN 1: Keyword-Flut**

```markdown
# SCHLECHT:
**Keywords:** Waffenbesitzkarte, WBK, Waffenbesitzkarten, Besitzkarte für Waffen, Karte zum Waffenbesitz, Erlaubnis zum Waffenbesitz, Waffenerlaubnis, Waffenerlaubniskarte, Erlaubniskarte Waffen, Schusswaffen Besitzkarte, kleine Waffenbesitzkarte, große Waffenbesitzkarte, grüne WBK, gelbe WBK, rote WBK, Waffenschein, kleiner Waffenschein, großer Waffenschein...

# GUT:
**Keywords:** Waffenbesitzkarte, WBK, Waffenschein, Munitionserwerbsschein
```

**❌ ANTI-PATTERN 2: Details in Keywords**

```markdown
# SCHLECHT:
**Keywords:** Gebühr 3,50 Euro, Zeitgebühr 78 Euro pro Stunde, Stundensatz mittlerer Dienst 51 Euro, Stundensatz gehobener Dienst 63 Euro, Stundensatz höherer Dienst 79 Euro...

# GUT:
**Keywords:** Gebühr, Zeitgebühr, Stundensatz, Dienstgruppe
```

**❌ ANTI-PATTERN 3: Zu viele/zu wenige Fragen**

```markdown
# SCHLECHT (zu viele):
25 Fragen für einen 3-Paragraph-Artikel

# SCHLECHT (zu wenig):
2 Fragen für einen 15-Paragraph-Artikel

# SCHLECHT (zu vage):
"Was ist das?", "Gibt es sowas?", "Wie geht das?"

# GUT:
5-10 konkrete, umgangssprachliche Fragen pro Artikel
```

**❌ ANTI-PATTERN 4: Tag-Index am Ende**

```markdown
# SCHLECHT:
[... Artikel ...]

## Tag-Index
**Waffen:** 2.2.3
**Gebühren:** 2.2.1, 2.2.2, 2.2.3
[... 50 weitere Zeilen ...]

# GUT:
Keine separaten Tag-Indizes! Keywords sind bereits in Artikeln integriert.
```

---

### 🔟 QUALITÄTSKRITERIEN: Das macht einen guten RAG-Index aus

**✅ CHECKLISTE FÜR EXZELLENTE RAG-INDIZES:**

**Struktur:**

- [ ] Folgt exakt dem Template-Format
- [ ] Thematische Gliederung ist logisch
- [ ] Alle Pflicht-Elemente vorhanden
- [ ] Navigationshinweise sind klar

**Keywords:**

- [ ] 20-50 Keywords pro Artikel (je nach Größe)
- [ ] Keine redundanten Variationen
- [ ] Keine Beträge/Zahlen
- [ ] Kommagetrennt

**Fragen:**

- [ ] 5-10 Fragen pro Artikel
- [ ] Umgangssprachlich formuliert
- [ ] Verschiedene Fragetypen
- [ ] Kurz und prägnant

**Tags:**

- [ ] Alle System-Tags vorhanden
- [ ] Konsistent mit Taxonomie
- [ ] Sinnvolle Projekt-Tags

**Performance:**

- [ ] Token-Reduktion 60-80% gegenüber unkomprimiert
- [ ] Alle Artikel bleiben findbar
- [ ] Keine Information verloren

**Wartbarkeit:**

- [ ] Datei-Pfade sind korrekt
- [ ] Querverweise sind aktuell
- [ ] Versionierung vorhanden

---

### 1️⃣1️⃣ BEISPIEL-TRANSFORMATION: Vorher/Nachher

**❌ VORHER (unkomprimiert):**

```markdown
### Waffenbesitzkarte Beantragen

**Keywords:** Waffenbesitzkarte, WBK, Waffenbesitzkarten, Besitzkarte für Waffen, Karte zum Waffenbesitz, Erlaubnis zum Waffenbesitz, Waffenerlaubnis, Waffenerlaubniskarte, grüne WBK, gelbe WBK, rote WBK, kleine Waffenbesitzkarte, große Waffenbesitzkarte, Sportschützen, Jäger, Waffensammler, Sachkundenachweis, Bedürfnisprüfung, Zuverlässigkeitsprüfung, polizeiliches Führungszeugnis, Waffenbesitzkarte Kosten 150 Euro, WBK Verlängerung Kosten 75 Euro, Bearbeitungszeit 3 Monate, Gültigkeitsdauer, Antrag, Antragsformular, zuständige Behörde Landratsamt, untere Waffenbehörde...

[Tokens: ~120]
```

**✅ NACHHER (optimiert):**

```markdown
### Waffenbesitzkarte Beantragen

**Keywords:** Waffenbesitzkarte, WBK, Waffenschein, Sportschütze, Jäger, Sammler, Sachkundenachweis, Bedürfnis, Zuverlässigkeit, Führungszeugnis, Antrag, Landratsamt, Waffenbehörde, Kosten, Gültigkeit, Verlängerung

**Fragen:**
- "Waffenbesitzkarte beantragen wie?"
- "WBK Kosten?"
- "Sportschütze Waffenbesitzkarte?"
- "Bedürfnisprüfung WBK?"
- "Wie lange gültig Waffenbesitzkarte?"

[Tokens: ~35]
```

**📊 Ergebnis:** 70% Token-Reduktion bei gleicher/besserer Findbarkeit!

---

## 📚 LEBENDES BEISPIEL: LKR-GP

Das folgende Regelungsmodul **Landkreis Göppingen (LKR-GP)** demonstriert die **exakte Umsetzung** aller oben genannten Prinzipien.

**Nutze es als 1:1-Vorlage für alle neuen RAG-Indizes!**

---

═══════════════════════════════════════════════════════════════

# RAGIndex: Regelungsmodul Landkreis Göppingen (LKR-GP)

**Gültigkeit:** Landkreis Göppingen (Kreisebene)  
**Stand:** 2026-01-28  
**Version:** 3.0

---

## Navigationshinweise für KI-Agenten

**Verwendung:**

- Keywords matchen gegen User-Anfrage
- Fragen wichtiger als Keywords
- Falls hilfreich: LLM Wissen nutzen (nur zur Identifikation der Quelle, nicht Inhalt)
- Bei Match: Artikel laden
- Originaltext beachten: NIE interpretieren
- Kreisrecht steht über Ortsrecht und unter Landes- und Bundesrecht

**Modul-Verzeichnis:** `10_REGELUNGSRAHMEN/Regelungsmodul-LKR-GP/`

---

## 1. KREISVERFASSUNG UND VERWALTUNG

### 1.1 Hauptsatzung des Landkreises Göppingen

**Datei:** `LKR-GP_Hauptsatzung.md`  
**§§:** 1-10

**Keywords:** Hauptsatzung, Kreisverfassung, Kreisordnung, Organe, Kreistag, Landrat, Zuständigkeiten, Ausschüsse, Verwaltungsausschuss, Sozialausschuss, Jugendhilfeausschuss, Umwelt Verkehr Ausschuss, Geschäftskreise, Delegation, Wertgrenzen, Beschlussrecht, Mitglieder, Wahl, Beteiligungsunternehmen, Sparkasse, Personal, Ehrungen, Satzungen

**Fragen:**

- "Hauptsatzung Landkreis Göppingen?"
- "Organe Landkreis?"
- "Kreistag Zuständigkeiten?"
- "Landrat Aufgaben?"
- "Ausschüsse Landkreis welche?"
- "Wertgrenzen Entscheidungen?"
- "Ab welchem Betrag Kreistag?"

**Tags:** typ-rechtsnorm, quelle-satzung, ebene-kreis, bereich-kreisverfassung, zg-kreistag, zg-landrat, status-published

**→** Geschäftsordnung Kreistag, Entschädigungssatzung, LKrO-BW

---

### 1.2 Geschäftsordnung des Kreistags

**Datei:** `LKR-GP_Geschaftsordnung_Kreistag.md`  
**§§:** 1-14

**Keywords:** Geschäftsordnung, Kreistag, Sitzung, Vorsitz, Fraktionen, Sitzordnung, Einberufung, Tagesordnung, Teilnahmepflicht, Aussprache, Abstimmung, Wahlen, Anfragen, Fragestunde, Bürgerbeteiligung, Protokoll, Hausrecht, nichtöffentlich

**Fragen:**

- "Ablauf Kreistagssitzung?"
- "Fraktion bilden wie viele?"
- "Einladungsfrist Kreistag?"
- "Bürgerfragen Kreistag?"
- "Namentliche Abstimmung?"
- "Protokoll einsehen?"

**Tags:** typ-rechtsnorm, quelle-satzung, ebene-kreis, bereich-kreisverfassung, zg-kreistag, status-published

**→** Hauptsatzung, Entschädigungssatzung

---

### 1.3 Archivordnung

**Datei:** `LKR-GP_Archivordnung.md`  
**§§:** 1-12

**Keywords:** Archiv, Kreisarchiv, Archivnutzung, Archivgut, Benutzung, berechtigtes Interesse, Sperrfristen, Öffnungszeiten, Reproduktionen, Gebühren, wissenschaftliche Forschung, Heimatgeschichte, Unterlagen Kreisverwaltung

**Fragen:**

- "Archiv Landkreis benutzen?"
- "Sperrfristen Archiv?"
- "Archivgut kopieren?"
- "Gebühren Archivnutzung?"
- "Heimatgeschichte Quellen?"

**Tags:** typ-rechtsnorm, quelle-satzung, ebene-kreis, bereich-verwaltung, thema-kultur, zg-buerger, status-published

**→** Verwaltungsgebührensatzung, Landesarchivgesetz-BW

---

### 1.4 Satzung über öffentliche Bekanntmachungen

**Datei:** `LKR-GP_Satzung_oeffentliche_Bekanntmachungen.md`  
**§§:** 1-2

**Keywords:** Bekanntmachungen, Veröffentlichung, NWZ, Göppinger Kreisnachrichten, Geislinger Zeitung, Amtsblatt, rechtswirksam, Satzungen, Verordnungen

**Fragen:**

- "Wo Satzungen veröffentlicht?"
- "Amtsblatt Landkreis?"
- "Wann Bekanntmachung rechtswirksam?"

**Tags:** typ-rechtsnorm, quelle-satzung, ebene-kreis, bereich-verwaltung, status-published

**→** Hauptsatzung, LKrO-BW

---

## 2. GEBÜHREN UND ENTGELTE

### 2.1 Satzung Jagdsteuer (AUFGEHOBEN)

**Datei:** `LKR-GP_Aufhebung_Satzung_Jagdsteuer.md`  
**Status:** AUFGEHOBEN 01.04.2009

**Keywords:** Jagdsteuer, aufgehoben, nicht mehr gültig

**Fragen:**

- "Jagdsteuer Landkreis?"
- "Jagdsteuer abgeschafft wann?"

**Tags:** typ-rechtsnorm, ebene-kreis, status-deprecated

---

### 2.2 Gebührenverordnung

**Datei:** `LKR-GP_Gebuehrenverordnung.md`  
**§§:** 1-5

**Keywords:** Gebührenverordnung, Verwaltungsgebühren, Landratsamt, untere Verwaltungsbehörde, Baurechtsbehörde, Zeitgebühr, Stundensatz, Ablehnung, Befreiung, Rechtsbehelf, Fotokopien, Beglaubigung, Aktenversand, Umsatzsteuer

**Fragen:**

- "Gebühren Landratsamt?"
- "Zeitgebühr wie viel?"
- "Beglaubigung Kosten?"
- "Fotokopie Preis?"
- "Widerspruch Gebühr?"

**Tags:** typ-rechtsnorm, quelle-verordnung, ebene-kreis, bereich-verwaltungsgebuehren, status-published

**→** Gebührenverzeichnis Anlage, Verwaltungsgebührensatzung, LGebG-BW

---

### 2.2.1 Änderungsverordnung Gebührenverordnung

**Datei:** `LKR-GP_1_Verordnung_zur_Aenderung_der_Gebuehrenverordnung_ax.md`

**Keywords:** Änderungsverordnung, Bauamt, Umweltschutzamt, Schornsteinfeger, Zweitbescheid, Abwasseranlagen, BImSchG, Arbeitsschutz, Betriebssicherheit, Arbeitszeitgesetz, Jugendarbeitsschutz, Feinstaubplakette

**Fragen:**

- "Gebühren geändert 2025?"
- "Schornsteinfeger Bestellung Gebühr?"
- "Abwasseranlage Kontrolle?"
- "Arbeitszeitausnahme Kosten?"

**Tags:** typ-rechtsnorm, quelle-verordnung, ebene-kreis, thema-gebuehren, status-published

**→** Gebührenverordnung

---

### 2.2.2 Änderungsverordnung Gebührenverordnung

**Datei:** `LKR-GP_2_Verordnung_zur_Aenderung_der_Gebuehrenverordnung_01-01-2026_ax.md`

**Keywords:** Änderungsverordnung, Mineralwasser, Thermalwasser, Thermalbad, Umweltschutzamt

**Fragen:**

- "Thermalwasser Gebühr?"
- "Thermalbad Anlieferung?"
- "Gebühren 2026 neu?"

**Tags:** typ-rechtsnorm, quelle-verordnung, ebene-kreis, thema-wasser, status-published

**→** Gebührenverordnung, Wassergesetz-BW

---

### 2.2.3 Gebührenverzeichnis - Teil 1 (Kommunalamt, Ordnungsamt, Veterinär, Gesundheitsamt)

**Datei:** `LKR-GP_Gebuehrenverzeichnis_Anlage_zur_Gebuehrenverordnung_Teil_1_von_3.md`  
**Produktnummern:** 11.31.05, 12.20.02-12.26.08, 41.40

**Keywords:** Gebührenverzeichnis, Waffenrecht, WBK, Waffenbesitzkarte, Waffenschein, Munitionserwerbsschein, Sprengstoff, Gaststättenerlaubnis, Gewerbeerlaubnis, Spielhalle, Bewachungsgewerbe, Heimaufsicht, WTPG, Namensänderung, Einbürgerung, Lebensmittelüberwachung, Fleischhygiene, Tierseuchen, Tierarzneimittel, Tierschutz, Kampfhund, Verhaltensprüfung, Amtsarzt, Gutachten, Kraftfahrzeugeignung, HIV-Test, Belehrung, Infektionsschutz, Hygienekontrolle, Trinkwasser, Badewasser, Zeitgebühr, Stundensatz

**Fragen:**

- "Waffenbesitzkarte Kosten?"
- "Gaststättenerlaubnis Gebühr?"
- "Gewerbeerlaubnis Preis?"
- "Spielhalle Erlaubnis?"
- "Bewachungsgewerbe Gebühr?"
- "Amtsärztliches Gutachten?"
- "HIV-Test Gesundheitsamt?"
- "Belehrung Infektionsschutz?"
- "Namensänderung Kosten?"
- "Lebensmittelkontrolle Gebühr?"
- "Kampfhund Verhaltensprüfung?"

**Tags:** typ-rechtsnorm, quelle-verordnung, ebene-kreis, bereich-verwaltungsgebuehren, thema-waffen, thema-gewerbe, thema-gastronomie, thema-gesundheit, thema-veterinaer, thema-lebensmittel, thema-tierschutz, zg-buerger, zg-unternehmen, zg-gastronomen, status-published

**→** Gebührenverordnung, Gebührenverzeichnis Teil 2, Gebührenverzeichnis Teil 3, WaffG, GastG, GewO, IfSG

---

### 2.2.4 Gebührenverzeichnis - Teil 2 (Umweltschutz, Naturschutz, Jagd, Fischerei)

**Datei:** `LKR-GP_Gebuehrenverzeichnis_Anlage_zur_Gebuehrenverordnung_Teil_2_von_3.md`  
**Produktnummern:** 55.20, 55.40.02.01.00, 12.20.03.02.00, 56.10

**Keywords:** Wasserrecht, Grundwasserentnahme, Brunnen, Erdwärmesonde, Geothermie, Abwasser, Einleitung, Gewässer, Wasserschutzgebiet, Naturschutz, Natura 2000, Landschaftsschutzgebiet, Biotop, Streuobstwiese, Eingriff, Ausgleich, Ökokonto, Auffüllung, Abgrabung, Bodenaushub, Steinbruch, Kiesgrube, Artenschutz, Werbeanlage, Jagdschein, Falkner, Fischereiprüfung, Altlasten, Sanierung, Bodenschutz, Deponie, Sammler, Beförderer, BImSchG, Immissionsschutz, Feinstaubplakette, UVP

**Fragen:**

- "Grundwasser entnehmen Erlaubnis?"
- "Brunnen bohren Genehmigung?"
- "Erdwärmesonde Kosten?"
- "Abwasser einleiten Gebühr?"
- "Wasserschutzgebiet Ausnahme?"
- "Streuobstwiese umwandeln?"
- "Eingriff Ausgleich?"
- "Ökokonto Anerkennung?"
- "Bodenaushub Genehmigung?"
- "Artenschutzprüfung?"
- "Jagdschein Kosten?"
- "Fischereiprüfung?"
- "Altlastensanierung?"
- "BImSchG Genehmigung?"

**Tags:** typ-rechtsnorm, quelle-verordnung, ebene-kreis, bereich-verwaltungsgebuehren, thema-wasser, thema-umwelt, thema-naturschutz, thema-artenschutz, thema-jagd, thema-fischerei, thema-bodenschutz, thema-immissionsschutz, zg-buerger, zg-unternehmen, zg-bauherren, status-published

**→** Gebührenverordnung, Gebührenverzeichnis Teil 1, Gebührenverzeichnis Teil 3, WHG, BNatSchG, BJagdG, BBodSchG, BImSchG

---

### 2.2.5 Gebührenverzeichnis - Teil 3 (Arbeitsschutz, Forst, Landwirtschaft, Bauamt, Denkmalschutz)

**Datei:** `LKR-GP_Gebuehrenverzeichnis_Anlage_zur_Gebuehrenverordnung_Teil_3_von_3.md`  
**Produktnummern:** 56.20, 55.50, 55.51, 52.10, 52.30

**Keywords:** Arbeitsschutz, Arbeitszeitgesetz, Ausnahmebewilligung, Sonn- und Feiertagsarbeit, Jugendarbeitsschutz, BetrSichV, Baugenehmigung, Bauantrag, vereinfachtes Verfahren, Bauvorbescheid, Kenntnisgabeverfahren, Befreiung, Ausnahme, BauGB, BauNVO, LBO, Geschossfläche, Baulinie, Firsthöhe, Traufhöhe, Dachform, Dachneigung, Bauüberwachung, Bauabnahme, Brandverhütungsschau, Abgeschlossenheitsbescheinigung, Wohnungseigentum, Schornsteinfeger, Kehrbezirk, Waldrodung, Kahlhieb, Wiederaufforstung, InVeKoS, FAKT, Pflanzenschutz, Sachkundenachweis, Denkmalschutz, Kulturdenkmal, Steuerbescheinigung

**Fragen:**

- "Baugenehmigung Kosten?"
- "Bauantrag Gebühr?"
- "Befreiung Baurecht?"
- "Ausnahme Bebauungsplan?"
- "Bauabnahme Gebühr?"
- "Brandverhütungsschau?"
- "Abgeschlossenheitsbescheinigung?"
- "Arbeitszeitausnahme beantragen?"
- "Sonntagsarbeit Genehmigung?"
- "Wald roden Genehmigung?"
- "Kahlhieb Erlaubnis?"
- "Pflanzenschutz Sachkundenachweis?"
- "Denkmalschutz Genehmigung?"

**Tags:** typ-rechtsnorm, quelle-verordnung, ebene-kreis, bereich-verwaltungsgebuehren, thema-bauen, thema-baurecht, thema-arbeitsschutz, thema-forst, thema-landwirtschaft, thema-denkmalschutz, zg-buerger, zg-bauherren, zg-arbeitgeber, zg-waldbesitzer, status-published

**→** Gebührenverordnung, Gebührenverzeichnis Teil 1, Gebührenverzeichnis Teil 2, LBO, ArbSchG, ArbZG, DSchG-BW

---

### 2.5 Verwaltungsgebührensatzung

**Datei:** `LKR-GP_Satzung_Verwaltungsgebuehrensatzung.md`  
**§§:** 1-18

**Keywords:** Verwaltungsgebührensatzung, Gebühren, öffentliche Leistungen, Gebührenschuldner, Eigenanteil, Beglaubigungen, Bescheinigungen, Rechtsbehelfe, Schulgebühren, Benutzungsgebühren, Obst-Gartenbau, Hochbauamt, Forstamt, Holzverkauf, Privatwald, Archiv, Stundensätze, Sondernutzung, Kreisstraßen

**Fragen:**

- "Verwaltungsgebühren Landkreis?"
- "Beglaubigung Kosten?"
- "Gebührenfreiheit wann?"
- "Forstamt Beratung?"
- "Holzverkauf Gebühr?"
- "Archiv Stundensatz?"

**Tags:** typ-rechtsnorm, quelle-satzung, ebene-kreis, bereich-verwaltungsgebuehren, status-published

**→** Archivordnung, Gebührenverzeichnis, Entgeltordnung

---

### 2.5.1 Gebührenverzeichnis zur Verwaltungsgebührensatzung

**Datei:** `LKR-GP_Gebuehrenverzeichnis_zur_Verwaltungsgebuehrensatzung.md`

**Keywords:** Verwaltungsgebühren, Ablehnung Antrag, Ausfertigungen, Abschriften, Ablichtungen, Fotokopien, Akteneinsicht, Befreiung Rechtsvorschriften, Beitreibung, Bescheinigungen, Beglaubigungen, Unterschriftsbeglaubigung, Zurücknahme Antrag, Rechtsbehelf, Widerspruch, Schulzeugnisse, Zeugnisbeglaubigung, Schülerausweis, Obst- und Gartenbau, LOGL, Sachkundenachweis, Gutachten, Stundensatz, VwV-Kostenfestlegung, Dienstgruppe

**Fragen:**

- "Antrag abgelehnt Gebühr?"
- "Akteneinsicht Kosten?"
- "Beglaubigung Unterschrift?"
- "Zeugnis beglaubigen?"
- "Schülerausweis verloren?"
- "Widerspruch Gebühr?"
- "LOGL Ausbildung Kosten?"
- "Gutachten Hochbauamt?"
- "Stundensatz gehobener Dienst?"

**Tags:** typ-rechtsnorm, quelle-satzung, ebene-kreis, bereich-verwaltungsgebuehren, thema-verwaltung, thema-beglaubigung, thema-schulen, thema-gartenbau, zg-buerger, zg-schueler, status-published

**→** Verwaltungsgebührensatzung, Entgeltordnung, Gebührenverordnung

---

### 2.6 Entgeltordnung - Benutzung kreiseigener Einrichtungen

**Datei:** `LKR-GP_Gebuehrenverzeichnis_Entgeltordnung.md`  
**Gültig ab:** 01.01.2021

**Keywords:** Entgeltordnung, Benutzungsentgelte, Kreishochbauamt, technische Beratung, HOAI, Schulgelder, Kreisarchivar, Gemeindearchivpfleger, Forstamt, Privatwald, Privatwaldbetreuung, Kommunalwald, Holzverkauf, Holzverkaufsstelle, Waldinspektionsvertrag, ständige Betreuung, fallweise Betreuung, Holzauszeichnung, Festmeter, GEHO, Stundensatz, Dienstgruppe

**Fragen:**

- "Hochbauamt Beratung Kosten?"
- "Kreisarchivar Stundensatz?"
- "Privatwald Betreuung?"
- "Forstamt Beratung?"
- "Holzauszeichnung Gebühr?"
- "Waldinspektionsvertrag?"
- "Holzverkauf Provision?"
- "Festmeter Holz verkaufen?"
- "Schulgelder kreiseigene Schule?"

**Tags:** typ-rechtsnorm, quelle-entgeltordnung, ebene-kreis, bereich-verwaltungsgebuehren, thema-entgelte, thema-hochbau, thema-archiv, thema-forst, thema-privatwald, thema-kommunalwald, thema-holzverkauf, thema-bildung, zg-buerger, zg-waldbesitzer, zg-gemeinden, status-published

**→** Verwaltungsgebührensatzung, Gebührenverordnung, Archivordnung, LWaldG

---

## 3. ENTSCHÄDIGUNGEN UND SOZIALES

### 3.1 Entschädigungssatzung ehrenamtliche Tätigkeit

**Datei:** `LKR-GP_Satzung_Entschaedigung_ehrenamtliche_Taetigkeit.md`  
**§§:** 1-5

**Keywords:** Entschädigung, Ehrenamt, Sitzungsgeld, Aufwandsentschädigung, Kreistagsmitglieder, Ausschussmitglieder, Fraktionsvorsitzende, Monatspauschale, Selbständige, Betreuungspflichten, Kreisbrandmeister, Reisekosten, Verdienstausfall

**Fragen:**

- "Entschädigung Kreistag?"
- "Sitzungsgeld Höhe?"
- "Fraktionsvorsitzender Entschädigung?"
- "Fahrtkosten erstattet?"
- "Selbständige höhere Entschädigung?"

**Tags:** typ-rechtsnorm, quelle-satzung, ebene-kreis, thema-entschaedigung, zg-ehrenamtliche, status-published

**→** Hauptsatzung, Geschäftsordnung, LRKG-BW

---

### 3.2 Satzung Jugendamt

**Datei:** `LKR-GP_Satzung_Jugendamt.md`  
**§§:** 1-7

**Keywords:** Jugendamt, Kreisjugendamt, Jugendhilfe, Jugendhilfeausschuss, JHA, Mitglieder, Kreisräte, Jugendverbände, Wohlfahrtspflege, beratende Mitglieder, Beschlussrecht, Jugendhilfeplanung, Anerkennung Träger, Förderung, Jugendschöffen

**Fragen:**

- "Jugendamt Aufgaben?"
- "Jugendhilfeausschuss Mitglieder?"
- "JHA Beschlussrecht?"
- "Förderung Jugendhilfe?"
- "Jugendschöffen Vorschlag?"

**Tags:** typ-rechtsnorm, quelle-satzung, ebene-kreis, bereich-soziales, thema-jugendhilfe, status-published

**→** Hauptsatzung, SGB-VIII, LJHG-BW

---

### 3.3 Rabattierung Zeitfahrausweise Ausbildungsverkehr

**Datei:** `LKR-GP_Satzung_Rabattierung_von_Zeitfahrausweisen_im_Ausbildungsverkehr.md`  
**§§:** 1-6

**Keywords:** Rabattierung, Zeitfahrausweise, Ausbildungsverkehr, Schülerverkehr, Auszubildende, ÖPNV, VVS, D-Ticket JugendBW, Ausbildungstarif, Ausgleichsmittel, Verkehrsunternehmen, Expressbuslinie

**Fragen:**

- "Schülerticket Rabatt?"
- "Azubi-Ticket vergünstigt?"
- "Ausbildungsverkehr Förderung?"
- "VVS Schülertarif?"

**Tags:** typ-rechtsnorm, quelle-satzung, ebene-kreis, bereich-soziales, thema-oepnv, zg-schueler, status-published

**→** Schülerbeförderung, VVS, ÖPNVG-BW

---

### 3.4 Schülerbeförderung Erstattung

**Datei:** `LKR-GP_Satzung_Erstattung_Schuelerbefoerderung.md`  
**§§:** 1-21

**Keywords:** Schülerbeförderung, Kostenerstattung, Schulweg, D-Ticket JugendBW, VVS-Ausbildungsticket, Eigenanteil, Mindestentfernung, Berufsschüler, SBBZ, Schulkindergarten, Begleitperson, Höchstbetrag, stundenplanmäßig, Wochenendheimfahrten, Antragsfrist, Verwendungsnachweis, private Kraftfahrzeuge

**Fragen:**

- "Schülerbeförderung erstattet?"
- "Eigenanteil wie viel?"
- "Mindestentfernung Schulbus?"
- "Berufsschüler Fahrtkosten?"
- "SBBZ Beförderung?"
- "Antrag Frist?"

**Tags:** typ-rechtsnorm, quelle-satzung, ebene-kreis, bereich-soziales, thema-schuelerbefoerderung, status-published

**→** Rabattierung Ausbildungsverkehr, VVS, LRKG-BW

---

## 4. ABFALLWIRTSCHAFT

### 4.1 Abfallwirtschaftssatzung Teil 1

**Datei:** `LKR-GP_Abfallwirtschaftssatzung_Teil_1_von_2.md`  
**§§:** 1-17

**Keywords:** Abfallwirtschaftssatzung, Abfallentsorgung, Müllabfuhr, AWB, Abfallvermeidung, Recycling, Überlassungspflicht, Anschlusspflicht, Benutzungspflicht, Hausmüll, Restmüll, Sperrmüll, Bioabfall, Grünabfall, Wertstoffe, Altpapier, Glas, Elektroschrott, Altholz, Bauschutt, Schadstoffe, Abfallbehälter, Mülltonne, Biotonne, Transponder, Holsystem, Bringsystem, Wertstoffzentrum, Grügutplatz, Abfuhrtermin, Bereitstellung, Entsorgungsschein, Express-Sperrmüll

**Fragen:**

- "Müllabfuhr wie oft?"
- "Biotonne Leerung?"
- "Sperrmüll abholen?"
- "Gartenabfall Abholung?"
- "Elektrogeräte entsorgen?"
- "Mülltonne Größe?"
- "Wertstoffzentrum Öffnungszeiten?"

**Tags:** typ-rechtsnorm, quelle-satzung, ebene-kreis, bereich-abfallwirtschaft, status-published

**→** Abfallwirtschaftssatzung Teil 2, Betriebssatzung AWB, KrWG

---

### 4.2 Abfallwirtschaftssatzung Teil 2

**Datei:** `LKR-GP_Abfallwirtschaftssatzung_Teil_2_von_2.md`  
**§§:** 18-29

**Keywords:** Abfallentsorgungsanlagen, Selbstanlieferer, Müllheizkraftwerk, Wertstoffhof, Benutzungsordnung, Härtefall, Befreiung, Benutzungsgebühren, Gebührenschuldner, Jahresgebühr, Leerungsgebühr, Mehrbedarfssack, AWB-Biobeutel, Selbstanlieferungsgebühr, Bodenaushub, Altholz, Altreifen, Entstehung, Fälligkeit, Vorauszahlung, Mindestleerung, Ordnungswidrigkeit, Geldbuße

**Fragen:**

- "Gebühren Müllabfuhr?"
- "Jahresgebühr Abfall?"
- "Express-Sperrmüll Kosten?"
- "Selbstanlieferung Gebühr?"
- "Bauschutt entsorgen Preis?"
- "Wann Müllgebühren bezahlen?"
- "Ordnungswidrigkeit Mülltrennung?"

**Tags:** typ-rechtsnorm, quelle-satzung, ebene-kreis, bereich-abfallwirtschaft, thema-gebuehren, status-published

**→** Abfallwirtschaftssatzung Teil 1, Betriebssatzung AWB

---

### 4.3 Betriebssatzung Abfallwirtschaftsbetrieb

**Datei:** `LKR-GP_Betriebssatzung_Abfallwirtschaftsbetrieb.md`  
**§§:** 1-13

**Keywords:** Betriebssatzung, Abfallwirtschaftsbetrieb, AWB, Eigenbetrieb, Organe, Kreistag, Betriebsausschuss, Landrat, Betriebsleitung, Erster Betriebsleiter, Zuständigkeiten, Wertgrenzen, Wirtschaftsplan, Finanzplan, Jahresabschluss, Wirtschaftsjahr, Geschäftsordnung

**Fragen:**

- "AWB Organisation?"
- "Betriebsleitung AWB?"
- "Betriebsausschuss Abfall?"
- "Wirtschaftsplan AWB?"
- "Wertgrenzen Entscheidungen?"

**Tags:** typ-rechtsnorm, quelle-satzung, ebene-kreis, bereich-abfallwirtschaft, status-published

**→** Hauptsatzung, Abfallwirtschaftssatzung, EigBG-BW

---

## 5. KULTUR

### 5.1 Kulturförderrichtlinien

**Datei:** `LKR-GP_Kulturfoerderrichtlinie.md`

**Keywords:** Kulturförderung, Kulturbudget, Fördermittel, Kulturprojekt, Kulturveranstaltung, Musik, Kunst, Kulturpflege, Bildung, gemeindeübergreifend, ehrenamtlich, Antragsfrist, Kostenplan, Verwendungsnachweis, Verwaltungsausschuss, Abmangelfinanzierung

**Fragen:**

- "Kulturförderung beantragen?"
- "Kulturprojekt Förderung?"
- "Antragsfrist wann?"
- "Maximale Förderung?"
- "Voraussetzungen Kulturförderung?"

**Tags:** typ-richtlinie, ebene-kreis, bereich-kultur, thema-foerderung, status-published

**→** Hauptsatzung, Haushaltsplan

---

**═══════════════════════════════════════════════════════════════**

**Version:** 3.0 (TEMPLATE-VERSION)  
**Token-Reduktion:** ca. 80% gegenüber unkomprimiert  
**Stand:** 2026-01-28

**ENDE TEMPLATE**