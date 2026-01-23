 # TIA SCL Style Programming Guide

## Inhaltsverzeichnis

- [TIA SCL Style Programming Guide](#tia-scl-style-programming-guide)
  - [Inhaltsverzeichnis](#inhaltsverzeichnis)
  - [Allgemeines](#allgemeines)
  - [Einstellungen in TIA Portal](#einstellungen-in-tia-portal)
    - [ES003 Empfehlung: Nichtproportionale Schriftart für Editoren](#es003-empfehlung-nichtproportionale-schriftart-für-editoren)
    - [ES004 Regel: Smarte Einrückung mit zwei Leerzeichen](#es004-regel-smarte-einrückung-mit-zwei-leerzeichen)
    - [ES005 Regel: Symbolische Repräsentation von Operanden](#es005-regel-symbolische-repräsentation-von-operanden)
    - [ES006 Regel: IEC-konforme Programmierung](#es006-regel-iec-konforme-programmierung)
    - [ES008 Regel: Automatische Wertprüfung (ENO) aktiviert](#es008-regel-automatische-wertprüfung-eno-aktiviert)
    - [ES009 Regel: Automatische Prüfung von Arraygrenzen](#es009-regel-automatische-prüfung-von-arraygrenzen)
  - [Nonemklatur und Formatierung](#nonemklatur-und-formatierung)
    - [NF001 Regel: Eindeutig und einheitlich in Englisch bezeichnen](#nf001-regel-eindeutig-und-einheitlich-in-englisch-bezeichnen)
    - [NF003 Regel: Entwicklerinformationen dokumentieren](#nf003-regel-entwicklerinformationen-dokumentieren)
    - [NF004 Regel: Präfixe und Struktur für Bibliotheken einhalten](#nf004-regel-präfixe-und-struktur-für-bibliotheken-einhalten)
      - [Alle in einer Bibliothek vorhandenen Elemente tragen das Präfix](#alle-in-einer-bibliothek-vorhandenen-elemente-tragen-das-präfix)
      - [Gruppieren in der Bibliothek](#gruppieren-in-der-bibliothek)
    - [NF005 Regel: Objekte in UpperCamelCase bezeichnen](#nf005-regel-objekte-in-uppercamelcase-bezeichnen)
    - [NF006 Regel: Codeelemente in lowerCamelCase bezeichnen](#nf006-regel-codeelemente-in-lowercamelcase-bezeichnen)
    - [NF007 Regel: Präfixe verwenden](#nf007-regel-präfixe-verwenden)
      - [Kein Präfix für Formalparameter](#kein-präfix-für-formalparameter)
      - [Temporäre und statische Variablen mit Präfix “temp” bzw. “stat”/“ext”](#temporäre-und-statische-variablen-mit-präfix-temp-bzw-statext)
      - [Instanzdaten mit Präfix “inst” bzw. “Inst”](#instanzdaten-mit-präfix-inst-bzw-inst)
      - [PLC-Datentypen mit Präfix “type”](#plc-datentypen-mit-präfix-type)
      - [Named value-Datentypen mit Präfix “nvt”](#named-value-datentypen-mit-präfix-nvt)
    - [NF008 Regel: Bezeichner von Konstanten in UPPER\_CASE schreiben](#nf008-regel-bezeichner-von-konstanten-in-upper_case-schreiben)
    - [NF010 Empfehlung: Zeichenlänge für Bezeichner einschränken](#nf010-empfehlung-zeichenlänge-für-bezeichner-einschränken)
    - [NF011 Empfehlung: Nur eine Abkürzung pro Bezeichner nutzen](#nf011-empfehlung-nur-eine-abkürzung-pro-bezeichner-nutzen)
    - [NF014 Regel: SCL-Code sinnvoll formatieren](#nf014-regel-scl-code-sinnvoll-formatieren)
      - [Vorrangig Zeilenkommentar // verwenden](#vorrangig-zeilenkommentar--verwenden)
      - [Ausdrücke sind immer in Klammern](#ausdrücke-sind-immer-in-klammern)
      - [Bedingung und Anweisungsteil werden mit Zeilenumbruch getrennt](#bedingung-und-anweisungsteil-werden-mit-zeilenumbruch-getrennt)
      - [Bedingungen und Anweisungen richtig einrücken](#bedingungen-und-anweisungen-richtig-einrücken)
  - [Wiederverwendrbarkeit](#wiederverwendrbarkeit)
    - [RU001 Empfehlung: Unterstützung für verschiedene Zielsysteme aktivieren](#ru001-empfehlung-unterstützung-für-verschiedene-zielsysteme-aktivieren)
    - [RU005 Regel: Symbolische Konstanten verwenden](#ru005-regel-symbolische-konstanten-verwenden)
  - [Referenzieren von Objekten](#referenzieren-von-objekten)
    - [AL001 Regel: Multiinstanzen statt Einzelinstanzen nutzen](#al001-regel-multiinstanzen-statt-einzelinstanzen-nutzen)
    - [AL002 Empfehlung: Arraygrenze von 0 bis Konstante definieren](#al002-empfehlung-arraygrenze-von-0-bis-konstante-definieren)
    - [AL003 Empfehlung: Array Parameter deklarieren](#al003-empfehlung-array-parameter-deklarieren)
    - [AL004 Empfehlung: Benötigte String Länge festlegen](#al004-empfehlung-benötigte-string-länge-festlegen)
  - [Sicherheit](#sicherheit)
  - [Designrichtlinien / Architektur](#designrichtlinien--architektur)
    - [DA001 Regel: Projekt/Bibliothek gruppieren und strukturieren](#da001-regel-projektbibliothek-gruppieren-und-strukturieren)
    - [DA002 Empfehlung: Geeignete Programmiersprache verwenden](#da002-empfehlung-geeignete-programmiersprache-verwenden)
      - [Standardbausteine – strukturierter Text (SCL/ST)](#standardbausteine--strukturierter-text-sclst)
      - [Aufrufumgebungen – grafisch/blockorientiert (KOP/FUP)](#aufrufumgebungen--grafischblockorientiert-kopfup)
      - [Schrittketten – flussorientiert (GRAPH)](#schrittketten--flussorientiert-graph)
      - [Signalflussorientiert (CFC - Continuous Function Chart)](#signalflussorientiert-cfc---continuous-function-chart)
      - [Ursachen-Wirkungs-Matrix (CEM - Cause Effect Matrix)](#ursachen-wirkungs-matrix-cem---cause-effect-matrix)
    - [DA003 Regel: Bausteineigenschaften setzen/prüfen](#da003-regel-bausteineigenschaften-setzenprüfen)
    - [DA004 Regel: PLC-Datentypen verwenden](#da004-regel-plc-datentypen-verwenden)
    - [DA005 Regel: Daten nur über Formalparameter austauschen](#da005-regel-daten-nur-über-formalparameter-austauschen)
    - [DA006 Regel: Auf statische Variablen nur lokal zugreifen](#da006-regel-auf-statische-variablen-nur-lokal-zugreifen)
    - [DA008 Regel: Ausgangsparameter genau einmal schreiben](#da008-regel-ausgangsparameter-genau-einmal-schreiben)
    - [DA016 Empfehlung: CASE Anweisung statt ELSIF Zweige nutzen](#da016-empfehlung-case-anweisung-statt-elsif-zweige-nutzen)
    - [DA017 Regel: ELSE Zweig bei CASE Anweisungen erstellen](#da017-regel-else-zweig-bei-case-anweisungen-erstellen)
    - [DA018 Empfehlung: Jump und Label vermeiden](#da018-empfehlung-jump-und-label-vermeiden)
  - [Performanz](#performanz)
  - [Versionierung](#versionierung)
  - [Änderungslog](#änderungslog)

## Allgemeines

Dieses Dokument basiert auf das Dokument Programmierstyleguide für
SIMATIC S7-1200 / S7-1500 Siemens. (Stand V2.1.0, 04/2025)


## Einstellungen in TIA Portal
Dieses Kapitel beschreibt die Regeln und Empfehlungen für die Grundeinstellungen in der
Programmierumgebung TIA Portal.

### ES003 Empfehlung: Nichtproportionale Schriftart für Editoren
Für die Editoren empfiehlt es sich eine nichtproportionale Schriftart (Monospace Font) zu
nutzen. Dadurch werden alle Zeichen in derselben Breite dargestellt und der Code, Wörter
sowie Einrückungen sind gleichmäßig in ihrer Verteilung. Die empfohlene Einstellung ist
“Consolas” mit Schriftgröße 10pt.

**Begründung:** Im Gegensatz zu “Courier New” wird bei “Consolas” verstärkt Wert auf die
Unterscheidbarkeit ähnlicher Zeichen gelegt. Sie wurde vor allem für die Programmierung
entworfen

**Quellenverweis:** K3/S10

### ES004 Regel: Smarte Einrückung mit zwei Leerzeichen
Für die Einrückung der Anweisungen werden zwei Leerzeichen und die Option “Indent” mit der
Einstellung “Smart” verwendet. Tabulatorzeichen sind in den textuellen Editoren nicht
zugelassen, da ihre Breite in verschiedenen Editoren unterschiedlich interpretiert und dargestellt
wird.

**Begründung:** Damit wird ein einheitliches Aussehen in unterschiedlichen Editoren
sichergestellt.

**Quellenverweis:** K3/S12

### ES005 Regel: Symbolische Repräsentation von Operanden
Die Repräsentation der Operanden wird auf symbolisch festgelegt.

**Begründung:** Es wird vollsymbolisch programmiert.

**Quellenverweis:** K3/S12

### ES006 Regel: IEC-konforme Programmierung
Um die IEC-konforme Programmierung zu gewährleisten, wird die IEC-Prüfung für die
Bausteinerstellung standardmäßig aktiviert.

**Begründung:** Dadurch wird bei der Bausteinerstellung sichergestellt, dass der IEC-Check
aktiviert ist und anschließend bei der Programmierung eine typkonforme und typsichere
Verwendung von Variablen gewährleistet wird.
So werden beispielsweise implizite Typumwandlungen, bei denen die Gefahr eines
Datenverlusts besteht (USint 0..255 <–> Uint -128..127), oder Slice-Zugriffe auf numerische
Datentypen vom Compiler als Fehler markiert.

**Quellenverweis:** K3/S12

### ES008 Regel: Automatische Wertprüfung (ENO) aktiviert
Für die automatische Prüfung von Typgrenzen und Operationen ist der EN/ENO Mechanismus
zuständig. Dieser wird standardmäßig aktiviert.
Der EN/ENO Mechanismus kann später am Baustein selbst deaktiviert werden.

**Begründung:** Somit werden die Wertprüfungen automatisch vom System durchgeführt, siehe
dazu auch “SE003 Regel: ENO behandeln”.

**Quellenverweis:** K3/S13

### ES009 Regel: Automatische Prüfung von Arraygrenzen
Die automatische Prüfung der Arraygrenzen ist standardmäßig zu aktivieren.

**Begründung:** Prüfung zur Laufzeit, ob Array-Indizes innerhalb des deklarierten Bereichs für ein
Array liegen. Wenn ein Array-Index den zulässigen Bereich überschreitet, wird der
Freigabeausgang ENO des Bausteins auf FALSE gesetzt.

**Quellenverweis:** K3/S13

## Nonemklatur und Formatierung
Dieses Kapitel beschreibt die Regeln und Empfehlungen für die Namensgebung und
Schreibweise.

### NF001 Regel: Eindeutig und einheitlich in Englisch bezeichnen
Der Name in Bezeichnern (Bausteine, Variablen etc.) ist in Englischer Sprache (English –
United States) zu verfassen. Der Name gibt den Sinn und Zweck des Bezeichners im Kontext
des Quellcodes wieder und lässt damit einen Rückschluss auf dessen Funktionalität bzw.
Verwendung zu.
• Die gewählte Schreibweise der Bezeichner muss in allen Objekten beibehalten werden und
ist so kurz wie möglich zu gestalten.
• Gleiche funktionale Bedeutung erhält namensgleiche Bezeichner. Dies gilt auch bezüglich
Groß- und Kleinschreibung.
• Für Bezeichner, die aus mehreren Worten bestehen, ist die Reihenfolge der Worte wie die
des gesprochenen Worts zu wählen.
• Funktionen/Funktionsbausteine beginnen nach Möglichkeit mit einem Verb, z. B. Get, Set,
Put, Find, Search, Calc usw.
• Ist der Bezeichner ein Arraybezeichner, ist er im Plural zu verwenden. Unzählbare Nomen
bleiben im Singular (data, information, content, management).
• Boolesche Variablen sind häufig zustandsanzeigende Variablen. In einem solchen Falle
sind Namen mit “is”, “can” oder “has” am eingängigsten und verständlichsten.
• Namensräume dienen zur Strukturierung und Abgrenzung der Softwareelemente und
werden entsprechend zur Projekt-Ordnerstruktur benannt.

**Begründung:** Ein schneller Überblick über das Programm und die Ein-/Ausgänge wird
gewährleistet.

**Quellenverweis:** K5/S17

### NF003 Regel: Entwicklerinformationen dokumentieren
Jeder Baustein erhält einen Beschreibungskopf im Programmcode (SCL/ST) bzw. im
Bausteinkommentar (KOP, FUP). Darin müssen die wichtigsten Informationen zur
Bausteinentwicklung hinterlegt werden. Durch die Platzierung im Programmcode werden diese
entwicklerrelevanten Informationen bei Know-how geschützten Bausteinen verborgen.
Anwenderrelevante Informationen müssen hingegen in die Bausteineigenschaften eingetragen
bzw. übernommen werden. Diese Informationen sind auch bei Know-how geschützten
Bausteinen für den Anwender sichtbar.
Die nachfolgende Schablone für einen Beschreibungskopf enthält sowohl die Elemente aus den
Baustein Eigenschaften, als auch entwicklerspezifische Elemente, die nicht in die Eigenschaften
übernommen werden müssen.
Die Beschreibung enthält folgende Punkte:
• (Optional) (C)Copyright (Name der Firma) [Jahr der Erstellung] - [Jahr der letzten Revision]
• (Optional) Titel/Bausteinbezeichner
• (Optional) Beschreibung der Funktionalität
• (Optional) Name der Bibliothek
• (Optional) Abteilung/Autor/Kontakt
• Testsystem – Getestet auf PLC(s) mit Firmware Version (z. B. 1516-3 PN/DP V4.0)
• Engineering – TIA Portal mit Version bei Erstellung/Änderungen
• Einschränkungen bei der Benutzung (z. B. bestimmte OB Typen)
• Voraussetzungen (z. B. zusätzliche Hardware)
• (Optional) zusätzliche Informationen
• (Optional) Änderungslog mit Version, Datum, Autor und Änderungsbeschreibung (bei Safety
Bausteinen Safety Signatur)

**Vorlage:**
```
REGION Description header
 //======================================================================
 // (C)Copyright (company) [year creation] - [year revision]
 //----------------------------------------------------------------------
 // Title: (Title of this block)
 // Comment/Function: (that is implemented in the block)
 // Library/Family: (that the source is dedicated to)
 // Author: (department/person in charge/contact)
 // Tested on System: (test system with FW version)
 // Engineering: TIA Portal (SW version)
 // Restrictions: (OB types, etc.)
 // Requirements: (hardware, technological package, etc.)
 //----------------------------------------------------------------------
 // Change log table:
 // Version | Date | Expert in charge | Changes applied
 //-------------|------------|------------------|------------------------
 // 001.000.000 | yyyy-mm-dd | (name of expert) | First released version
 //======================================================================
END_REGION Description header
```

**Quellenverweis:** K5/S19

### NF004 Regel: Präfixe und Struktur für Bibliotheken einhalten
Der Bibliotheksbezeichner hat das Präfix L und die Gesamtlänge maximal acht Zeichen
Der Bezeichner einer Bibliothek erhält das Präfix L plus maximal sieben Zeichen für den Namen
(z. B. LGF, LCom). “L” steht für das Wort “Library”. Nach dem Bibliothekspräfix wird ein
Unterstrich (_) zur Trennung verwendet (z. B. LGF_).
Die maximale Länge des Bezeichners für einen Bibliotheksnamen (inklusive Präfix) wird auf
acht Zeichen begrenzt.

**Begründung:** Diese Beschränkung dient zur kompakten Namensvergabe.

#### Alle in einer Bibliothek vorhandenen Elemente tragen das Präfix
Alle in einer Bibliothek vorhandenen Typen und Kopiervorlagen erhalten den Bezeichner der
Bibliothek.
Ein Element, welches nur die Verwendung der Bibliothek zeigt, ist kein Bibliothekselement im
Sinne der standardisierenden Bibliothek, sondern ein Beispiel und trägt deshalb auch nicht
zwingend das Präfix.

**Begründung:** Dadurch werden Kollisionen bei Bezeichnern vermieden.

- Bibliothek: Hauptordner der Bibliothek LExample
- PLC-Datentyp: LExample_type<Name>
- Named value-Datentyp: LExample_nvt<Name>
- Funktion/Funktionsbaustein: LExample_<Name>
- Organisationsbaustein: LExample_<Name>
- Globaldatenbaustein: LExample_<Name>
- PLC-Variablentabelle: LExample_<Name>
- Globale Konstante: LEXAMPLE_<NAME>
- Globale Konstante: für Status/Fehler/… LEXAMPLE_STATUS_<NAME>
- Globale Konstante: für Fehler LEXAMPLE_ERROR_<NAME>
- LEXAMPLE_ERR_<NAME>
- Globale Konstante für Warnung: LEXAMPLE_WARNING_<NAME>
- LEXAMPLE_WARN_<NAME>
- PLC-Meldetextliste: LExample_<Name>

#### Gruppieren in der Bibliothek
Alle Kopiervorlagen und Typen werden in einem Unterordner in der Bibliothek abgelegt, welcher
den Bibliotheksbezeichner als Ordnerbezeichner trägt.

**Begründung:** Der Unterordner dient zum Zweck der Projektharmonisierung und zum
Gruppieren von mehreren unabhängigen Bibliotheken in einem Projekt.

**Quellenverweis:** K5/S19

### NF005 Regel: Objekte in UpperCamelCase bezeichnen
Bezeichner von TIA Portal Objekten z. B.
• Bausteine, Software Units, Technologieobjekte, Bibliotheken, Projekte, Namespaces
• PLC-Variablentabellen, PLC-Meldetextlisten
• Beobachtungs- und Forcetabellen
• Traces und Messungen
werden in UpperCamelCase (PascalCasing) geschrieben.
Folgende Regeln gelten für UpperCamelCase:
• Das erste Zeichen ist ein Buchstabe und wird großgeschrieben.
• Besteht ein Bezeichner aus mehreren Worten, wird der Anfangsbuchstabe der einzelnen
Worte großgeschrieben.
• Es werden keine Trennzeichen (z. B. Binde- oder Unterstriche) für die optische
Begriffstrennung verwendet. Zur Strukturierung und Spezialisierung von wiederkehrenden
Strukturen bei Objektbezeichnern ist die maßvolle Nutzung von Unterstrichen (maximal
drei) erlaubt.

**DO:**
- GetAxisData_PosAxis
- GetAxisData_SpeedAxis
- GetAxisData_SyncAxis

**DO NOT:**
- Get_Axis_Data_Pos_Axis

**Quellenverweis:** K5/S21

### NF006 Regel: Codeelemente in lowerCamelCase bezeichnen
Bezeichner von Codeelementen z. B.
• Variablen
• PLC-Datentypen
• Named value-Datentypen
• Strukturen (“STRUCT”)
• Parameter
werden in lowerCamelCase (camelCasing) geschrieben.
Folgende Regeln gelten für lowerCamelCase:
• Das erste Zeichen ist ein Buchstabe und wird kleingeschrieben.
• Besteht ein Bezeichner aus mehreren Worten, wird der Anfangsbuchstabe der folgenden
einzelnen Worte großgeschrieben.
• Es werden keine Trennzeichen (z. B. Binde- oder Unterstriche) für die optische
Begriffstrennung verwendet.

**DO:**
- turnLeft
- turnRight

**DO NOT:**
- turn_Left
- turn-Left

**Quellenverweis:** K5/21

### NF007 Regel: Präfixe verwenden

#### Kein Präfix für Formalparameter
Formalparameter von Bausteinen werden ohne Präfixe verwendet. Auch bei der Übergabe
eines PLC-Datentyps oder Named value-Datentyps wird kein Präfix vergeben.

**Hinweis:** Formalparameter in Bausteinen erhalten kein Präfix (z. B. in / out / inOut).

**Quellenverweis:** K5/22

#### Temporäre und statische Variablen mit Präfix “temp” bzw. “stat”/“ext”
Um temporäre und statische interne Variablen klar von Formalparametern im Code zu trennen,
werden die Präfixe temp und stat verwendet.
Um statische Schnittstellen-Parameter zu PLC externen Systemen (z. B. HMI, MES,...) im
statischen Bereich eines FBs zu deklarieren, werden diese mit dem Präfix ext gekennzeichnet.

**Begründung:** Dies erleichtert dem Entwickler eines Bausteins die Unterscheidung zwischen
Formalparametern und Lokaldaten. Dadurch können sofort die Zugriffsrechte für den Benutzer
definiert und erkannt werden.

**Hinweis:** Statische Variablen in Global-DBs erhalten nicht das Präfix stat oder ext

**Quellenverweis:** K5/22

#### Instanzdaten mit Präfix “inst” bzw. “Inst”
Sowohl Einzelinstanzen als auch Multiinstanzen und Parameterinstanzen erhalten ein Präfix.
Bei Einzelinstanzen wird ein Inst, bei Multi- und Parameterinstanzen ein inst vorangestellt.

**Begründung:** Es kann einfach erkannt werden, ob ein (unzulässiger) Zugriff auf Instanzdaten
erfolgt.

**Hinweis:** Datenbausteine, die von einem PLC-Datentyp abgeleitet sind, erhalten kein Präfix Inst.

**Quellenverweis:** K5/22

#### PLC-Datentypen mit Präfix “type”
Der Deklaration des PLC-Datentypen wird das Präfix type vorangestellt. Die Definition einer
Variablen von diesem PLC-Datentyp sowie die Elemente im PLC-Datentyp erhalten wiederum
kein Präfix.

**Begründung:** Dies erleichtert dem Entwickler eines Bausteins die Unterscheidung zwischen
PLC-Datentypen, Named value-Datentypen, Funktionsbausteinen und Basis- / SystemDatentypen.

**Hinweis:** Datenbausteine, die von einem PLC-Datentyp abgeleitet sind, erhalten kein Präfix Type oder
type.

**Quellenverweis:** K5/22

#### Named value-Datentypen mit Präfix “nvt”
Der Deklaration des Named value-Datentypen wird das Präfix nvt vorangestellt. Die Definition
einer Variablen von diesem Named value-Datentypen sowie die Elemente im Named valueDatentypen erhalten wiederum kein Präfix.

**Begründung:** Dies erleichtert dem Entwickler eines Bausteins die Unterscheidung zwischen
Named value-Datentypen, PLC-Datentypen, Funktionsbausteinen und Basis- / SystemDatentypen.

**Hinweis:** Variablen, die von einem Named value-Datentypen abgeleitet sind, erhalten kein Präfix nvt.

**Quellenverweis:** K5/22

### NF008 Regel: Bezeichner von Konstanten in UPPER_CASE schreiben
Die Namen von Konstanten werden in UPPER_CASING geschrieben - durchgehend in
Großschrift (GROSS_SCHREIBUNG / UPPER_SNAKE_CASING /
SCREAMING_SNAKE_CASE / ALL_CAPS). Zum Trennen und Erkennen einzelner Worte oder
Abkürzungen ist jeweils ein Unterstrich zwischen den einzelnen Worten oder Abkürzungen
einzusetzen.
Zu den Konstanten zählen folgende Elemente:
• Globale Konstanten
• Lokale Konstanten
• Elemente in Named value-Datentypen
Folgende Regeln gelten für Konstanten in UPPER_CASING:
• Das erste Zeichen ist ein Buchstabe und wird großgeschrieben.
• Alle folgenden Zeichen sind entweder Großbuchstaben oder Ziffern.
• Wenn ein Bezeichner aus mehreren Wörtern zusammengesetzt ist, werden die Wörter
durch einen Unterstrich getrennt.


**Hinweis:** TRUE und FALS sind ebenfalls Konstanten.

**Quellenverweis:** K5/S24

### NF010 Empfehlung: Zeichenlänge für Bezeichner einschränken
Die Gesamtlänge eines einzelnen Bezeichners inkl. Präfix, Suffix oder Bibliotheksbezeichnung
soll 24 Zeichen nicht überschreiten.

**Begründung:** Da Variablennamen aus Strukturen sich aus mehreren Bezeichnern
zusammensetzen, wird sich in solchen Fällen ohnehin eine entsprechend lange
Variablenbezeichnung an der Verwendungsstelle ergeben.

**Quellenverweis:** K5/S24

### NF011 Empfehlung: Nur eine Abkürzung pro Bezeichner nutzen
Mehrere Abkürzungen sollten nicht direkt hintereinander verwendet werden, um eine optimale
Lesbarkeit zu gewährleisten. Um Zeichen bei einem Variablennamen zu sparen und die
Lesbarkeit des Programms zu erhöhen, können die Abkürzungen aus Tabelle 5-6 verwendet
werden.
Die Tabelle stellt nur eine gängige Auswahl dar. Die Schreibweise der Abkürzungen muss den
Regeln für die jeweilige Verwendung entsprechend angepasst werden (Groß-/Kleinschreibung).

**Beispiele:**
- Min Minimum
- Max Maximum
- Lim Limit
- Act Actual, Current
- Next Next value
- Prev Previous value
- Avg Average
- Sum Total sum
- Diff Difference
- Cnt Count
- Len Length
- Pos Position
- Ris Rising edge
- Fal Falling edge
- Old Old value (z. B. für Flankenerkennung)
- Sim Simulated
- Dir Direction
- Err Error
- Warn Warning
- Cmd Command
- Addr Address
  
**Quellenverweis:** K5/S25

### NF014 Regel: SCL-Code sinnvoll formatieren
Es wird empfohlen die Autoformat-Funktion von TIA Portal zu verwenden. Der Vorteil daraus ist,
dass alle Benutzer mit einer einheitlichen Formatierung arbeiten und das Einrücken automatisch
vorgenommen wird.

**Quellenverweis:** K5/S26

#### Vorrangig Zeilenkommentar // verwenden
Es ist zwischen zwei Arten von Kommentaren zu unterscheiden:
• Ein Kommentarabschnitt (*…*) oder ein mehrsprachiger Kommentarabschnitt (/*…*/) ist in
einer oder mehreren Zeilen vor dem entsprechenden Code Abschnitt zu setzen und
beschreibt eine Funktion, oder einen Codeabschnitt.
• Ein Zeilenkommentar // beschreibt den Code einer einzelnen Zeile und ist, wenn möglich,
an das Ende der Codezeile zu setzen, ansonsten vor die betreffende Code Zeile.
Um das Auskommentieren von Codebereichen beim Debugging zu erleichtern, werden im PLCCode nur Zeilenkommentare mit // verwendet.
Ein Kommentar liefert dem Leser Information darüber, warum etwas an der betreffenden Stelle
getan wird. Er darf nicht den Code als redundanten Klartext wiedergeben. Der Code beschreibt
bereits was getan wird, daher ist es wichtig zu dokumentieren, warum es getan wird.

**Begründung:** Man vermeidet dadurch Syntaxprobleme durch Einfügen und möglicherweise
Verschachteln von Kommentarabschnitten mit (*...*) oder (/*...*/).

**Quellenverweis:** K5/S26


#### Ausdrücke sind immer in Klammern
Um die Reihenfolge der Interpretation eindeutig zu machen, werden Ausdrücke entsprechend
der gewünschten Interpretationsreihenfolge geklammert.

**Beispiel:**
```
#tempSetlag:= FALSE;
OR (#tempPositionAct > #MIN_POS);
OR (#tempPositionAct < #MAX_POS);
```

**Quellenverweis:** K5/S27

#### Bedingung und Anweisungsteil werden mit Zeilenumbruch getrennt
Es ist eine klare Trennung zwischen Bedingung und Anweisungsteil herzustellen. Das heißt
nach einer Bedingung (z. B. THEN) oder nach einem Alternativzweig (z. B. ELSE) muss immer ein
Zeilenumbruch erfolgen, bevor eine Anweisung programmiert wird. Dieses gilt ebenso für den
Umgang mit Bedingungen anderer Anweisungen (z.B. CASE, FOR, WHILE, REPEAT).

**Quellenverweis:** K5/S27

#### Bedingungen und Anweisungen richtig einrücken
Jede Anweisung im Rumpf einer Kontrollstruktur wird eingerückt. Boolesche Verknüpfungen
werden, wenn eine Zeile nicht für die gesamte Bedingung ausreicht, in einer neuen Zeile
fortgesetzt.
Bei mehrzeiligen Bedingungen in IF-Anweisungen werden diese um zwei Leerzeichen
eingerückt. THEN wird in eine eigene Zeile auf der gleichen Höhe wie IF platziert. Passen die
Bedingungen einer IF-Anweisung in eine Zeile, kann THEN an das Zeilenende geschrieben
werden. Falls tiefer geschachtelt wird, steht der Operand allein in einer Zeile. Eine
alleinstehende Klammer zeigt das Ende der geschachtelten Bedingung. Operanden stehen
immer am Anfang der Zeile.
Entsprechend gelten diese Regeln auch für den Umgang mit Bedingungen anderer
Anweisungen
(z. B. CASE, FOR, WHILE, REPEAT).

**Beispiele:**
```
IF #enable //
 AND #tempIsConnected
 AND (
 (#turnLeft XOR #turnRight)
 OR (#statIsMaintenance AND #statIsManualMode)
 ) // Comment
THEN
 ; // Statement
ELSE
 ; // Statement
END_IF;
```

```
IF TRUE
 AND #enable // Comment
 AND #tempIsConnected
 AND (FALSE
 OR (#turnLeft XOR #turnRight)
 OR (#statIsMaintenance AND #statIsManualMode)
 ) // Comment
THEN
 ; // Statement
ELSE
 ; // Statement
END_IF;
```

```
IF #enable THEN
 ; // Statement
 IF #tempIsReleased THEN
 ; // Statement
 END_IF;
ELSE
 ; // Statement
END_IF;
```

## Wiederverwendrbarkeit
Dieses Kapitel beschreibt die Regeln und Empfehlungen für die mehrfache Nutzung von
Programmelementen.

### RU001 Empfehlung: Unterstützung für verschiedene Zielsysteme aktivieren
Aktivieren Sie die Simulierbarkeit und die Nutzbarkeit für virtuelle CPUs über die
Projekteigenschaft.

**Begründung:** Damit wird eine vollständige und vollumfängliche Nutzbarkeit der Bausteine auch
beim Simulieren oder in virtuellen CPUs sichergestellt.

**Hinweis:** Mit dem Hinzufügen dieser Optionen für Know-how geschützte Programmbausteine wird
potentiell das Niveau des Schutzes reduziert, da der Know-how Schutz unter anderem von
dem ausführenden Zielsystem abhängig ist.
In der auf unterschiedlichsten PC-Systemen betreibbaren Laufzeitumgebungen kann der
Schutz prinzipbedingt nicht so hoch sein, wie in einer dedizierten Hardware-CPU.

**Quellenverweis:** K6/S28

### RU005 Regel: Symbolische Konstanten verwenden
Im Sinne gekapselter Bausteine sind lokale Konstanten oder Named value-Datentypen zu
verwenden. Werden globale Konstanten verwendet, sind sie nach Möglichkeit über die
Formalparameter zu übergeben. Globale Konstanten sind in eigenen PLC-Variablentabellen zu
definieren.

**Hinweis:**
Wird in einem Baustein eine globale Konstante direkt verwendet und der Wert der
Konstanten verändert, muss der Baustein neu übersetzt werden. Dies bedeutet, dass bei
Know-how geschützten Bausteinen das Passwort bekannt sein muss.
Keine “Magic Numbers”
Wird eine Variable im Code mit einem Wert ungleich 0 (Integer), 0.0 (Real/LReal), TRUE oder
FALSE belegt oder verglichen, sind dafür symbolische Konstanten zu verwenden.

**Begründung:** Dadurch wird eine Änderung des Werts deutlich vereinfacht, da dieser nicht an
mehreren Stellen im Code, sondern zentral in der Deklaration der Konstanten geändert wird.

**Quellenverweis:** K6/S31

## Referenzieren von Objekten
Dieses Kapitel beschreibt die Regeln und Empfehlungen für die Speicherverwaltung und den
Zugriff.

### AL001 Regel: Multiinstanzen statt Einzelinstanzen nutzen
Im Programm sind vorrangig Multiinstanzen an Stelle von Einzelinstanzen zu verwenden.

**Begründung:** Dadurch können in sich geschlossene Module in Form von Funktionsbausteinen
erstellt werden, z. B. ein FB mit integrierten Zeiten für eine Zeitüberwachung. Dadurch müssen
keine zusätzlichen Instanzen in überlagerten oder globalen Strukturen angelegt werden.

**Quellenverweis:** K7/S34

### AL002 Empfehlung: Arraygrenze von 0 bis Konstante definieren
Für Array-Grenzen gilt Folgendes:
1. Der Startindex ist 0 (Untergrenze)
2. Endet mit einer symbolischen Konstante (Obergrenze)
Beachten Sie die folgenden Regeln und Empfehlungen:
• Bei Arrays, die nur in einem Baustein verwendet werden, muss die Konstante als lokale
Konstante definiert werden.
Der Zugriff auf globale Konstanten ist nur für die Definition von Array-Grenzen zur
Skalierung verschiedener Mengengerüste zulässig.
Siehe „RU004-Regel: Nur lokale Variablen verwenden“
• Als Datentyp für die Konstante wird empfohlen DInt zu wählen, um den gleichen Datentyp
wie für die Variable des Schleifenindex / Arrayzugriff zu verwenden.
Siehe „PE008 Empfehlung: Steuer-/Indexvariablen als „DInt“ deklarieren“

**Beispiel:**
```
BUFFER_UPPER_LIMIT DINT 10
diagnostics Array[0..BUFFER_UPPER_LIMIT] of typeDiagnostics

```

**Begründung:** Ein Array beginnend mit Index 0 ist sinnvoll, da bestimmte Systembefehle und
mathematische Operationen null basiert arbeiten, z. B. die Modulo Funktion. Dadurch kann der
gewünschte Index direkt in die Systemfunktion gegeben werden und muss nicht umgerechnet
werden.
Ein weiterer Vorteil ist, dass auch WinCC (Comfort, Advanced, Professional und Unified) nur mit
null basierten Arrays arbeitet, z. B. für Skripte.
Wird dennoch mit nicht null basierten Arrays gearbeitet, sollte ein Array mit jeweils einer
symbolischen Konstante für die Unter- und Obergrenze deklariert werden

**Quellenverweis:** K7/S34

### AL003 Empfehlung: Array Parameter deklarieren
Muss ein Array unbekannter Größe über die Formalparameter übergeben werden können,
empfiehlt es sich diesen Parameter als Array mit unspezifizierter Größe zu deklarieren.
Die Größen und Grenzen werden innerhalb des Bausteins mit den Systemfunktionen
UPPER_BOUND und LOWER_BOUND ermittelt und verarbeitet.

**Beispiel:**
```
diagnostics Array[*] of typeDiagnostics
```

**Begründung:**
Dadurch können generische Programmstrukturen aufgebaut werden,
insbesondere auch mit Know-how geschützten Bausteinen, da die Arraygröße nicht explizit in der Bausteinschnittstelle festgelegt werden muss.

**Quellenverweis:** K7/S34

### AL004 Empfehlung: Benötigte String Länge festlegen
String und WString reservieren beim Anlegen standardmäßig immer die Länge von 254
Zeichen. Ein String kann bis zu 254 Zeichen enthalten, ein WString bis zu 16382 Zeichen.
Es empfiehlt sich daher…
1. alle Zeichenketten auf die erforderliche Länge zu begrenzen.
2. symbolische Konstanten zur Angabe der Länge zu verwenden.

**Begründung:** Das verhindert zum einen unnötiges Allokieren von Speicher und zum anderen
bringt es Performanz Vorteile bei der Übergabe von Zeichenfolgen über die Formalparameter.

**Beispiel:**
```
MAX_MESSAGE_LENGTH DINT 24
errorMessage String[#MAX_MESSAGE_LENGTH] 
```

**Quellenverweis:** K7/S35

## Sicherheit
Dieses Kapitel beschreibt die Regeln und Empfehlungen für das Gestalten eines möglichst
sicheren und robusten Programmablaufs.

(TBD)

## Designrichtlinien / Architektur
Dieses Kapitel beschreibt die Regeln und Empfehlungen für Programmdesign und
Programmarchitektur.

### DA001 Regel: Projekt/Bibliothek gruppieren und strukturieren
Strukturieren und gruppieren Sie Ihr Programm in logische Einheiten. Das System stellt dazu
die verschiedensten Mittel zur Verfügung.
• Zusammengehörige Bausteine in einem Ordner/einer Gruppe zusammenfassen
• Strukturieren von technologischen Anlagenteilen in Software Units
• Gliedern von Programmen in logische funktionale Einheiten – FC/FB
• Zusammenfassen von zusammengehörigen Daten in PLC-Datentypen
• Strukturieren von Programmcode durch Netzwerke bzw. Regionen

**Hinweis:**
“REGION” in SCL ist vergleichbar mit Netzwerken in KOP/FUP.
Der Name einer Region ist vergleichbar mit einem Netzwerktitel und ist daher wie ein
Titel/Kommentar zu schreiben.
Regionen bieten verschiedene Vorteile:
– Eine Übersicht aller Regionen im Editor am linken Rand
– Schnelle Navigation durch den Code mit Hilfe der Übersicht und Verlinkung
– Die Möglichkeit des Einblendens und Ausblendens von Codefragmenten
– Schnelles Ein- und Ausklappen mit Hilfe der Navigation durch die Synchronisierung von
Übersicht und Code

**Quellenverweis:** K9/S39

### DA002 Empfehlung: Geeignete Programmiersprache verwenden
Es ist eine für den Anwendungsfall geeignete Programmiersprache zu wählen.

#### Standardbausteine – strukturierter Text (SCL/ST)
Als Programmiersprache von Standardbausteinen ist SCL die bevorzugte Sprache. SCL bietet
die kompakteste Lesbarkeit unter den Programmiersprachen und unterstützt zudem den
Programmierer durch Automarkierung aller Verwendungsstellen bei Selektion eines
Codeelements.

#### Aufrufumgebungen – grafisch/blockorientiert (KOP/FUP)
Soll eine Verschaltung einzelner Bausteine vorgenommen werden, z. B. in einem OB als
Aufrufumgebung, kann die Programmiersprache KOP oder FUP gewählt werden. Auch wenn
ein Baustein größtenteils aus Binärverknüpfungen besteht, kann KOP oder FUP gewählt
werden. In diesen Fällen sind durch die Wahl der Programmiersprache KOP oder FUP eine
leichtere Diagnose und eine schnellere Übersicht durch Servicepersonal möglich.

#### Schrittketten – flussorientiert (GRAPH)
Bei Ablaufketten empfiehlt sich die Verwendung von GRAPH. So können sequenzielle Abläufe
übersichtlich und schnell programmiert und nachverfolgt werden. Zusätzlich werden hier bereits
Verriegelungen und Überwachungen vom System bereitgestellt.

#### Signalflussorientiert (CFC - Continuous Function Chart)
CFC (Continuous Function Chart) wird insbesondere für verfahrenstechnische oder strukturierte
Automatisierungslösungen eingesetzt. Sie verknüpfen z. B. selbst erstellte Bausteine oder von
CFC gelieferte Anweisungen mit den Operanden Ihres Zielsystems. Mit Hilfe eines CFC-Charts
bleibt auch ein komplexes Anwenderprogramm übersichtlich. Prozesswerte sowie Ein- und
Ausgangsparameter der Anweisungen und Bausteine können Sie zum Testen online
überwachen.

#### Ursachen-Wirkungs-Matrix (CEM - Cause Effect Matrix)
CEM (Cause-Effect-Matrix) ist eine Programmiersprache, mit der Sie übersichtlich und schnell
unmittelbare Ursache-Wirkungs-Beziehungen definieren können. Dabei beschreiben Sie
bestimmte Prozessereignisse und definieren mögliche Prozessreaktionen. Diese weisen Sie
einander in einer zweidimensionalen Matrix zu.

**Quellenverweis:** K9/S39

### DA003 Regel: Bausteineigenschaften setzen/prüfen
In den Bausteineigenschaften sind folgende Einstellungen zu aktivieren:
1. Autonummerierung: Bausteine (FC, FB, DB, TO) werden nur mit aktivierter automatischer
Nummernvergabe ausgeliefert. Beachten Sie, dass die Abarbeitung eines
Organisationsbausteins von seiner Nummer/Priorität abhängig ist.
2. IEC-Check: Um die IEC konforme Programmierung zu gewährleisten wird der IEC-Check
aktiviert. Die Kompatibilität von Operanden bei Vergleichsoperationen und arithmetischen
Operationen wird gemäß den IEC-Regeln geprüft. So wird die typkonforme und typsichere
Programmierung sichergestellt. Nicht kompatible Operanden müssen explizit konvertiert
werden.
So werden beispielsweise implizite Typumwandlungen, bei denen die Gefahr eines
Datenverlusts besteht (USint 0..255 <–> Uint -128..127), oder Slice-Zugriffe auf
numerische Datentypen vom Compiler als Fehler markiert.
3. Optimierter Zugriff: Für die vollsymbolische Programmierung und maximale Performance
ist der optimierte Bausteinzugriff zu aktivieren.
In den Bausteineigenschaften sind folgende Attribute zu prüfen:
• ENO: Siehe “SE003 Regel: ENO behandeln”.
• Multiinstanz Fähigkeit: Die Verwendung als Multiinstanz ist gewährleistet, wenn ein
Baustein intern auch Multiinstanzen anstatt globaler Einzelinstanzen verwendet.
Siehe “AL001 Regel: Multiinstanzen statt Einzelinstanzen nutzen”
• Bibliothekskonformität: Siehe “RU004 Regel: Nur lokale Variablen verwenden”.

**Quellenverweis:** K9/S40

### DA004 Regel: PLC-Datentypen verwenden
Zum Strukturieren sind im Anwenderprogramm PLC-Datentypen zu verwenden. Auch in den
Lokaldaten werden PLC-Datentypen eingesetzt, wenn sie als Ganzes ausgetauscht werden.
Strukturen (“STRUCT”) werden nur in den Lokaldaten eines Bausteines oder innerhalb eines
PLC-Datentyps definiert, um bei Bedarf Variablen innerhalb des Bausteins oder PLC-Datentyps
durch die Gruppierung übersichtlicher darzustellen.

**Begründung:**
Eine Änderung in einem PLC-Datentyp wird an allen Verwendungsstellen im
Anwenderprogramm automatisch aktualisiert und der Datenaustausch über Formalparameter
zwischen mehreren Bausteinen wird vereinfacht.

**Hinweis:**
Variablen von PLC-Datentypen können, durch Vorhalten einer leeren/ungenutzten Variablen
vom gleichen Typ, mit einer Zuweisung einfach initialisiert und mit entsprechenden
Startwerten vorbelegt werden. Bei einer Änderung am Datentyp ist dadurch keine weitere
Nacharbeit für die Initialisierung erforderlich.

**Quellenverweis:** K9/S41

### DA005 Regel: Daten nur über Formalparameter austauschen
Der Datenaustausch innerhalb der PLC bei FBs oder FCs erfolgt grundsätzlich über die
Bausteinschnittstelle (Eingangs-, Ausgangs- oder Durchgangsparameter).
Werden FBs oder FCs als Aufrufumgebung oder zur Strukturierung der Software eingesetzt und
benötigen keine Schnittstelle zur Wiederverwendung, kann auf Formalparameter verzichtet
werden. Der Datenaustausch erfolgt in diesem Fall ausschließlich über den direkten Zugriff auf
Globaldaten. Eine Vermischung beider Zugriffsarten in einem Baustein ist nicht zulässig.
Begründung: Im Sinne gekapselter Bausteine werden Daten über die Schnittstelle entkoppelt
und Abhängigkeiten aufgelöst. Dadurch wird die Datenkonsistenz bei mehrfachen Aufrufen (ggf.
an unterschiedlichen Programmstellen) sichergestellt.
Benötigt eine Aufrufumgebung/Strukturelement keine Schnittstelle zur Wiederverwendung,
können durch den Verzicht auf Formalparameter Aufwände reduziert werden.

**Hinweis:** Es ist zulässig, direkt auf Eingangsvariablen unterlagerter Instanzen zu schreiben und von
deren Ausgangsvariablen zu lesen. Dafür sind keine zusätzlichen Variablen notwendig und
unnötige Kopiervorgänge werden vermieden.

**Beispiel:**

```
instCall.execute := TRUE;
instCall();
IF instCall.done THEN
 ; // next step
ELSIF instCall.error THEN
 ; // do something....
END_IF;
```
**Quellenverweis:** K9/S42

### DA006 Regel: Auf statische Variablen nur lokal zugreifen
Die internen statischen Daten eines Funktionsbausteins sind nur innerhalb des Bausteins zu
verwenden in dem sie deklariert sind.
Werden statische Variablen als Schnittstelle zu PLC-externen Systemen benötigt, z. B. zu dem
Baustein zugehörigen HMI Faceplate, sind diese explizit zu kennzeichnen.
Siehe auch:
• “NF007 Regel: Präfixe verwenden”
• “SE004 Regel: Datenzugriff per HMI/OPC UA/Web API selektiv aktivieren”.

**Begründung:**
Bei direktem Zugriff auf interne statische Variablen einer Instanz ist die
Kompatibilität nicht gewährleistet, da keinerlei Einfluss auf zukünftige Updates besteht.
Außerdem ist nicht klar, welchen Einfluss das Modifizieren statischer Variablen von außen auf
die Abarbeitung innerhalb eines FBs hat.

**Quellenverweis:** K9/S42

### DA008 Regel: Ausgangsparameter genau einmal schreiben
1. Die Ausgangsparameter und Rückgabewerte werden pro Bearbeitungszyklus genau einmal
mit einem Wert beschrieben. Dies muss möglichst gemeinsam und am Ende passieren.
2. Es ist nicht erlaubt, den eigenen Ausgangsparameter oder Rückgabewert zu lesen.
Stattdessen muss eine temporäre oder statische Variable eingeführt werden.

**Begründung:** Dadurch wird sichergestellt, dass alle Ausgänge konsistent gehalten werden.

**Quellenverweis:** K9/S43

### DA016 Empfehlung: CASE Anweisung statt ELSIF Zweige nutzen
Wenn möglich, soll anstatt einer IF Anweisung mit mehreren ELSIF Zweigen eine CASE
Anweisung verwendet werden.

**Begründung:**
Damit wird das Programm übersichtlicher.

**Quellenverweis:** K9/S52

### DA017 Regel: ELSE Zweig bei CASE Anweisungen erstellen
Eine CASE Anweisung muss immer einen ELSE Zweig aufweisen.

**Begründung:**
Dies dient dazu Fehler, die zur Laufzeit auftreten, melden zu können.

**Beispiel:**
```
CASE #stateSelect OF
 #CMD_INIT: // Comment
 ; // Statement
 #CMD_READ: // Comment
 ; // Statement
ELSE
 // default statement
 ; // Generate error message
END_CASE
```

**Quellenverweis:** K9/S52

### DA018 Empfehlung: Jump und Label vermeiden
Auf Sprünge im Programm ist zu verzichten. Verwendet werden Sprünge nur im Ausnahmefall,
wenn der Programmablauf nicht durch andere Methoden zu realisieren ist.
Begründung: Sprünge führen mitunter zu einem unleserlichen Programm, da durch diese
Befehle im Code hin und her gesprungen wird.
DA019 Empfehlung: Verwenden von Named value-Datentypen
Verwendung von Named value-Datentypen wenn möglich, z. B. für:
1. CASE-Anweisungen, z. B. in Zustandsautomaten.
2. Konfigurationsparametern anstelle von Integer
Beispiel: direction := nvtDirection#FORWARD / direction := nvtDirection#BACKWARD
3. Status- und Diagnosedaten
Siehe auch "RU005-Regel: Symbolische Konstanten verwenden“
Begründung: Dies gewährleistet die Lesbarkeit und Rückverfolgbarkeit der Software.

**Hinweis:**
Named value-Datentypen sind nur innerhalb von Software Units verfügbar.

**Beispiel:**
```
CASE #statMainState OF
 nvtStates#NO_OPERATION:
 REGION NO_OPERATION
 ; // No operational state
 END_REGION NO_OPERATION

 nvtStates#ENABLING:
 REGION ENABLING
 ; // Enabling state
 #statMainState := nvtStates#PROCESSING;
 END_REGION ENABLING

 nvtStates#PROCESSING:
 REGION PROCESSING
 ; // Processing state
 #statMainState := nvtStates#DISABLING;
 END_REGION PROCESSING

 nvtStates#DISABLING:
 REGION DISABLING
 ; // Disabling state
 #statMainState := nvtStates#NO_OPERATION;
 END_REGION DISABLING

 ELSE // Statement section ELSE
 // Error, undefined state reached
 #status := nvtStates#ERR_UNDEF;
END_CASE;
```

**Quellenverweis:** K9/S52

## Performanz
Dieses Kapitel beschreibt die Regeln und Empfehlungen für ein performantes
Anwenderprogramm.

(tbd)

## Versionierung

**Aktuelle Version:** 1.0.0  
**Letzte Änderung:** 2026-01-22

## Änderungslog

| Version | Datum      | Autor        | Änderung |
|--------:|------------|--------------|----------|
| 1.0.0   | 2026-01-22 | Andreas Benz | Initiale Version (Basis: Siemens Styleguide V2.1.0, 04/2025) |
| 0.2.0   | 2026-01-15 | Andreas Benz | Kapitel „Nomenklatur“ erweitert, Links/TOC ergänzt |
| 0.1.0   | 2026-01-10 | Andreas Benz | Grundstruktur erstellt |


**Quelle**:https://support.industry.siemens.com/cs/ww/de/view/81318674