---
translatedFrom: en
translatedWarning: Если вы хотите отредактировать этот документ, удалите поле «translationFrom», в противном случае этот документ будет снова автоматически переведен
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/ru/adapterref/iobroker.enigma2/README.md
title: ioBroker enigma2
hash: CMhfYP3QyUUKiVNuORpPGTP5bZbsc8c3fhhCmrAFUBI=
---
![Логотип](../../../en/adapterref/iobroker.enigma2/admin/enigma2.png)

![версия NPM](http://img.shields.io/npm/v/iobroker.enigma2.svg)
![Загрузки](https://img.shields.io/npm/dm/iobroker.enigma2.svg)
![НПМ](https://nodei.co/npm/iobroker.enigma2.png?downloads=true)

----

# IoBroker enigma2
- Адаптер для ioBroker для получения информации от приемника enigma2 и отправки команд
- (Адаптер работает только на одном хосте! с установкой клиента пока еще проблемы.)

- (DE) Адаптер для ioBroker um Informationen von einem enigma2 Receiver abzufragen und Befehle zu Senden
- (DE)(Adapter läuft nur auf einem Host! Bei einer Client Installation gib's aktuell noch probleme.)

## Форум
[![ioBroker](https://forum.iobroker.net/assets/uploads/system/site-logo.png)](https://forum.iobroker.net/topic/25112/enigma2-adapter-ab-v1-2-3)

----

### Функции
- BOX_IP
- СЕТЬ
- CHANNEL_SERVICEREFERENCE
- КАНАЛ_СЕРВИСРЕФЕРЕНЦИЯ_ИМЯ
- КАНАЛ
- ОПИСАНИЕ СОБЫТИЯ
- ПРОДОЛЖИТЕЛЬНОСТЬ СОБЫТИЯ
– СОБЫТИЕDURATION_MIN
- МЕРОПРИЯТИЕ
– EVENTREMAINING_MIN
– EVENT_PROGRESS_PERCENT
– EVENT_TIME_START
- EVENT_TIME_END
– EVENT_TIME_PASSED
- HDD_CAPACITY
- HDD_БЕСПЛАТНО
- MESSAGE_ANSWER
- МОДЕЛЬ
- ПРИГЛУШЕН
- ПРОГРАММА
- PROGRAMM_INFO
- ПРОГРАММА_ПОСЛЕ
- PROGRAMM_AFTER_INFO
- ПОДДЕРЖИВАТЬ
- ОБЪЕМ
- WEB_IF_VERSION
- isRecording
- Timer_is_set
- MOVIE_LIST (только openwebif)
- ТАЙМЕР_СПИСОК
- CHANNEL_PICON (Picon path - только openwebif)

----

### Основной
- enigma2-СОЕДИНЕНИЕ

----

### Команда
- команда.CHANNEL_DOWN
- команда.CHANNEL_UP
- команда.ВНИЗ
- команда.ВВЕРХ
- команда.EPG
- команда.ВЫХОД
- команда.СЛЕВА
- команда.МЕНЮ
- команда.MUTE_TOGGLE
- команда.ОК
- команда.ПАУЗА
- команда.ИГРАТЬ
- команда.РАДИО
- команда.REC
- command.ДИСТАНЦИОННОЕ УПРАВЛЕНИЕ
- команда.ПРАВО
- команда.SET_VOLUME
- команда.STANDBY_TOGGLE
- команда.СТОП
- команда.ТВ
- команда.ВВЕРХ
- команда.VOLUME_DOWN
- команда.VOLUME_UP
- command.ZAP = отправить неверную ссылку на сервис

----

### Основная команда
- main_command.DEEP_STANDBY = Глубокий резерв
- main_command.REBOOT = Перезагрузить
- main_command.RESTART_GUI = Перезапустить Enigma2 (GUI)
- main_command.STANDBY = Режим ожидания
- main_command.WAKEUP_FROM_STANDBY = Форма пробуждения в режиме ожидания

----

### Сообщение
 - Message.Text = Текст сообщения (Enter -> Отправить)
 - Message.Type = Число от 0 до 3 (0=Да/Нет; 1=Информация; 2=Сообщение; 3=Внимание)
 - Message.Timeout = время ожидания сообщения в сек. Может быть пустым или числом секунд, через которое сообщение должно исчезнуть.

----

### Alexa_Command
 - Alexa_Command.Mute = Команда Alexa
 - Alexa_Command.Standby = Команда Alexa

----

 ### Отправить
#### (в блочном)
 - сообщение = Текст сообщения
 - msgType = Число от 0 до 3 (0=Да/Нет; 1=Информация; 2=Сообщение; 3=Внимание)
 - timeout = время ожидания сообщения в сек. Может быть пустым или числом секунд, через которое сообщение должно исчезнуть.

![Рекламный текст](../../../en/adapterref/iobroker.enigma2/admin/enigma2_message2.png)

### Или ![Рекламный текст](../../../en/adapterref/iobroker.enigma2/admin/enigma2_message.png)
[> zum Блочный импорт <](admin/Blockly_Import.md)

#### (в Java)
```
sendTo("enigma2.0", "send", {
   "message": 'Test Nachricht', /* Text of Message */
   "timeout": 26,               /* timeout of Message in sec. (Can be empty or the Number of seconds the Message should disappear after.) */
   "msgType": 1                 /* Number from 0 to 3 (0= Yes/No ; 1= Info ; 2=Message ; 3=Attention) */
});
```

## Changelog
<!--
    Placeholder for the next version (at the beginning of the line):
    ### **WORK IN PROGRESS**
-->
### 2.0.2 (2023-08-17)
* (Lucky-ESA) Bugfixes: [#61](https://github.com/Matten-Matten/ioBroker.enigma2/issues/61)
* (Lucky-ESA) Bugfixes: undefined e2eventlist
* (bluefox) Added json config
* (mcm1957) Adapter now requires node 16

### 1.5.0 (2023-05-05)
* (mcm1957) The adapter has been moved into iobroker-community-adapters organisation
* (mcm1957) changed: Testing has been added and changed to support node 16, 18 and 20
* (mcm1957) changed: Dependencies have been updated
* (mcm1957) changed: issues reported by adapter-checker have been fixed (#15)

### 1.4.0 (2022-04-11)
* (foxriver76) compatibility to js-controller v5

### 1.3.3 (2021-06-07)
* (TDCroPower)          Bugfixes: [#48](https://github.com/Matten-Matten/ioBroker.enigma2/issues/48)

### 1.3.2 (2020-08-22)
* (Matten-Matten)       add: `.command.VOLUME_UP` & `.command.VOLUME_DOWN`([#41](https://github.com/Matten-Matten/ioBroker.enigma2/issues/41))

### 1.3.1 (2020-08-20)
* (Matten-Matten)       correction in `.enigma2.Timer_is_set` & `.enigma2.isRecording` with login handling

### 1.3.0 (2020-02-08)
* (Matten-Matten)       add: `connectionType` and `dataSource` in `io-package.json`
* (Matten-Matten)       bugfix: in `.enigma2.CHANNEL_PICON`

### 1.2.9 (2019-12-10)
* (Scrounger)           bugfix: Movielist generates high load [#33](https://github.com/Matten-Matten/ioBroker.enigma2/issues/33)
* (Matten-Matten)       bugfix: Blockly [#31](https://github.com/Matten-Matten/ioBroker.enigma2/issues/31)

### 1.2.8 (2019-11-30)
* (Matten-Matten)       add: `.enigma2.CHANNEL_PICON` (Picon path - only openwebif)
* (Matten-Matten)       add: Select / Deselect Timer List in the Adapter Config mask
* (Matten-Matten)       add: Select / Deselect Movie List in the Adapter Config mask
* (Matten-Matten)       add: new Logo

### 1.2.7 (2019-11-30)
* (Matten-Matten)       correction in (Blockly Block) to sending Messages

### 1.2.6 (2019-11-29)
* (Matten-Matten)       add: `sendTo` (Blockly) to sending Messages
* (Scrounger)           add: `.enigma2.MOVIE_LIST`

### 1.2.5 (2019-11-17)
* (Scrounger)           add: `.enigma2.Timer_list` [#25](https://github.com/Matten-Matten/ioBroker.enigma2/issues/25) (Merge pull request [#28](https://github.com/Matten-Matten/ioBroker.enigma2/issues/28))

### 1.2.4 (2019-10-20)
* (Matten-Matten)       add: `.enigma2.Timer_is_set` ([#23](https://github.com/Matten-Matten/ioBroker.enigma2/issues/23))

### 1.2.3 (2019-09-15)
* (Matten-Matten)       authentication correction in `.enigma2.isRecording` check
* (Matten-Matten)       correction in `.enigma2.isRecording` check after shutdown

### 1.2.2 (2019-09-05)
* (Matten-Matten)       correction in `.enigma2.isRecording` check

### 1.2.1 (2019-08-07)
* (Matten-Matten)       add: `.enigma2.isRecording` ([#12](https://github.com/Matten-Matten/ioBroker.enigma2/issues/12))

### 1.2.0 (2019-05-14)
* (Matten-Matten)      ([#17](https://github.com/Matten-Matten/ioBroker.enigma2/issues/17)) `.Alexa_Command.Mute` & `.Alexa_Command.Standby` now with status feedback
* (Matten-Matten)       add: `.enigma2.EVENT_TIME_PASSED`

### 1.1.9 (2019-02-04)
* (Matten-Matten)      (#14) add enigma2.EVENTDURATION_MIN in Minute
* (Matten-Matten)      (#14) add enigma2.EVENTREMAINING_MIN in Minute
* (Matten-Matten)      Troubleshooting in standby toggle
* (Matten-Matten)      Troubleshooting in the "eventlist" query

### 1.1.8 (2019-01-10)
* (Matten-Matten)      enigma2.EVENTDURATION decoded in H:M:S
* (Matten-Matten)      enigma2.EVENTREMAINING decoded in H:M:S

### 1.1.7 (2019-01-09)
* (Matten-Matten)      enigma2.EVENT_PROGRESS_PERCENT
* (Matten-Matten)      enigma2.EVENT_TIME_START
* (Matten-Matten)      enigma2.EVENT_TIME_END

### 1.1.6 (2018-11-18)
* (Matten-Matten)      command.ZAP (send an invalid servicereference)

### 1.1.5 (2018-11-17)
* (Matten-Matten)      add Alexa_command

### 1.1.4 (2018-11-16)
* (Matten-Matten)      add main_command

### 1.1.3 (2018-11-15)
* (Matten-Matten)      remove Timer

### 1.1.2 (2018-11-01)
* (Matten-Matten)      Bug Fix

### 1.1.1 (2018-10-26)
* (NightWatcher)      CodeCleaning

### 1.1.0 (2018-10-26)
* (Matten-Matten)      add Timer, max 8 Timer
* (Matten-Matten)      add manually updating Timer states
* (Matten-Matten)      optimizations 
* (Matten-Matten)      auto Check HDD (max.2 HDD)
* (Matten-Matten)      add manually updating Enigma2 states
* (Matten-Matten)      read the device information only at the adapter start
* (Matten-Matten)      fixed hard disk (HDD) update Time every 30 sec.

### 1.0.0 (2018-10-23)
* (Matten-Matten)      add command.REMOTE-CONTROL
* (Matten-Matten)      Message optimized
* (Matten-Matten)      Command-Button integrated (no extra script needed!)

### 0.4.3 (2018-10-21)
* (Matten-Matten)      Nicht bestätigte Werte und zustände (rot angezeigt) angepasst
* (Matten-Matten)      Message um ein Objekt erweitert "ANSWER_IS"
* (Matten-Matten)      Button BUTTON SCRIPT auf V3.4 angepasst

### 0.4.2 (2018-10-05)
* (Matten-Matten)      Button Probleme bei Dreamwebif angepasst
* (Matten-Matten)      Button BUTTON SCRIPT auf V3.1 angepasst

### 0.4.1 (2018-09-21)
* (Matten-Matten)      Button werden gelöscht wenn in der Config "BUTTON SCRIPT" deaktiviert wird
* (Matten-Matten)      Alexa (Mute,Standby)

### 0.3.3 (2018-09-20)
* (Matten-Matten)      Message senden hinzugefügt
* (Matten-Matten)      Message answer (true/false) hinzugefügt
* (Matten-Matten)      Message.Question_Activ hinzugefügt

### 0.3.0 (2018-08-19)
* (Matten-Matten)      enigma2-CONNECTION hinzugefügt
* (Matten-Matten)      Update Configurationsmaske
* (Matten-Matten)      Update ENIGMA 2 BUTTON SCRIPT V2.0 (nur noch manuell die Adapter Instanz im Script festlegen)

### 0.2.3 (2018-08-17)
* (Matten-Matten)      Admin V3.51

### 0.2.2 (2018-05-12)
* (Matten-Matten)      Button hinzugefügt

### 0.2.1 (2018-03-22)
* (Matten-Matten)      Fehlerbehebung in der HDD Abfrage

### 0.2.0 (2018-03-22)
* (Matten-Matten)      keine Fehlermeldung mehr wenn Box in DeepStandby
* (Matten-Matten)      Erweiterung (PROGRAMM_AFTER ; PROGRAMM_AFTER_INFO ; WEB_IF_VERSION ; NETWORK) hinzugefügt

### 0.1.0 (2018-03-21)
* (Matten-Matten)      installierbar

### 0.0.11 (2018-03-19)
* (Matten-Matten)                  Adapterkonfigurationsmaske (für Admin3) überarbeitet
* (wendy2702 & Matten-Matten)      Admin3

### 0.0.10 (2018-03-19)
* (Matten-Matten)  Umstellungsversuch Admin3

### 0.0.9 (2018-02-07)
* (Matten-Matten)  Kategorie geändert
* (Matten-Matten)  Abfrage Werte sind nur noch lesbar nicht mehr beschreibbar.

### 0.0.8 (2017-11-25)
* (Matten-Matten)  Fehlerbehebung in HDD Abfrage
* (Matten-Matten)  Fehlerbehebung wenn Box Heruntergefahren (nicht erreichbar)
                    jetzt nur noch mit: info	received error: connect ECONNREFUSED 192.168. ...
* (Matten-Matten)  Konfigurations-Maske vereinfacht

### 0.0.7 (2017-09-20)
* (Matten-Matten) add Fehlerbehebung in der MUTED Abfrage

### 0.0.6 (2017-09-19)
* (Matten-Matten) add Erweiterung der Adapterkonfiguration

### 0.0.5 (2017-09-18)
* (Matten-Matten) add grafische Optimierung der Adapterkonfiguration

## License
MIT License

Copyright (c) 2023 iobroker-community-adapters

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