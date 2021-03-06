oparl:System (System)   {#oparl_system}
--------------------

Der Objekttyp `oparl:System` bildet grundlegende Informationen zum
parlamentarischen Informationssystem ab. Das Objekt repräsentiert
das technische System, unabhängig von der Frage, welche Körperschaften
auf diesem System vertreten sind.

Ein Beispiel:

~~~~~  {#system_ex1 .json}
{
    "@type": "oparl:System",
    "@id": "https://oparl.beispielris.de/",
    "oparlVersion": "http://oparl.org/specs/1.0/",
    "name": "Beispiel-System",
    "website": "http://www.beispielris.de/",
    "contactEmail": "mailto:info@beispielris.de",
    "contactName": "Allgemeiner OParl Kontakt",
    "vendor": "http://example-software.com/",
    "product": "http://example-software.com/oparl-server/",
    "bodies": "https://oparl.beispielris.de/bodies/",
    "newObjects": "https://oparl.beispielris.de/new_objects/",
    "updatedObjects": "https://oparl.beispielris.de/updated_objects/",
    "removedObjects": "https://oparl.beispielris.de/removed_objects"
}
~~~~~

Ein Kontext:

~~~~~  {#system_ex_context .json}
{
    "@language": "de",
    "beispielris": "https://oparl.eispielris.de/",
    "oparl": "http://oparl.org/specs/1.0/schema/",
    "dc": "http://purl.org/dc/terms/",
    "foaf": "http://xmlns.com/foaf/0.1/",
    "skos": "http://www.w3.org/2004/02/skos/core#",
    "vcard": "http://www.w3.org/2006/vcard/ns#",
    "xsd": "http://www.w3.org/2001/XMLSchema#",

    "name": {
        "@id": "skos:prefLabel",
        "@type": "@id"
    },
    "contactEmail": {
        "@id": "foaf:mbox",
        "@type": "@id"
    },
}
~~~~~

Und das System-Objekt in kompakter Form unter Verwendung des Kontext:

~~~~~  {#system_ex2 .json}
{
    "@type": "oparl:System",
    "@id": "https://oparl.beispielris.de/",
    "oparlVersion": "http://oparl.org/specs/1.0/",
    "name": "Beispiel-System",
    "website": "http://www.beispielris.de/",
    "contactEmail": "mailto:info@beispielris.de",
    "contactName": "Allgemeiner OParl Kontakt",
    "vendor": "http://example-software.com/",
    "product": "http://example-software.com/oparl-server/",
    "bodies": "beispielris:bodies/",
    "newObjects": "beispielris:new_objects/",
    "updatedObjects": "beispielris:updated_objects/",
    "removedObjects": "beispielris:removed_objects"
}
~~~~~

Auf jedem OParl Server MUSS ein Objekt vom Typ `oparl:System` vorgehalten
werden. Es DARF nur ein einziges solches Objekt je Server existieren.

Für Clients ist das `oparl:System` Objekt ein geeigneter Einstiegspunkt,
um grundlegende Informationen über das Sytem zu bekommen und die URLs
zum Zugriff auf andere Informationen in Erfahrung zu bringen.

Die URL des `oparl:System` Objekts MUSS per Definition identisch mit
der URL des API-Endpunkts des Servers sein.

### Eigenschaften

`oparlVersion`
:   Die URL der OParl-Spezifikation, die von diesem Server unterstützt 
    wird. Der Wert MUSS die URL `http://oparl.org/specs/1.0/` sein.
    Typ: URL
    ZWINGEND.

`bodies`
:   Liste der URLs der [`oparl:Body`](#oparl_body)-Objekte, also der 
    Körperschaften, die auf dem System vorliegen. Alternativ kann statt 
    einer Liste eine einzelne URL zum Abruf der Liste angeboten werden.
    Typ: URL
    ZWINGEND.

`name`
:   Nutzerfreundlicher Name für das System, mit dessen Hilfe Nutzer das
    System erkennen und von anderen unterscheiden können.
    Typ: String
    EMPFOHLEN.

`contactEmail`
:   E-Mail-Adresse für Anfragen zur OParl-API. Die Angabe einer E-Mail-Adresse dient sowohl NutzerInnen
    wie auch EntwicklerInnen von Clients zur Kontaktaufnahme mit dem
    Betreiber.
    Typ: mail-Adresse inklusive "mailto:"
    EMPFOHLEN. 

`contactName`
:   Name des Ansprechpartners oder der Abteilung, die über die `contactEmail`
    erreicht werden kann.
    Typ: Zeichenkette.
    EMPFOHLEN. 

`newObjects`
:   URL des Feeds ["Neue Objekte"](#feed_neue_objekte).
    EMPFOHLEN.
    Typ: URL

`updatedObjects`
:   URL des Feeds ["Geänderte Objekte"](#feed_geaenderte_objekte).
    Typ: URL
    EMPFOHLEN.

`removedObjects`
:   URL des Feeds ["Entfernte Objekte"](#feed_entfernte_objekte).
    Typ: URL
    EMPFOHLEN.

`website`
:   URL zur WWW-Oberfläche des parlamentarischen Informationssystem.
    Typ: URL
    OPTIONAL.

`vendor`
:   Software-Anbieter, von dem die OParl-Server-Software stammt.
    Typ: URL
    OPTIONAL.

`product`
:   Informationen zu der auf dem System genutzten OParl-Server-Software.
    Typ: URL
    OPTIONAL.
