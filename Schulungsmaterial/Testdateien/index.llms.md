Ladereihenfolge : Player → Unit-XML → Booklet-XML → Testtaker-XML Löschen in umgekehrter Reihenfolge

Vorwissen · Grundlage

XML-Grundlagen

Drei der vier Testdateien sind XML. Was sind Elemente, Attribute und Schema-Definitionen — und welcher Editor eignet sich am besten?

Details ansehen →

Schritt 1 · .html

Player

Stellt Aufgaben im Browser dar. Das Testcenter selbst zeigt keine Items an — der Player übernimmt die Darstellung vollständig.

Details ansehen →

Schritt 2 · .xml

Unit-XML

Beschreibt eine einzelne Aufgabe oder Seite: Metadaten, eindeutige ID, Verweis auf den Player und die eigentliche Aufgabendefinition.

Details ansehen →

Schritt 3 · .xml

Booklet-XML

Legt die Reihenfolge der Units fest und konfiguriert Blöcke, Zeitlimits, Freigabeworte und Navigationsregeln.

Details ansehen →

Schritt 4 · .xml

Testtaker-XML

Definiert Logins, weist Booklets zu und steuert den Modus der Teilnahme. Logins sind nach dem Upload sofort aktiv.

Details ansehen →

Wichtige Grundregeln

📋 Alle XML-Dateien

Unit-, Booklet- und Testtaker-Dateien sind XML. Ein Editor mit Syntax-Hervorhebung (z. B. VS Code) hilft enorm, Fehler vor dem Upload zu finden.

🔗 IDs sind Verweise

Das Booklet referenziert Units über deren `Id`. Die Testtaker-XML referenziert Booklets über deren `Id`. IDs müssen stabil und eindeutig sein.

⚠️ Upload-Reihenfolge

Das Testcenter prüft Abhängigkeiten beim Upload. Fehlt eine abhängige Datei, schlägt der Upload fehl. Ladereihenfolge unbedingt einhalten.

XML-Grundlagen\
Bevor es losgeht

Vorwissen

Grundlage für Schritte 2–4

> **NOTE:**

Was ist XML?

XML ist ein Textformat zur strukturierten Übertragung von Informationen — lesbar für Menschen und Maschinen gleichermaßen.

XML-Dateien können mit jedem Texteditor geöffnet und bearbeitet werden.

Eine XML besteht aus **Elementen**, die mit spitzen Klammern eingeleitet und mit einem Schrägstrich abgeschlossen werden: `<Element>...</Element>`

Elemente können beliebig tief **verschachtelt** werden und weitere Kind-Elemente enthalten.

Elemente, Attribute & Werte

**Daten** stehen zwischen den spitzen Klammern: `<Titel>Mein Buch</Titel>`

**Attribute** stehen im öffnenden Tag und ergänzen ein Element um zusätzliche Eigenschaften: `<Buch kategorie="kochen">`

Elemente können leere Kurzform nutzen, wenn kein Inhalt nötig ist: `<Unit id="M1" />`

Groß- und Kleinschreibung ist in XML **bedeutsam** — `<Unit>` und `<unit>` sind verschiedene Elemente.

Aufbau einer XML — Beispiel

beispiel.xml

    <?xml version="1.0"?>       <!-- Pflicht-Header jeder XML-Datei -->

    <Buecher>                      <!-- Hauptelement (root) -->

      <Buch kategorie="kochen">    <!-- Kind-Element mit Attribut -->
        <Titel>Tolle Suppen kochen</Titel>   <!-- Daten zwischen Tags -->
        <Autor>Sven Mustermann</Autor>
        <Preis>20.00</Preis>
      </Buch>

      <Buch kategorie="backen">
        <Titel>Tolle Kuchen backen</Titel>
        <Autor>Sabine Mustermann</Autor>
        <Preis>20.00</Preis>
      </Buch>

    </Buecher>

Warum ist Struktur so wichtig?

Anwendungen lesen die Struktur

Eine Anwendung wie das Testcenter liest XML-Dateien nach einem festen Schema — sie erwartet Elemente an bestimmten Stellen mit bestimmten Namen.

Wird ein Element umbenannt oder an die falsche Stelle gesetzt, kann die Anwendung die Datei nicht mehr korrekt lesen — im schlimmsten Fall ohne Fehlermeldung.

