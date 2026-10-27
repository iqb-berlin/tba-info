# Rechte und Rollen im IQB-Studio

# Accounts der Nutzer\*innen

Jede Person, die sich im IQB-Studio anmelden kann, wird in einer einzigen Nutzer\*innenliste verwaltet. Ein neuer Account kann nur von der obersten Rechte-Ebene - dem sog. System-Account - eingerichtet werden[^1]. Es sind neben dem Benutzernamen Informationen wie Vor-, Nachname und E-Mail-Adresse hinterlegt. Jede/r Nutzer\*in kann seine eigenen Angaben jederzeit ändern (außer den Benutzernamen). Nach dem Anlegen verfügt der Account zunächst über keine Rechte. Diese werden dem Account nachfolgend zugewiesen.

# System-Account

Bei der Installation des Studios wird ein System-Account eingerichtet. Ein System-Account verfügt über folgende Rechte:

- Nutzer\*innen und Bereichsgruppen anlegen und löschen
- anderen Nutzer\*innen den Status eines System-Accounts geben oder entziehen
- anderen Nutzer\*innen Zugriffsrechte als Bereichsgruppen-Admin geben oder entziehen
- Module (Verona) und Pakete hochladen und löschen
- Globale Einstellungen wie Text des Impressums oder Hintergrundfarbe ändern
- Übergreifende Statistiken abrufen (z. B. Nutzung von Modulen)

Nach der Anmeldung mit einem System-Account erscheint ein Admin-Symbol auf der Startseite über der Liste der Arbeitsbereiche. Mit einem Klick darauf kommt man in ein Portal, das gesondert beschrieben ist.

# Admins für Bereichsgruppen

Die Aufgaben werden in [Arbeitsbereichen](../../tasks/manage/workspaces.llms.md) bearbeitet. Diese Portale enthalten üblicherweise Aufgaben zu bestimmten Testdomänen - z. B. Lesen. Die Arbeitsbereiche wiederum sind in Gruppen zusammengefasst, die z. B. über das Fach und die Klassenstufe (Deutsch Sek 1) oder eine spezielle Funktion (Schulung) gebildet sind.

Wenn jemand die Aufgabenentwicklung starten möchte, muss hierfür eine Bereichsgruppe existieren. Über einen System-Account wird ggf. eine neue Gruppe angelegt und einem existierenden Account die Rolle **Bereichsgruppen-Admin** zugewiesen. Dieser Bereichsgruppen-Admin hat folgende Rechte:

- Arbeitsbereiche innerhalb der Gruppe anlegen und löschen
- anderen Nutzer\*innen Zugriffsrechte auf Arbeitsbereiche der Gruppe geben oder entziehen
- diverse Einstellungen für die Arbeitsbereiche innerhalb der Gruppe vornehmen

Nach der Anmeldung wird geprüft, ob Rechte als Bereichsgruppen-Admin vergeben wurden. In diesem Fall erscheint ein Admin-Symbol in der Liste der Arbeitsbereiche im Kopf der jeweiligen Bereichsgruppe. Das Portal, das man durch einen Klick darauf erreicht, ist nicht gesondert beschrieben. Statt dessen findet sich in diesem Kapitel “Aufgaben entwickeln - Organisieren” in den Funktionsbeschreibungen jeweils ein Hinweis darauf, dass dies oder jenes im Portal für Bereichsgruppen-Admins eingestellt werden könne.

# Zugriff auf Arbeitsbereiche

Ein Account mit der Rolle Arbeitsbereichs-Admin kann für vorhandene Accounts drei verschiedene Rollen für einen Arbeitsbereich innerhalb der Bereichsgruppe vergeben:

forum

**Nur Kommentieren**: Alle Informationen innerhalb eines Arbeitsbereiches stehen zur Verfügung, aber es können mit einer Ausnahme keinerlei Änderungen gespeichert werden. Die Ausnahme bezieht sich auf den letzten Reiter in einem Arbeitsbereich: Kommentieren.

edit

**Standard**: Mit dieser Berechtigung kann man Aufgaben anlegen, kopieren, exportieren, abgeben und zurückgeben sowie Berichte und Druckansichten erstellen.

supervisor_account

**Vollzugriff**: Mit dieser Berechtigung kann man zusätzlich Aufgaben verschieben, löschen, importieren, eine Aufgabe aus vorhandener Aufgabe erstellen, Aufgabenfolgen anlegen und löschen sowie Aufgabengruppen verwalten.

| Funktionalität | forum | edit | supervisor_account |
|:---|:--:|:--:|:--:|
| Aufgaben anlegen | unpublished | check_circle | check_circle |
| Aufgaben in andere Arbeitsbereiche kopieren | check_circle | check_circle | check_circle |
| Aufgaben verschieben | unpublished | unpublished | check_circle |
| Aufgaben löschen | unpublished | unpublished | check_circle |
| Aufgaben exportieren | check_circle | check_circle | check_circle |
| Aufgaben importieren | unpublished | unpublished | check_circle |
| Aufgabenfolgen anlegen | unpublished | unpublished | check_circle |
| Aufgabenfolgen löschen | unpublished | unpublished | check_circle |
| Aufgabengruppen verwalten | unpublished | unpublished | check_circle |
| Kommentare schreiben | check_circle | check_circle | check_circle |
| Berichte erstellen | check_circle | check_circle | check_circle |
| Druckansichten erstellen | check_circle | check_circle | check_circle |

Ein Editor im Studio kann aufgrund der Rolle ebenfalls seine Funktionalität variieren. Das wird beispielsweise vom Aspect-Editor praktiziert: Die vergebene Rolle “Standard” schaltet den Aspect-Editor in den sog. [Standardmodus](../../tasks/design/basic/index.llms.md), die Rolle “Vollzugriff” bewirkt den [Erweiterten Modus](../../tasks/design/extended/index.llms.md).

Nach der Anmeldung wird eine Liste mit Arbeitsbereichen angezeigt, zu denen man Zugriff hat. Mit einem Klick auf einen Eintrag kommt man zum Portal des Arbeitsbereiches. Hier gibt es eine Funktion “Nutzer:innen”, die alle Personen auflistet, die Zugriff zum Arbeitsbereich haben.

Zurück nach oben

## Fußnoten

[^1]: Ein alternativer Weg der Anmeldung über das Standardprotokoll OpenID Connect befindet sich derzeit in Erprobung. Dann können sich Interessierte selbst einen Account anlegen, der zunächst keine Rechte hat.
