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
