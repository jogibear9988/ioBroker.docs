<img src="admin/bambulab.png" alt="Logo" width="200"/>

# ioBroker.bambulab

[![NPM version](https://img.shields.io/npm/v/iobroker.bambulab.svg)](https://www.npmjs.com/package/iobroker.bambulab)
[![Downloads](https://img.shields.io/npm/dm/iobroker.bambulab.svg)](https://www.npmjs.com/package/iobroker.bambulab)
![Number of Installations](https://iobroker.live/badges/bambulab-installed.svg)
![Current version in stable repository](https://iobroker.live/badges/bambulab-stable.svg)

[![NPM](https://nodei.co/npm/iobroker.bambulab.png?downloads=true)](https://nodei.co/npm/iobroker.bambulab/)

**Tests:** ![Test and Release](https://github.com/DrozmotiX/ioBroker.bambulab/workflows/Test%20and%20Release/badge.svg)

## Bambulab 3D-Printing adapter for ioBroker

## Getting started

With credits to [kmxak](https://forum.iobroker.net/user/kmxak), [djalexz](https://forum.iobroker.net/user/djalexz), all other involved and inspired by [this forum thread](https://forum.iobroker.net/topic/61585/bambu-lab-3d-drucker-mqtt-integration)
this adapter integrates Bambulab 3D-Printers into ioBroker.

Please provide your Printer IP-Address, API token and serial number in adapter settings, these are required for a local connection (no cloud involved) to your printer.
These credentials are stored locally and not shared to third parties.

You must select your Printer model, only the X1 allows pushing of messages, P1x series needs to request by interval setting (default every 5 seconds)

## Supported models
| Printer-Model | Status                  |
|---------------|-------------------------|
| P1p           | :white_check_mark:      |
| P1s           | :question:needs testing |
| X1            | :white_check_mark:      |
| AMS           | :white_check_mark:      |

## Supported commands
| Command            | X1C                 | X1                  | P1P                      | P1S                      |
|--------------------|---------------------|---------------------|--------------------------|--------------------------|
| Custom g-code      | :white_check_mark:  | :white_check_mark:  | :white_check_mark:       | :question: needs testing |
| Pause              | :white_check_mark:  | :white_check_mark:  | :white_check_mark:       | :question: needs testing |
| Resume             | :white_check_mark:  | :white_check_mark:  | :white_check_mark:       | :question: needs testing |
| Stop               | :white_check_mark:  | :white_check_mark:  | :white_check_mark:       | :question: needs testing |
| Fan-Aux            | :white_check_mark:  | :white_check_mark:  | :question: needs testing | :question: needs testing |
| Fan-Chamber        | :white_check_mark:  | :white_check_mark:  | :question: needs testing | :question: needs testing |
| Fan-ToolHead       | :white_check_mark:  | :white_check_mark:  | :question: needs testing | :question: needs testing |
| Light-Chamber      | :white_check_mark:  | :white_check_mark:  | :question: needs testing | :question: needs testing |
| Light-Nozzle       | :white_check_mark:  | :white_check_mark:  | :question: needs testing | :question: needs testing |
| Light-Logo         | :white_check_mark:  | :white_check_mark:  | :question: needs testing | :question: needs testing |
| Temperature-Bed    | :white_check_mark:  | :white_check_mark:  | :white_check_mark:       | :question: needs testing |
| Temperature-Nozzle | :white_check_mark:  | :white_check_mark:  | :white_check_mark:       | :question: needs testing |
| Speed Level        | :white_check_mark:  | :white_check_mark:  | :white_check_mark:       | :question: needs testing |

## To-Do
[ ] Implement more commands, please provide feedback what we need :exclamation:  
[ ] Restructure/complete current control states in control folder
[ ] Optimize state attributes definitions  
[ ] Test printer series P1S  

## Support me
If you like my work, please consider a personal donation  
(this is a personal Donate link for DutchmanNL, no relation to the ioBroker Project !)  
[![Donate](https://raw.githubusercontent.com/DrozmotiX/ioBroker.sourceanalytix/master/admin/button.png)](http://paypal.me/DutchmanNL)

## What is Sentry.io and what is reported to the servers of that company?
Sentry.io is a service for developers to get an overview about errors from their applications. And exactly this is implemented in this adapter.

When the adapter crashes or any other Code error happens, this error message that also appears in the ioBroker log is submitted to Sentry. When you allowed iobroker GmbH to collect diagnostic data then also your installation ID (this is just a unique ID **without** any additional infos about you, email, name or such) is included. This allows Sentry to group errors and show how many unique users are affected by such an error. All of this helps me to provide error free adapters that basically never crashs.


## Changelog
<!--
	Placeholder for the next version (at the beginning of the line):
	### **WORK IN PROGRESS**
-->
### 0.1.5 (2023-07-29) - HMS error codes Human readable, new functionalities added
#### Several state locations have been changed, advise to completely remove adapter & reinstall to upgrade
* (DutchmanNL) State for human readable start time added
* (DutchmanNL) Speed level control implemented solves #10
* (DutchmanNL) Capability to control all fans implemented
* (DutchmanNL) Control bed & Nozzle temperature implemented
* (DutchmanNL) HMS error status indicator states implemented
* (DutchmanNL) Translations of HMS error codes implemented solves #9
* (DutchmanNL) Correct definitions for all temperature related states
* (DutchmanNL) Control LED for tooling head Logo and calibration unit

### 0.1.4 (2023-07-28) - Support P1-series
* (DutchmanNL) Configuration page in admin updated
* (DutchmanNL) Information messages regarding incorrect type of bed-temperatures solved
* (DutchmanNL) Implemented P1-X printer series, polling interval required for this model (only X1 handles data push)

### 0.1.3 (2023-07-27) - Add new control options
* (DutchmanNL) add control for chamber fan, tooling head light and allow custom g-code

### 0.1.1 - Minor improvements
* (DutchmanNL) Translations added
* (DutchmanNL) Debug logging improved
* (DutchmanNL) Minor code improvements
* (DutchmanNL) Control states implemented
* (DutchmanNL) Test & release workflows updated
* (DutchmanNL) Encryption of token and device serial improved

### 0.1.0 initial release
* (DutchmanNL) initial release
* During startup adapter throws warnings, these can be ignored and will be solved in =< 0.5.0
* Control start/stop/resume and light available in >= 0.1.1

## License
MIT License

Copyright (c) 2023 DutchmanNL <oss@drozmotix.eu>

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