Daher: **Struktur und Elementnamen niemals eigenmächtig ändern**. Nur Werte und Inhalte anpassen.

XML-Schema-Definition (XSD)

Das Testcenter legt für jede Dateiart eine **Schema-Definition (XSD)** fest — eine maschinenlesbare Vorlage aller erlaubten Elemente und Attribute.

Die XSD wird im Haupt-Element der XML verlinkt. Beim Upload prüft das Testcenter automatisch gegen diese Vorlage.

Fehlt der XSD-Link, erscheint die Warnung *„File has no link to XSD-Schema"*. Stimmt die Version nicht, erscheint *„Outdated or wrong version"*.

Empfohlene Editoren

Windows

**Visual Studio Code** — kostenlos, hervorragende XML-Unterstützung mit Erweiterungen, farbliche Syntaxhervorhebung.

**Notepad++** — leichtgewichtig, schnell, gute Wahl für einfache Bearbeitungen.

Linux / macOS

**Visual Studio Code** — plattformübergreifend verfügbar, gleiche Vorteile wie unter Windows.

**Atom** — ebenfalls kostenfrei mit XML-Erweiterungen verfügbar.

> **NOTE:**

← Übersicht

Weiter: Player →

Player\
Aufgaben sichtbar machen

.html

Upload: Schritt 1 von 4

> **NOTE:**

Was ist ein Player?

Eine `.html`-Datei, die der Verona-Spezifikation folgt.

Wird in den Arbeitsbereich hochgeladen — muss vor den Units vorhanden sein.

Manche Player benötigen zusätzliche **Basis-Pakete** (z. B. GeoGebra als `.itcr.zip`). Diese werden zuerst geladen.

Die Unit-XML referenziert den Player über seinen Namen im Attribut `player`.

Basis-Pakete

Einige Player laden zur Laufzeit zusätzlichen Code nach (z. B. GeoGebra für interaktive Grafiken).

Basis-Pakete sind `.itcr.zip`-Dateien und müssen **vor dem Player** hochgeladen sein.

GeoGebra wird aus lizenzrechtlichen Gründen nicht mit dem Testcenter ausgeliefert und muss separat heruntergeladen werden.

IQB-Player im Überblick

Aspect

Standard-Player für komplexe Testaufgaben (VERA, Bildungstrend). Zusammen mit dem IQB-Studio verwendbar — Export direkt ins Testcenter ladbar.

Abi

Player für einfache Scriptsprache mit dynamischen Unterformularen. Ideal für Befragungen von Erwachsenen; ermöglicht automatisierte Rotation von Frageitems.

Speed Test (multi)

Lesegeschwindigkeitstest mit mehreren Items pro Unit (Text und Bild). Editor im IQB-Studio vorhanden.

Speed Test (mono)

Lesegeschwindigkeitstest mit einem Item pro Unit (nur Text). Sehr einfache Dateistruktur, leicht manuell erstellbar.

Simple Player

Universeller Player für HTML-Seiten. Erlaubt die Nutzung gängiger HTML-Werkzeuge zur Aufgabenerstellung.

← Übersicht

Weiter: Unit-XML →

Unit-XML\
Eine Aufgabe, eine Datei

.xml

Upload: Schritt 2 von 4

Was ist eine Unit?

Eine Unit entspricht einer Seite im Testablauf — mit Items, als Begrüßungsseite oder Abschlussseite.

Units sind **unabhängig** gedacht — sie sollen unabhängig von einem konkreten Test entwickelt und wiederverwendet werden.

Die **zwingend erforderliche** `Id` wird im Booklet referenziert und muss stabil bleiben.

Jede Unit-XML muss auf einen im Arbeitsbereich vorhandenen **Player** verweisen.

Definition: inline oder extern?

**Inline (`Definition`):** Die Aufgabendefinition steht direkt in der XML. Einfach, aber bei komplexen Formaten (JSON) unhandlich.

**Extern (`DefinitionRef`):** Verweis auf eine separate Datei (z. B. `.voud`). Empfohlen für JSON-basierte Aufgaben, da kein XML-Escaping nötig ist.

Externe Ressourcendateien müssen ebenfalls in den Arbeitsbereich hochgeladen werden.

