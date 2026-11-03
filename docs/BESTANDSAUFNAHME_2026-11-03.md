# Bestandsaufnahme – 025_TestSolutionTestDesign

> Arbeitsstand 03.11.2026. Lesende Analyse; kein neuer Code und keine normative Vertragsfreigabe. Frühere dokumentierte Tests sind kein aktueller Live-Nachweis.

## Fachliche Aufgabe
Testset mit mehreren Testläufen und unterschiedlichen Abläufen; Local PAR und Action/Group als fachlichen Testfall erhalten.

## Technische Funktionen
Testdesign / Local PAR. Geplante Funktionen aus README und unten beschriebener Zielsetzung – noch nicht als implementiert behauptet.

## Bereits vorhandener Code und Nachweise
007 ADR-006: Excel-Original + JSON und Mapping, rückführbarer Export/Zell-Diff als angenommenes Ziel. ADR-002 Variantenvergleich. 025: README; noch kein finaler Datenvertrag.

## Wiederverwendungsmöglichkeiten
Bestehende echte anonymisierte Testsets und 007-ADRs als Fachreferenz; keine neue Semantik vor Kollegentermin.

## Schnittstellen
024 technische Flows, 026 Legacy-Import, 011/012 Zusammenarbeit und Versionen.

## Offene Entscheidungen (für mobile Gespräche)
1. Wie verbindet Lauf eigenen Flow mit Action/Group?
2. Mehrfach-Groups?
3. Szenario-Daten über Läufe?
4. Checkout?
5. Roundtrip-Sonderfälle?

## Risiken
Excel-Verluste, falsche Group-Semantik, Abhängigkeiten und Teamkonflikte.

## Erster Abnahmeschritt
Ab 09.11.: gemeinsamer Workshop mit zwei anonymisierten realen Testsets, vorher keine irreversible Implementierung.

## Quellen / SSOT
- [010 Modulvertrag und SSOT](https://github.com/ChrisMayerAux/010_TestSolutionHub/blob/main/contracts/modules/v0.1/README.md)
- [010 dokumentierter Integrationstest](https://github.com/ChrisMayerAux/010_TestSolutionHub/blob/main/berichte/MOD_TECH_INTEGRATION_02_TESTBERICHT.md)
- [007 TestCraft](https://github.com/ChrisMayerAux/007_SVLFG_TestCraft)
- [008 LegacyConverter](https://github.com/ChrisMayerAux/008_TestCraftLegacyConverter)
- [014 Module Lab, nur Referenz](https://github.com/ChrisMayerAux/014_TestSolutionModules)

Normativ bleibt die 010-SSOT. Diese Bestandsaufnahme darf ihr nicht widersprechen; offene Vertragsfragen werden dort entschieden.
