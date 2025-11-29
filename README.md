Logisches Datenmodell (meta-bv)
===============================

**Status:** Prototyp / Konzept

Dies ist der Prototyp für einen **Datenkatalog** des Bundesamtes für Bauten und Logistik (BBL), Bereich Bauten. Ziel ist die transparente Dokumentation und Verknüpfung von Geschäftsobjekten, Metadaten und Attributen gemäss dem DCAT-AP CH Standard.

Live Demo
---------

Die aktuelle Version des Prototypen ist via GitHub Pages verfügbar:

[**Zur Live-Anwendung**](https://davras5.github.io/meta-bv/ "null")

![Preview](images/readme/Preview.JPG)

Technologie
-----------

Dieses Projekt ist als minimalistischer **Single-File-Web-Prototyp** konzipiert, um maximale Einfachheit und schnelle Bereitstellung zu gewährleisten.

-   **HTML5:** Struktur und Layout

-   **CSS3:** Styling mittels CSS-Variablen und Responsive Design.

-   **JavaScript (Vanilla JS):** Dynamisches Laden der Daten, Routing (via Hash), Filterung, View-Umschaltung (Grid/List) und Rendering der Detailansichten.

-   **Datenquelle:** Der Katalog wird über eine externe `data.json` Datei befüllt (nicht im Code enthalten, muss im Repository vorhanden sein).

Funktionen (Frontend)
---------------------

-   **Navigation:** Hash-basierte Navigation zwischen den Hauptansichten (Datenmodell, Über, Handbuch).

-   **Datenanzeige:** Umschaltung zwischen Grid-Card-Ansicht und detaillierter Listenansicht.

-   **Suche/Filter:** Dynamische Suche über Titel, Beschreibung und Tags.

-   **Detailansicht:** Detaillierte Ansicht eines Geschäftsobjekts, einschliesslich Metadaten und Attribute-Tabelle (PK/FK/Format-Badges).

-   **Corporate Design:** Verwendung des offiziellen Schweizer Wappens als Inline-SVG und der Schriftfamilie "Frutiger" (via Fallback-Stack) für ein authentisches Erscheinungsbild der Bundesverwaltung.

-   **Dokumentation:** Integrierte "Über"- und "Handbuch"-Sektionen für die statische Konzeptdokumentation.
