# 025_TestSolutionTestDesign

> **Planungsstand · technische Erweiterung der Test-Solution-Plattform**

## Ziel

Hier entsteht die **fachliche** Gestaltung von Tests und Testvarianten. Die vorhandene Local-PAR-Logik ist zwingend zu erhalten; das endgültige Datenmodell wird **erst mit den Kollegen ab 09.11.2026** abgestimmt.

## Geplanter Funktionsumfang

- Testset mit mehreren Testläufen; Testläufe können unterschiedliche Abläufe besitzen
- Local PAR: Action-/Group-Kombination als fachlicher Testfall; Global PAR am Testset
- Parameter- und Szenariodaten einschließlich Übergaben zwischen Testläufen
- Fachliche Varianten, erwartete Ergebnisse, Abhängigkeiten und Vorlagen
- Zusammenarbeit, Austausch, Versionierung und nachvollziehbare Änderungen

## Erster Entwicklungsdurchstich

Vor dem Kollegentermin ausschließlich Bestand, Anforderungen, Beispiele und offene Fragen sammeln. **Keine irreversible Modellentscheidung und keine alternative Local-PAR-Semantik implementieren.**

## Abgrenzung

Dieses Repository verantwortet **Testdesign, Testsets, Testläufe und Parameterlogik**. Die Studio-Oberfläche, zentrale Benutzer- und Paketverwaltung sowie die generische Worker-Orchestrierung gehören nicht hierher. Technische Treiber dürfen eigenständig sein; Ablauf- und Ergebnisverträge werden gemeinsam abgestimmt.

## Gemeinsame Entwicklungsregeln

- Eigenständige Entwicklung im jeweiligen Repository, keine ungefragten Änderungen an anderen Projekten (insbesondere nicht an `014_TestSolutionModules`).
- Windows 11 als Zielplattform; lokale Tests und manuell ausgelöste GitHub-Actions-Builds statt automatischer CI-Ausführung.
- Technische Module müssen unabhängig von Studio und Server startbar, prüfbar und diagnostizierbar sein. Aufzeichnungsfähige Module benötigen eigenständige Aufnahme und Wiedergabe.
- Einheitliche versionierte Contracts für Nodes, Eingaben/Ausgaben, Fehler, Ergebnisse und Diagnose; keine parallelen inkompatiblen Laufzeit-Engines.
- Kein automatisches Installieren von Software auf Benutzergeräten; kein unkontrollierter Zugriff auf Credentials, personenbezogene Daten oder Zielsysteme.
- Dieses Dokument beschreibt die Planung und stellt noch keinen implementierten oder freigegebenen Funktionsumfang dar.

## Zusammenarbeit

Die Gesamtarchitektur und verbindlichen Schnittstellen werden in der zentralen Test-Solution-SSOT abgestimmt. Schnittstellenänderungen sind vor der Nutzung durch andere Repositories zu versionieren und mit Contract-Tests abzusichern. Entwicklung in Feature-Branches, Review per Pull Request und stabilem `main`.
