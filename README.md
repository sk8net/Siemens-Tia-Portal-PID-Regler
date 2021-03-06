# PID-Regler für Siemens SCL Tia-Portal

## Probleme:
Ich hatte immer viel mit Regeltechnik am Tia Portal zu tun und war einfach nie zufrieden mit den Siemens Bausteine. Ich brauche PI-Regler für Drucksteuerung und PID für Temperaturreglungen. Hier ein paar Punkte die mich störten:
- Unterschiedliche Bausteine unter verschidenen CPUs
- Nicht simulierbar
- Nicht einsehbar und notfalls änderbar
- Viel zu kompliziert mit hoher Einarbeitung
- Keine Portierbarkeit nach Codesys
- Zu hohe Integration in TIA
- Viel basteln und testen bis endlich etwas funktionierte
- Zyklische OBs und Globale DB waren zwingend nötig 
- Viele tausens Seiten Handbücher

## Arbeit:
Nach längerem Suchen habe ich keine Alternative gefunden. Aber in OSCAT eine Inspiration, da es eigentlich ziemlich simpel ist, habe ich die Funktionen neu geschrieben. Ich habe es in TIA14 und 15 für die 1200 und 1500 CPU geschrieben. Jetzt habe ich alles schon länger im produktiven Einsatz und wollte mal schauen was Ihr dazu meint. 
Meine Intention war nicht jeden glücklich zu machen, sondern etwas zurück zugeben. Ich habe dank offener Libs (OSCAT) viel gelernt und es währe nicht richtig, wenn ich jetzt für immer auf meinen Sourcen sitzen bleibe. 

## Portierung:
Anmerkung zum Portieren auf Step-7, Codesys oder ähnlich:

    #VergangeneZeit := LREAL_TO_REAL(RUNTIME(#StaticZyklusZeit_Aux));
    IF #VergangeneZeit > 0 AND #VergangeneZeit < 0.1 THEN
    
Die erste Zeile liefert die Zeit zwischen zwei Aufrufe in Sekunden zurück. Die Auflösung ist bis zur Nanosekunde genau. Die zweite prüft die Gültigkeit. Bei Step-7 würde ich die Zeit als Parameter übergeben, bei Codesys kann TIME_TCK verwendet werden. Auf 300er kann eventuell auch mit "SFC64"(TIMETICK) gearbeitet werden. 

## Offene Arbeiten
- Anleitung schreiben
- Musterprojekte erstellen
- Alles auf Englisch umstellen
- Fehlerbeseitigung
- Portieren auf verschiedene Steuerungen

## License:
This project is released under the WTFPL LICENSE.
<a href="http://www.wtfpl.net/"><img src="http://www.wtfpl.net/wp-content/uploads/2012/12/wtfpl-badge-4.png"
       width="80" height="15" alt="WTFPL" /></a>
