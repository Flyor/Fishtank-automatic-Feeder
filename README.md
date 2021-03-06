# Fishtank-automatic-Feeder
Creating an automatic feeding system for a fishtank, using a 3D Printer and a Servomotor of a central locking system from a car. 




# Bauteilliste (in English below):
- 2x M3x16 Schrauben
- 2x 3,5x16 Senkkopfschrauben
- 2x 3,5x20 Senkkopfschrauben
- Universal Stellmotor für Zentralverriegelung (2 oder 5 PIN Variante ist egal)
- 
![Vorschau](https://github.com/Flyor/Fishtank-automatic-Feeder/blob/main/Pcitures/Servomotor.jpg)

Bitte das Bild abgleichen, es gibt auch optisch andere Varianten welche natürlich nicht mit den Druckdaten zusammenpasst!

- ESP8266 (zum Beispiel D1 Mini) mit Tasmota
- Relaisshield für D1 Mini
- 5V USB Ladegerät, vorzugsweise 2,4A (1A funktioniert meistens auch)
- USB A zu USB Micro Kabel 
- "JBL Click Dispenser"

# 3D Druckteile
Die Druckteile wurden alle in einer Auflösung von 0,2mm auf einem PRUSA MINI gefertigt, daher sind die beiden Chassis auch getrennt. Wer eine größere Druckfläche hat, kann dise natürlich zusammenfügen. Als Material wurde PETG verwendet, Infill 30%. 


# Konfiguration Tasmota
Lediglich 2 Konfigurationen sind in der Console des ESP nötig, dass nach dem Einschalten das Relais nach kurzer Zeit automatisch abfällt. 
```
PowerOnState 0
```
```
PulseTime 4
```

Über die Weboberfläche kann im Menüpunkt Einstellungen/Zeitplan konfigurieren eine Wiederholung festgelegt werden. Es ist lediglich ein "on" Befehl nötig, da das ausschalten von Tasmota selbst übernommen wird (durch den Befehl "PulseTime"). 

# Anschluss
Auch wenn der Stellmotor für 12V ausgelegt ist, funktionert er auf 5V aus dem USB Netzteil ausreichend stark, um das Futter aus dem Spender abzusetzen. 
Beim Anschluss des Stellmotors wird lediglich Plus und Minus benötigt. Hat man einen 5-poligen Stellmotor, muss man die beiden passenden Leitungen (durch ausprobieren) ermitteln. Der Rest bleibt unbelegt. Bitte beim Anschluss unbedingt darauf achten, dass am Relais der Wechsler für "NO / Normally Open" genutzt wird - also den Schließer Kontakt. 

# Integration
Mit Hilfe von Tasmota, ist das System nahezu überall integrierbar. Per MQTT oder direktem URL Kommando kann das System ebenfalls bedient werden. Auch eine Simulation des Gerätes für Alexa ist in Tasmoata onboard, so kann man beispielsweise ein Routine erstellen á la: "Alexa, füttere die Fische". 


# To be done
- Snap On Chassis for the whole device at the fishtank
- Include the ESP8266 and the Relais at the Chassis  (rework the Printfiles)
