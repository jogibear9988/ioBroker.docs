![Logo](admin/telegram-menu.png)

# ioBroker.telegram-menu

[![NPM version](https://img.shields.io/npm/v/iobroker.telegram-menu.svg)](https://www.npmjs.com/package/iobroker.telegram-menu)
[![Downloads](https://img.shields.io/npm/dm/iobroker.telegram-menu.svg)](https://www.npmjs.com/package/iobroker.telegram-menu)
![Number of Installations](https://iobroker.live/badges/telegram-menu-installed.svg)
![Current version in stable repository](https://iobroker.live/badges/telegram-menu-stable.svg)

[![NPM](https://nodei.co/npm/iobroker.telegram-menu.png?downloads=true)](https://nodei.co/npm/iobroker.telegram-menu/)

**Tests:** ![Test and Release](https://github.com/MiRo1310/ioBroker.telegram-menu/workflows/Test%20and%20Release/badge.svg)

## ioBroker telegram-menu adapter

Easily create Telegram Menus

You can create different groups with separate menus, and then assign users to them.

**If you like it, please consider a donation:**

[![paypal](https://www.paypalobjects.com/en_US/DK/i/btn/btn_donateCC_LG.gif)](https://www.paypal.com/donate/?hosted_button_id=7QGL5CXJCUSCE)

## Documentation

[🇺🇸 Documentation](./docs/en/README.md)

[🇩🇪 Dokumentation](./docs/de/README.md)

## Changelog

<!--
	Placeholder for the next version (at the beginning of the line):
	### **WORK IN PROGRESS**
-->

### **WORK IN PROGRESS**

-   Convert milliseconds value to a local time specification
-   setstate and get result of another state with text adjusted

### 0.7.1 (2023-10-02)

-   bugfix, Error read UserListTypeError: Cannot read properties of undefined

### 0.7.0 (2023-10-01)

-   #53 feature: sendPicture von server-path
-   #52 icons are missing, copy data
-   #51 by creating a new Menu, the Users are not shown

### 0.6.10 (2023-09-23)

-   bug fix

### 0.6.9 (2023-09-23)

-   Rearranging listed actions #49
-   when calling up the submenu, Text was send no entry found, fixed
-   bug switch menu, fixed
-   set a state, and receive the change of another state

### 0.6.8 (2023-09-16)

-   chatId in UI
-   trigger is not displayed when editing, fixed

### 0.6.7 (2023-09-05)

-   fixed, send menu with error

### 0.6.6 (2023-09-03)

-   add info-big.png

### 0.6.5 (2023-09-01)

-   get user by chatID and send back to this chatID

### 0.6.4 (2023-08-20)

-   Trigger check, used triggers are no longer available in action, in nav it is visualized that the trigger is already in use

### 0.6.3 (2023-08-17)

-   user check, least one user must be checked

### 0.6.2 (2023-08-14)

-   Active Menu Output fixed
-   change instance, user will be load from new instance

### 0.6.1 (2023-08-13)

-   bug fixed style

### 0.6.0 (2023-08-13)

-   checkbox for Telegram Users
-   styling
-   small fixes
-   Add Row Button in Nav for every Row
-   More Groups with the same User
-   Trigger generates without saving

### 0.5.1 (2023-08-05)

-   sent to the wrong instance, fixed

### 0.5.0 (2023-08-05)

-   trigger avoid duplicate entries and sort alphabetical
-   adapter stops responding after some time, fixed #42
-   generate Trigger in Action, fixed
-   math value for getstate
-   settings instance #41, menus, fixed
-   no spellcheck for input fields
-   menu go back to last Sides

### 0.4.2 (2023-07-30)

-   menu switch ersetzt menu yes-no, on-off, it is possible to customize text and value with this menu

### 0.4.1 (2023-07-30)

-   Return text for submenus adjusted

### 0.4.0 (2023-07-28)

-   change output value for getState
-   checkbox to disbale Text No Entry found in the settings #34
-   submenu
-   **changed!!!**, states are always set with ack false
-   adapter does not restart when telegram restarts #35

### 0.3.0 (2023-07-02)

-   add ack Flag
-   Copy-Button to copy User-elements to activ User

### 0.2.0 (2023-05-28)

-   rename button
-   create groups with users

### 0.1.1 (2023-05-18)

-   shift rows
-   small fixes
-   Darkmode fixed
-   option, return text without value
-   get all Values of functions

### 0.1.0 (2023-05-07)

-   Fixes
-   Style
-   Confirmation, that the value has been set
-   Second User Menu fixed

### 0.0.8 (2023-05-01)

-   Send Grafana Diagrams

### 0.0.7 (2023-04-23)

-   Bugs fixed
-   Translate

### 0.0.6 (2023-04-18)

-   Fixed SetState and GetState
-   Translate

### 0.0.2 (2023-04-16)

-   (MiRo1310) initial release

## License

MIT License

Copyright (c) 2023 MiRo1310 <michael.roling@gmx.de>

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