Beispiel: Unit-XML mit externer Definition

unit1.xml

    <?xml version="1.0"?>
    <Unit xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xsi:noNamespaceSchemaLocation="https://raw.githubusercontent.com/.../vo_Unit.xsd">
      <Metadata>
        <Id>M1_JK05</Id>                    <!-- zwingend erforderlich -->
        <Label>Schriftliche Verfahren Plus 1</Label>
      </Metadata>
      <DefinitionRef player="iqb-player-aspect@2.0">  <!-- Player referenzieren -->
        M1_JK05.voud                               <!-- externe Definitionsdatei -->
      </DefinitionRef>
    </Unit>

> **NOTE:**

← Player

Weiter: Booklet-XML →

Booklet-XML\
Ablauf & Regeln definieren

.xml

Upload: Schritt 3 von 4

Was macht ein Booklet?

Definiert die **Reihenfolge der Units** für einen Test via Unit-IDs.

Steuert Darstellung und Verhalten über `<BookletConfig>` (z. B. Navigationsmodus, Seitenlayout).

Units können in **Blöcke (Testlets)** gruppiert werden — mit optionalen Restriktionen.

Texte im Test können über `CustomTexts` bookletspezifisch angepasst werden (z. B. Ansprache "Du"/"Sie").

Testlets: Blöcke mit Regeln

Blöcke erhöhen die Übersichtlichkeit und ermöglichen Restriktionen pro Abschnitt.

Der **Gruppenmonitor** benötigt Blöcke, um Testpersonen gezielt steuern zu können.

Blöcke können verschachtelt sein — Vorsicht, da sich Restriktionen gegenseitig behindern können.

Tipp: Stets alleinstehende Units vor und nach einem Block einplanen, um Blockierungen zu vermeiden.

Restriktionen im Testlet

CodeToEnter

Zeigt vor dem Betreten des Blocks eine Dialogbox. Erst nach Eingabe des korrekten Codes (Groß-/Kleinschreibung egal) wird der Block betreten. Dient der Synchronisation innerhalb einer Testgruppe.

TimeMax

Zeitlimit für den Block in Minuten. Nach Ablauf wird automatisch zur nächsten Unit außerhalb des Blocks navigiert und der Block wird gesperrt. Attribut `leave` steuert, ob freiwilliges Verlassen erlaubt ist (`allowed` / `forbidden`).

DenyNavigationOnIncomplete

Verhindert das Verlassen einer Unit bei unvollständiger Präsentation oder unvollständigen Antworten. Werte: `OFF` (keine Beschränkung), `ON` (nur Vorwärts), `ALWAYS` (Vor- und Rückwärts).

LockAfterLeaving

Sperrt eine Unit oder das gesamte Testlet nach dem Verlassen. Attribut `scope`: `unit` oder `testlet`. Attribut `confirm`: Warnung vor Sperrung anzeigen (true/false).

> **NOTE:**

Beispiel: Booklet mit Block

booklet1.xml

    <Booklet>
      <Metadata>
        <Id>booklet1</Id>
        <Label>Testheft 1</Label>
      </Metadata>
      <BookletConfig>
        <Config key="pagingMode">buttons</Config>
      </BookletConfig>
      <Units>
        <Unit id="Welcome" label="Willkommen" labelshort="-"/>
        <Testlet id="Block1" label="Aufgaben">
          <Restrictions>
            <CodeToEnter code="BUS">Bitte warte auf das Freigabewort.</CodeToEnter>
            <TimeMax minutes="10" leave="forbidden"/>
          </Restrictions>
          <Unit id="M1_JK05" label="Aufgabe 1" labelshort="1"/>
          <Unit id="M2_AK18" label="Aufgabe 2" labelshort="2"/>
        </Testlet>
        <Unit id="Goodbye" label="Danke" labelshort="-"/>
      </Units>
    </Booklet>

← Unit-XML

Weiter: Testtaker-XML →

Testtaker-XML\
Wer darf, wie, was testen?

.xml

Upload: Schritt 4 von 4

> **NOTE:**

Grundprinzip: Gruppen & Logins

Logins werden in **Gruppen** (`<Group>`) organisiert. Mindestens eine Gruppe muss vorhanden sein.

