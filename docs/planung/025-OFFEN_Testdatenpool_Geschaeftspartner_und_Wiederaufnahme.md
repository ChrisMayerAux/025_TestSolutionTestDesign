# Offener Planungspunkt – Testgeschäftspartner-Pool und Wiederaufnahme

**Erfasst:** 07.11.2026  
**Status:** IDEE / OFFEN – keine Architekturentscheidung, keine Umsetzung beauftragt  
**Bezug:** Fehlerbehandlung in 022 SAP GUI und 023 Browser; Testdesign/Testdaten in 025.

## Heute beobachtetes Testverhalten

Laut Auftraggeber beginnen Testautomatisierungen im Regelfall **vollständig von vorne**. Beim Anlegen von Geschäftspartnern wird für einen neuen Testlauf ein **neuer Testgeschäftspartner** angelegt. Ein pauschales Fortsetzen mitten im Ablauf ist deshalb nicht als Standard beschlossen.

## Idee für später

Möglicherweise soll ein **Repertoire bereits angelegter Testgeschäftspartner** geführt werden, die über **Tags bzw. Merkmale** ausgewählt und für bestimmte Tests gezielt wiederverwendet werden können. Der Auftraggeber hat ausdrücklich offengelassen, **ob** dies umgesetzt wird.

Denkbare spätere Fragen:
- Neue Testdaten erzeugen vs. vorhandene tagbasierte Testdaten wiederverwenden.
- Eindeutige Kennzeichnung nach SAP-System, Mandant, Zustand und fachlichen Merkmalen.
- Reservierung und Exklusivität bei parallelen Testausführungen.
- Gültigkeit, Aktualisierung, Wiederherstellung, Verfall, Aufräumen und fachliche Trennung von Testdaten.
- Nachweis, ob ein abgebrochener SAP-Schritt bereits einen Geschäftspartner erzeugt hat; sichere Wiederaufnahme ohne Doppelanlage.
- Umgang mit schutzbedürftigen bzw. personenbezogenen Daten, Berechtigungen und Löschregeln.

## Bis zu einer späteren Entscheidung

**Kein** generischer Neustart ab beliebiger Fehlerstelle als Standard; zunächst gilt vollständiger Neustart des Testlaufs. Die bestehende Entscheidung „Fehlerverhalten pro Aktion“ (022-D-005 / 023-D-002) bleibt bestehen. Eine optionale Teil-Wiederaufnahme ist **nicht entschieden**.

Das fachliche Testdesign-Modell in 025 bleibt bis zur geplanten Abstimmung mit Kollegen offen. Keine Änderungen an 022, 023, 024 oder bestehenden Verträgen durch diesen Planungspunkt.

## Neuer Modulvorschlag: eigenständiges Testdatenmanagement

**Zusätzlicher Wunsch des Auftraggebers (07.11.2026):** Ein **eigenständiges technisches/fachliches Modul für Testdatenmanagement** vorsehen. Es soll bestehende Testdaten über **Filter** auffindbar machen und beispielsweise unterschiedliche **Geschäftspartnerarten** für einen Testlauf auswählen können.

**Vorgeschlagene allgemeine Fähigkeiten:**
- Testdatenbestände nach **Typ, Tags, Eigenschaften, SAP-System, Mandant, Status und Eignung** durchsuchen und filtern, soweit diese Metadaten bereitgestellt werden.
- Einen geeigneten Datensatz **gezielt auswählen oder regelbasiert zuteilen**; bei parallelen Testläufen eine kontrollierte Reservierung vorsehen.
- Rückmeldung an den Test nur über definierte Referenzen/Parameter; keine direkte Vermischung des Testdatenmodells mit SAP-GUI-Objektidentifikation.
- Wiederverwendbarkeit für weitere Datenarten über Geschäftspartner hinaus (z. B. Vorgänge, Konten, Web-Testdaten), ohne SVLFG-spezifische Datenmodelle fest einzubauen.
- Möglichkeit, neu erzeugte Testdatensätze später als wiederverwendbar zu katalogisieren; Datenlebenszyklus und Bereinigung noch offen.
- Zugriffsrechte, Trennung von Testumgebungen und Schutz sensibler Daten zwingend berücksichtigen.

**Architekturvorschlag zur Abgrenzung:**
- **Eigenständiges neues Modul (Nummer/Repository noch offen):** Katalog, Filter, Auswahl, Reservierung und Lebenszyklus der Testdaten.
- **025 Testdesign:** Definition, welche Testdaten ein Test benötigt (Anforderungsprofil/Parameter), nicht eigener Datenpool.
- **022 SAP GUI / 023 Browser:** Technische Bedienung des Zielsystems, nicht allgemeiner Testdatenkatalog.
- **011/013:** Autorisierte Auftragszuweisung und Ausführung; mögliche koordinierte Reservierung, sofern erforderlich.
- **010/021:** Versionsfähige Schnittstellen und Konformitätstests.

**Noch zu entscheiden:** Soll dieses Modul eine neue Nummer (z. B. 030_TestSolutionTestData) und ein eigenes Repository erhalten? Wo liegen die Datensätze (Metadaten vs. tatsächliche Werte)? Werden die Daten nur gesucht/reserviert oder auch erzeugt und gepflegt? Wer definiert fachliche Geschäftspartner-Tags?

**Wichtig:** Diese Dokumentation ist ein **Modulvorschlag**, keine technische Freigabe und keine Festlegung des 025-Testdesign-Modells vor dem Kollegengespräch.

## Entscheidung zum Umfang der ersten Ausbaustufe (07.11.2026)

**Fachlich beschlossen:** Das geplante eigenständige Modul **030_TestSolutionTestData** wird in seiner **ersten Ausbaustufe** auf folgende Fähigkeiten begrenzt:

1. **Anzeige:** Bereits vorhandene Testdatensätze, zunächst insbesondere SAP-Geschäftspartner, übersichtlich darstellen.
2. **Suche und Filterung:** Daten nach geeigneten Merkmalen, Geschäftspartnerarten, Tags sowie relevanten System-/Mandantenkontexten eingrenzen, soweit die Datenquelle solche Informationen bereitstellt.
3. **Bereitstellung für Testausführungen:** Einen ausgewählten oder anhand von Kriterien gefundenen vorhandenen Datensatz an einen Testlauf als definierte Referenz bzw. Parameter übergeben. Dabei Berechtigungen und Konflikte bei paralleler Nutzung berücksichtigen.

**Nicht Bestandteil der ersten Ausbaustufe:**
- Automatisches Anlegen neuer Geschäftspartner oder anderer Testdatensätze.
- Automatisches Ändern, fachliches Pflegen, Zurücksetzen oder Löschen/Bereinigen von Testdaten.
- Eine neue SAP-Automatisierungsengine oder ein zweites SAP-Objektmodell.

Ob und wie diese Funktionen später ergänzt werden, bleibt **ausdrücklich offen**. Die Planung soll Erweiterbarkeit ermöglichen, ohne die erste Version aufzublähen.

**Noch zu klären:** Woher der Katalog seine Einträge und Metadaten erhält, welche Berechtigungen gelten, welche Filter zuerst benötigt werden und wie Reservierung bzw. Bereitstellung technisch ablaufen. Keine Änderung an 022/025/010 oder bestehendem Code.

