---
translatedFrom: en
translatedWarning: Wenn Sie dieses Dokument bearbeiten möchten, löschen Sie bitte das Feld "translationsFrom". Andernfalls wird dieses Dokument automatisch erneut übersetzt
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/de/adapterref/iobroker.wled/README.md
title: ioBroker.wled
hash: E3OIGsPjegbE2pMLuI1ubD3CpiZCu/EKcoyg+2WlpSI=
---
![Logo](../../../en/adapterref/iobroker.wled/admin/wled_logo_akemi.png)

![NPM-Version](https://img.shields.io/npm/v/iobroker.wled.svg)
![Downloads](https://img.shields.io/npm/dm/iobroker.wled.svg)
![Anzahl der Installationen](https://iobroker.live/badges/wled-installed.svg)
![Aktuelle Version im stabilen Repository](https://iobroker.live/badges/wled-stable.svg)
![Abhängigkeitsstatus](https://img.shields.io/david/DrozmotiX/iobroker.wled.svg)
![NPM](https://nodei.co/npm/iobroker.wled.png?downloads=true)

# IoBroker.wled
**Tests:** ![Testen und freigeben](https://github.com/DrozmotiX/iobroker.wled/workflows/Test%20and%20Release/badge.svg)

**Dieser Adapter verwendet den Dienst [Sentry.io](https://sentry.io), um mir als Entwickler automatisch Ausnahmen und Codefehler sowie neue Geräteschemas zu melden.** Weitere Details siehe unten!

## WLAN-Adapter für ioBroker
Eine schnelle und funktionsreiche Implementierung eines ESP8266/ESP32-Webservers zur Steuerung von NeoPixel (WS2812B, WS2811, SK6812, APA102)LEDs oder auch SPI-basierten Chipsätzen wie dem WS2801!

[WLED - Github-Projekt](https://github.com/Aircoookie/WLED) von @Aircoookie

## Anweisungen
Der Adapter versucht automatisch, WLED-Geräte in Ihrem Netzwerk mithilfe von Bonjour-Diensten zu finden.
Bekannte Probleme: Netzwerke mit VLAN-Trennung leiten den Broadcast-Datenverkehr meistens nicht weiter, was bedeutet, dass die automatische Erkennung fehlschlägt.

Keine Sorge, in diesem Fall können Sie das Gerät manuell per IP-Adresse hinzufügen.

1) Stellen Sie sicher, dass Ihr WLED-Gerät läuft und über das Netzwerk erreichbar ist 2) Installieren Sie den Adapter 3) Konfigurieren Sie die Intervallzeiten für die Datenabfrage und die automatischen Erkennungszyklen 4 - A) Starten Sie den Adapter, die Geräte sollten automatisch erkannt werden 4 - B) Wenn A fehlschlägt , verwenden Sie die Schaltfläche Gerät hinzufügen und geben Sie die IP-Adresse des Geräts ein 5) Adapter sendet Änderungen sofort und fragt Daten alle x Sekunden ab (konfigurierbar)

## Unterstütze mich
Wenn Ihnen meine Arbeit gefällt, können Sie gerne eine persönliche Spende machen (dies ist ein persönlicher Spenden-Link für DutchmanNL, keine Verbindung zum ioBroker-Projekt!) [![Spenden](https://raw.githubusercontent.com/DrozmotiX/ioBroker.wled/main/admin/button.png)](http://paypal.me/DutchmanNL)

## Was ist Sentry.io und was wird an die Server dieser Firma gemeldet?
Sentry.io ist ein Dienst für Entwickler, um sich einen Überblick über Fehler in ihren Anwendungen zu verschaffen. Und genau das ist in diesem Adapter umgesetzt.

Wenn der Adapter abstürzt oder ein anderer Code-Fehler auftritt, wird diese Fehlermeldung, die auch im ioBroker-Protokoll erscheint, an Sentry gesendet. Wenn Sie der iobroker GmbH erlaubt haben, Diagnosedaten zu sammeln, dann ist auch Ihre Installations-ID (dies ist nur eine eindeutige ID **ohne** zusätzliche Informationen über Sie, E-Mail, Name oder ähnliches) enthalten. Dadurch kann Sentry Fehler gruppieren und anzeigen, wie viele einzelne Benutzer von einem solchen Fehler betroffen sind. All dies hilft mir, fehlerfreie Adapter bereitzustellen, die im Grunde nie abstürzen.

## Changelog
<!--
    Placeholder for the next version (at the beginning of the line):
    ### __WORK IN PROGRESS__
-->
### 0.6.7 (2022-06-08) - Bugfix [#400](https://github.com/DrozmotiX/ioBroker.wled/issues/400)
* (DutchmanNL) Bugfix: Cannot read property 'initialized' of undefined handleStates solved [#400](https://github.com/DrozmotiX/ioBroker.wled/issues/400)

### 0.6.6 (2022-06-08) - Log messages and error reporting improved
* (DutchmanNL) Log messages and error reporting improved
* (DutchmanNL) Don't send missing attribute definitions to Sentry

### 0.6.5 (2022-06-04) - Correct indication of connection state
* (DutchmanNL) Dependency updates
* (DutchmanNL) Bugfix: Correct indication of connection state #307
* (DutchmanNL) Improve error messages & sentry reporting

### 0.6.3 (2021-09-08) - HotFixes
* (DutchmanNL) Missing dropdown for ID of effects added
* (DutchmanNL) HotFix: Missing axios dependency added

### 0.6.1 (2021-09-08)
* (DutchmanNL) Missing state definitions WLED FW 0.13.0-b12 added.

## License
MIT License

Copyright (c) 2022 DutchmanNL <rdrozda86@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.