Die Gruppen-ID muss im gesamten Testcenter eindeutig sein — auch über verschiedene Arbeitsbereiche hinweg.

Benutzernamen müssen installationsweit eindeutig sein. Zu kurze Namen vermeiden!

Mehrere Testtaker-XMLs können hochgeladen werden — die Logins werden in einer gemeinsamen Liste geführt.

Login-Varianten

**Klassisch:** Name + Kennwort — Standardfall. Das Kennwort wird als Punkte dargestellt.

**Nur Name (URL):** Anmeldung direkt über URL oder QR-Code. Ideal für vereinfachte Szenarien oder Integration in Lernmanagementsysteme.

**Zweistufig (Personencode):** Gleiche Zugangsdaten für alle Computer einer Gruppe, individuelle Identifikation durch kurzen Personencode.

**Zeitbeschränkung:** Attribute `validFrom`, `validTo`, `validFor` steuern die zeitliche Gültigkeit einer Anmeldegruppe.

Login-Modi im Vergleich

Quelle: [iqb.pages.cms.hu-berlin.de/testcenter/pages/test-mode.html](https://iqb.pages.cms.hu-berlin.de/testcenter/pages/test-mode.html)

| Modus | Neuer Teilnehmer je Login | Reviews (Kommentare) | Antworten & Logs gespeichert | Zeitbeschränkungen aktiv | Navigationsbeschränkungen aktiv | Im Gruppenmonitor sichtbar | Freigabewort vorausgefüllt | Aufgaben-Übersicht erlaubt | Aus Monitor steuerbar | Adaptiver Pfad frei wählbar |
|----|----|----|----|----|----|----|----|----|----|----|
| run-hot-return | ✗ | ✗ | ✓ | ✓ | ✓ | ✓ | ✗ | ✗ | ✓ | ✗ |
| run-hot-restart | ✓ | ✗ | ✓ | ✓ | ✓ | ✓ | ✗ | ✗ | ✓ | ✗ |
| run-review | ✗ | ✓ | ✗ | ✗ | ✗ | ✗ | ✓ | ✓ | ✗ | ✓ |
| run-trial | ✗ | ✓ | ✓ | ✗ | ✗ | ✓ | ✓ | ✓ | ✗ | ✓ |
| run-simulation | ✗ | ✗ | ✗ | ✓ | ✓ | ✗ | ✗ | ✗ | ✗ | ✗ |
| run-demo | ✗ | ✗ | ✗ | ✗ | ✗ | ✗ | ✓ | ✗ | ✗ | ✓ |
| monitor-group | — | — | — | — | — | — | — | — | — | — |
| monitor-study | — | — | — | — | — | — | — | — | — | — |
| sys-check-login | — | — | — | — | — | — | — | — | — | — |

**sys-check-login**: Versteckt den System-Check für alle anderen Logins. Der Check ist dann nur über Logins mit diesem Modus erreichbar.

Beispiel: Testtaker-XML

testtaker1.xml

    <Testtakers>
      <Metadata/>
      <Group id="Klasse4a" label="Klasse 4a">

        <!-- Reguläre Testperson -->
        <Login mode="run-hot-return" name="t9f5y" pw="v6e5">
          <Booklet>booklet1</Booklet>
        </Login>

        <!-- Testleitung / Gruppenmonitor -->
        <Login mode="monitor-group" name="lehrerin4a">
        </Login>

      </Group>
    </Testtakers>

Richtlinien für Login-Codes

🔤 Geeignete Zeichen

Buchstaben: `abcdefghprqstuvxyz`\
Ziffern: `2345679`\
Keine optisch ähnlichen Zeichen (n/m, 1/l). Codes beginnen mit einem Buchstaben, dann wechseln Ziffern und Buchstaben ab.

🔊 Sprechen & Tippen

Codes müssen gut sprechbar und akustisch verständlich sein. Keine Großbuchstaben oder Sonderzeichen — alle Zeichen sollten mit einer Taste erreichbar sein.

🚫 Keine Serien-Codes

Keine fortlaufenden Muster wie `gxst1`, `gxst2` etc. — Schüler\*innen raten dann schnell benachbarte Logins. Das itc-ToolBox-Programm erzeugt eindeutige, zufällige Codes.

← Booklet-XML

↩ Zur Übersicht
