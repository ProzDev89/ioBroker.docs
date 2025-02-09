---
translatedFrom: en
translatedWarning: Wenn Sie dieses Dokument bearbeiten möchten, löschen Sie bitte das Feld "translationsFrom". Andernfalls wird dieses Dokument automatisch erneut übersetzt
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/de/adapterref/iobroker.plex/README.md
title: ioBroker.plex
hash: YzUZPhFRNPLV/ihYasl3YnhG5wbHqo2qD3QJEfKyJMM=
---
![Logo](../../../en/adapterref/iobroker.plex/admin/plex.jpg)

![Anzahl der Installationen](http://iobroker.live/badges/plex-installed.svg)
![stabile Version](http://iobroker.live/badges/plex-stable.svg)
![NPM-Version](http://img.shields.io/npm/v/iobroker.plex.svg)
![Travis CI](https://travis-ci.org/Zefau/ioBroker.plex.svg?branch=master)
![Downloads](https://img.shields.io/npm/dm/iobroker.plex.svg)
![Greenkeeper-Abzeichen](https://badges.greenkeeper.io/Zefau/ioBroker.plex.svg)
![NPM](https://nodei.co/npm/iobroker.plex.png?downloads=true)

# IoBroker.plex Integration des Plex Media Servers in ioBroker (mit oder ohne Plex Pass). Darüber hinaus Tautulli-Integration.
**Inhaltsverzeichnis**

1. [Funktionen] (Nr. 1-Funktionen)
2. [Setup Anweisungen] (# 2-Setup-Anweisungen)
   1. [Grundeinstellung] (# 21-Grundeinstellung)
   2. [Erweitertes Setup] (# 22-Erweitertes-Setup-Plex-Pass-or-Tautulli)
3. [Channels & States] (# 3-Kanäle - Staaten)
   1. [mit Basic Setup] (# 31-mit-Basis-Setup)
   2. [mit erweitertem Setup] (# 32-mit-erweitertem-Setup)
4. [Changelog] (# changelog)
5. [Lizenz] (# Lizenz)

## 1. Eigenschaften
tbd

## 2. Setup-Anweisungen
### 2.1. Grundeinstellung
Für die Grundeinstellung müssen Sie lediglich die IP-Adresse (und den Port) Ihrer Plex-Installation angeben. Darüber hinaus müssen Sie Benutzer und Kennwort für den Adapter angeben, um Daten von Plex abzurufen.

Wenn Sie Benutzer und Kennwort nicht im Adapter speichern möchten, können Sie die ioBroker-IP in Ihren Plex-Einstellungen auf eine Whitelist setzen. Gehen Sie dazu zu den `Settings` Ihres Plex Media Servers und zu `Network`. Geben Sie die ioBroker-IP-Adresse in die beiden Felder `LAN Networks` und `List of IP addresses and networks that are allowed without auth` ein:

![Plex-Netzwerkeinstellungen](../../../en/adapterref/iobroker.plex/img/screenshot_plex-networksettings.jpg)

Sobald dies angegeben ist, ruft ioBroker.plex alle grundlegenden Daten (einschließlich Server, Bibliotheken) ab. Die vollständige Liste der Grunddaten finden Sie in [Kanäle und Bundesstaaten](#21-with-basis-setup).

### 2.2. Erweitertes Setup (Plex Pass oder Tautulli)
#### 2.2.1. Plex Pass
Wenn Sie ein Plex Pass-Benutzer sind, können Sie in den Plex-Einstellungen [einen Webhook einrichten](https://support.plex.tv/articles/115002267687-webhooks/#toc-0) das aktuelle Ereignis / die aktuelle Aktion von Ihrem Plex Media-Server abrufen (Abspielen, Anhalten, Fortsetzen, Stoppen, Anzeigen und Bewerten).

Navigieren Sie zu Ihrem Plex Media Server und gehen Sie zu ```Settings``` und ```Webhook```. Erstellt einen neuen Webhook, indem Sie auf ```Add Webhook``` klicken und Ihre ioBroker-IP-Adresse mit dem in den ioBroker.plex-Einstellungen angegebenen benutzerdefinierten Port eingeben. ```http://192.168.178.29:41891/plex```:

![Plex Webhook](../../../en/adapterref/iobroker.plex/img/screenshot_plex-webhook.png)

#### 2.2.2.Tautulli
[Tautulli ist eine Drittanbieteranwendung] (https://tautulli.com/#about), die Sie zusammen mit Ihrem Plex Media Server ausführen können, um Aktivitäten zu überwachen und verschiedene Statistiken zu verfolgen. Am wichtigsten ist, dass diese Statistiken enthalten, was gesehen wurde, wer es gesehen hat, wann und wo sie es gesehen haben und wie es gesehen wurde. Alle Statistiken werden in einer ansprechenden und übersichtlichen Oberfläche mit vielen Tabellen und Grafiken dargestellt, sodass Sie problemlos mit Ihren Servern für alle anderen prahlen können. Überprüfen Sie [Tautulli Preview] (https://tautulli.com/#preview) und [installieren Sie es auf Ihrem bevorzugten System](https://github.com/Tautulli/Tautulli-Wiki/wiki/Installation) wenn Sie interessiert sind.

Dieser Adapter stellt eine Verbindung zum [Tautulli API](https://github.com/Tautulli/Tautulli/blob/master/API.md) her und empfängt auch Webhook-Ereignisse von Tautulli.

##### 2.2.2.1. API
Öffnen Sie nach der Installation von Tautulli die Seite _Einstellungen_ im Tautulli-Dashboard und navigieren Sie zu _Webschnittstelle_. Scrollen Sie zum Abschnitt _API_ und vergewissern Sie sich, dass ```Enable API``` markiert ist. Kopieren Sie den ```API key``` und tragen Sie ihn in die ioBroker.plex-Einstellungen ein. Fügen Sie außerdem die Tautulli-IP-Adresse und den Port hinzu, um die API-Kommunikation zu ermöglichen.

##### 2.2.2.2. Webhook
###### Überblick
Befolgen Sie zum Einrichten eines Webooks mit Tautulli die nachstehenden Anweisungen und vergewissern Sie sich, dass Sie alle vier Schritte ausgeführt haben:

1. Fügen Sie den Notification Agent hinzu
2. Konfigurieren Sie Webhook im Notification Agent
3. Konfigurieren Sie die Trigger im Notification Agent
4. Konfigurieren Sie die Daten im Notification Agent
5. Konfigurieren Sie die Benachrichtigungsoptionen

###### Beschreibung
Nach der Installation öffnen Sie die Einstellungsseite im Tautulli-Dashboard und navigieren Sie zu Notification Agents (siehe unten):

![Tautulli-Einstellungen](../../../en/adapterref/iobroker.plex/img/screenshot_tautulli-settings.png)

1. Klicken Sie auf "Neuen Benachrichtigungsagenten hinzufügen" und auf "Webhook".
2. Geben Sie Ihre ioBroker-IP-Adresse mit dem in den ioBroker.plex-Einstellungen angegebenen benutzerdefinierten Port ein und folgen Sie dem Pfad `` `/ tautulli```, z. `` `http://192.168.178.29: 41891 / tautulli```:

![Tautulli Webhook](../../../en/adapterref/iobroker.plex/img/screenshot_tautulli-webhook.png) Wählen Sie außerdem ```POST``` für die _Webhook-Methode_ und geben Sie eine beliebige Beschreibung in _Description_ ein.

3. Wechseln Sie anschließend zur Registerkarte _Triggers_, und wählen Sie die gewünschten (oder einfach alle) Optionen aus
4. Tragen Sie nun __wichtigst__ die entsprechende Datennutzlast in der Registerkarte _Data_ gemäß der [hier gefundenen Benachrichtigungskonfiguration] ein (README-tautulli.md # notification-configuration). Kopieren Sie den gesamten Inhalt in die ersten vier Benachrichtigungsagenten (`` `Wiedergabe starten```,` `` Wiedergabe stoppen```, `` `Wiedergabe anhalten``` und` `` Wiedergabe fortsetzen```), wie unten gezeigt für `` `Playback Start```:

   ![Tautulli-Benachrichtigung](../../../en/adapterref/iobroker.plex/img/screenshot_tautulli-notification.png)

5. Aktivieren Sie abschließend die Option "Aufeinanderfolgende Benachrichtigungen zulassen", um das Senden aufeinanderfolgender Benachrichtigungen zuzulassen (z. B. sowohl überwachte als auch gestoppte Benachrichtigungen):

   ![Tautulli-Benachrichtigungseinstellungen](../../../en/adapterref/iobroker.plex/img/screenshot_tautulli-notification_settings.png)

## 3. Kanäle und Bundesstaaten
Wenn sowohl die Grundkonfiguration als auch die erweiterte Konfiguration konfiguriert sind, werden die folgenden Kanäle angezeigt (Bibliotheken, Server und Benutzer sind natürlich nur Beispiele). Siehe weiter unten für [vollständige Liste der Kanäle und Bundesstaaten](#21-with-basis-setup).

![Beispiel für Kanäle und Bundesstaaten](../../../en/adapterref/iobroker.plex/img/screenshot_plex-states.jpg)

### 3.1. Mit Basis Setup
Nach erfolgreicher Grundeinstellung werden die Kanäle gemäß folgender Tabelle angelegt. Für eine Liste aller Staaten, die erstellt werden, bitte [Siehe spezielle Liste der Bundesstaaten](README-states.md#with-basis-setup).

| Kanal / Ordner | Beschreibung |
| ------- | ----------- |
| __bibliotheken__ | Plex-Bibliotheken |
| __servers__ | Plex Server |
| __Einstellungen__ | Plex-Einstellungen |

### 3.2. Mit erweitertem Setup
Nach erfolgreichem Advanced Setup werden zusätzlich folgende Kanäle angelegt. Für eine Liste aller Staaten, die erstellt werden, bitte [Siehe spezielle Liste der Bundesstaaten](README-states.md#with-advanced-setup).

| Kanal / Ordner | Beschreibung | Bemerkung |
| ---------------- | ----------- | ------ |
| __ \ _ spielen__ | Plex Media wird abgespielt | mit Plex Pass oder Tautulli |
| __Statistik__ | Plex Watch Statistics | nur mit Tautulli |
| __users__ | Plex Benutzer | nur mit Tautulli |

## Changelog

### 1.0.0 (2019-xx-xx) [MILESTONES / PLANNED FEATURES FOR v1.0.0 RELEASE]
- add support for all Tautulli triggers
- add playback control for players

### 0.3.0 (2019-05-16)
- ([@Apollon77](https://github.com/Apollon77)) updated testing for Node.js v12 ([#6](https://github.com/Zefau/ioBroker.plex/pull/6))
- added support / discovery in [iobroker.discovery](https://github.com/ioBroker/ioBroker.discovery) ([#62](https://github.com/ioBroker/ioBroker.discovery/pull/62))
- added playlists to states
- added state description for object tree ```_playing```
- updated German translation (instead of generating it from English)

### 0.2.0 (2019-05-14)
- added authentication method (using Plex user and Plex password)
- fixed @iobroker/adapter-core dependency

### 0.1.0 (2019-04-26)
- get initial data from Plex API
- receive events from Plex Webhook (Plex Pass only)
- receive events from Tatulli (if used)

## License
The MIT License (MIT)

Copyright (c) 2019 Zefau <zefau@mailbox.org>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.