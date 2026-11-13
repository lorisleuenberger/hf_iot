# Initialisierungsbericht
Autor: Loris Leuenberger, 25B

| Initialisierung | |
|---|---|
| **Projektname:** | Nachttischlampe mit Uhr, Wecker und Luftqualitätsanzeige |
| **Ausgangslage** | Ich habe morgens Mühe, aufzustehen wenn der Wecker klingelt. Oft werde ich mitten aus dem Tiefschlaf gerissen und neige dann dazu, lange zu schlummern. |
| **Projektziele:** | Ich möchte Device, welches mich auf langsame natürliche Weise weckt, und welches mich dazu forciert, wach zu werden und keinen easy schlummer Button hat. Zudem möchte ich ein All-in-One Gerät welches viele Funktionen bietet, ohne meinen Nachttisch zu überfüllen.<br/> Dieses Gerät würde in etwa so aussehen <br/> ![Nachttischlampe Beispiel](img/nachttischlampe.jpeg)<br/> Folgende Funktionalitäten sind das Ziel:<br/> - Das ganze Device ist an den HomeAssistant angebunden und kann dementsprechend automatisiert werden<br/> - Eine dimmbare LED Lampe mit WRGB Optionen<br/>- Ein kleines Display mit einer Zeitanzeige und Co2 Gehalt der Luft<br/>- Eingebauter Lautsprecher<br/>- Weckerfunktion: Sowohl Lampe und Sound werden auf festgelegten Zeitpunkt hin heller/lauter.<br/>- Wecker abstellen Minigame: Eine Abfolge an Pfeilen erscheint auf dem Display und muss über ein integriertes D-Pad eingegeben werden damit der Wecker abstellt. Als Backup/Alternative kann der Wecker über HomeAssistant gestoppt werden. |
| **Abgrenzungen:** | Im Fokus hier steht die Technische/Funktionelle Ausarbeitung. Ich behalte mir vor, am Aussehen/Design des Gerätes Änderungen vorzunehmen während der Umsetzung/Testing. Z.B. kann ich mir auch vorstellen, die LEDs oben an meinem Bettrahmen anzumachen oder ggf. noch mehr Lampen in meinem Zimmer an die Wecker Funktionalität zu koppeln. Ein z.B. 3D gedrucktes Gehäuse wäre eine super Sache, ist aber nicht Priorität. |
| **Meilensteine** | Folgende Meilensteine gibt es in dem Projekt:<br><br>• Lieferung der Hardware<br>• Zusammenbauen der Komponenten<br>• Installation der Software<br>• Test der verschiedenen Funktionen durchgeführt |
| **Termine** | KW48 2026: Lieferung der Hardware<br>KW49 2026: Zusammenbauen der Komponenten<br>KW50 2026: Installation der Software<br>KW51 2026: Test der verschiedenen Funktionen durchgeführt<br>KW51 2026: Projektabgabe |
| **Kosten** | Geschätzte Materialkosten: **ca. CHF 100 - 150** (ohne optionales Gehäuse / 3D-Druck). Der genaue Betrag kann variieren je nach Versandkosten etc. |
| **Personenaufwand** | 1 Projektmitglied: Loris Leuenberger. Geplanter Aufwand: ca. 15–25 Stunden für Planung, Beschaffung, Aufbau, Programmierung, Integration und Testing. |
| **Sachmittel** | Ich habe mir von AI helfen lassen und das ganze so gut wies geht überprüft. Es kann aber sein, dass noch kleinere Teile dazukommen:<br/>- 1× ESP32-S3 DevKitC-1 N8R8 als zentrale Steuereinheit<br>- 1× SK6812 RGBW LED-Streifen (5 V, ca. 1 m)<br>- 1× SN74AHCT125 Pegelwandler für die LED-Datenleitung<br>- 1× OLED-Display (1,3 Zoll, 128 × 64 Pixel, I²C)<br>- 1× Sensirion SCD41 CO₂-Sensor<br>- 1× 5-Wege-Navigationsmodul als D-Pad<br>- 1× MAX98357A I²S-Audioverstärker<br>- 1× Lautsprecher (4 Ω, 3 W)<br>- 1× 5-V-Netzteil (voraussichtlich 5 A, abhängig von der LED-Anzahl)<br>- 1× 330-Ω-Widerstand und 1× 1000-µF-Kondensator<br>- Sicherung, Anschlussbuchse, Kabel, Steckverbinder und Verteilerplatine |
| **Auftraggeber** | Thomas Staub |
| **Projektleiter** | Loris Leuenberger |
| **Projektmitglieder** | Loris Leuenberger |
| **Projektausschuss** | Thomas Staub, Loris Leuenberger |
| **Verteiler** | Thomas Staub, Loris Leuenberger |
