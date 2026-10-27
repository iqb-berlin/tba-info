# XML Validierung

> **NOTE:**
>
> **Die XML Validierung ist ab der Testcenter Version 19.0.0 eingeschaltet.** Ältere Versionen validieren gar nicht oder mit veralteten Abläufen.

## Einleitung

Eine XML wird zur Validierung gegen eine XML-Schema-Definition (XSD) validiert. Die XSD dient als eine Art Schablone und legt fest was in einer XML-Datei erlaubt ist und was nicht. Damit eine XML gegen die XSD validiert werden kann, muss im Kopf der XML die Adresse zur XSD angegeben werden.

## Ort der XSD

Die XSD’s befinden sich in Repositories unter [IQB-Specifications](https://github.com/iqb-specifications/iqb-specifications.github.io):

- [Testcenter-Testtaker-xml](https://github.com/iqb-specifications/testcenter-testtaker-xml)
- [Testcenter-Booklet-xml](https://github.com/iqb-specifications/testcenter-booklet-xml)
- [Unit-xml](https://github.com/iqb-specifications/unit-xml)

Bei Änderungen an einer XSD wird ein neues Release mit entsprechenden Release-Notes in diesen Repositories erzeugt. Ein Permalink im Kopf der XML verweist auf das entsprechende Repository und den gewünschten Release-Tag.

#### Permalink zur XSD

Im Root-Element der XML-Dateien Booklet, Testtaker und Unit befindet sich ein Permalink zur XSD. Dieser verweist auf eine gültige XSD-Version (Release), die in den Repositories unter IQB-Specifications veröffentlicht wurde.

> **NOTE:**
>
> Die hier gezeigten Versionsnummern entsprechend dem Stand zum Zeitpunkt der Dokumentationserstellung und sind eventuell bereits veraltet. Prüfen Sie deshalb zuvor, ob es vielleicht bereits eine neuere Version gibt.

**Testtaker-XML**

``` xml
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:noNamespaceSchemaLocation="https://w3id.org/iqb/spec/testcenter-testtaker-xml/18.0"
```

**Booklet-XML**

``` xml
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:noNamespaceSchemaLocation="https://w3id.org/iqb/spec/testcenter-booklet-xml/18.0"
```

**Unit-XML**

``` xml
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:noNamespaceSchemaLocation="https://w3id.org/iqb/spec/unit-xml/17.6"
```

## Ablauf der Validierung

Das Testcenter prüft beim Laden einer XML folgendes:

- gültige Adresse in `xsi:noNamespaceSchemaLocation`
  - Adresse entspricht der festgelegten Norm
  - Adresse ist nicht leer
- gültige Version in `xsi:noNamespaceSchemaLocation`
  - Release-Tag existiert wirklich
- Inhalt der XML, wie in XSD festgelegt

> **NOTE:**
>
> Es gibt keinen Fallback! Wenn die Version nicht existiert, kann die XML nicht geladen werden. Es wird nicht automatisch auf die letzte aktuelle Version umgeschaltet.

Wurde eine XML angenommen und in das Testcenter geladen. Wird die zugehörige XSD-Version im Testcenter gehalten. Jede nachfolgende Validierung gegen diese XSD-Version, ist dann nicht mehr auf eine funktionierende Internetverbindung angewiesen. Das ist entscheidend für Offline-Testungen.

> **NOTE:**
>
> Zum Zeitpunkt der Installation auf einem Server, muss eine Verbindung zum Internet bestehen, damit die Docker-Images geladen werden können. Dabei werden auch die aktuellsten XSD-Versionen heruntergeladen und gehalten. Wenn der Server offline verwendet wird, werden alle XML’s gegen diese Version validiert. Wenn nach der Installation eine neue XSD-Version veröffentlicht wird und eine XML diese Version verwenden, kann das Testcenter die XML nicht validieren solange es offline ist.

### Abgleich mit der Version des Testcenters

Da Testcenter und XSD getrennt versioniert werden, muss geprüft werden, ob die verwendete Version des Testcenters die neuen Elemente und Attribute einer XSD-Version unterstützt. Es würde zu Verwirrungen führen, wenn eine XML mit neuen Inhalten vom Testcenter angenommen wird, die Inhalte aber vom Testcenter nicht gelesen und logisch weiterverarbeitet werden können. Es wird daher geprüft, ob die XSD-Version vom Testcenter unterstützt wird. Ist dies nicht der Fall, wird die XML mit einer entsprechenden Meldung abgelehnt.

Welche XSD-Version von der eingesetzen Testcenter Version unterstützt wird, ist [**hier**](https://github.com/iqb-berlin/testcenter/blob/master/definitions/compatibility.json) zu finden.

Zurück nach oben
