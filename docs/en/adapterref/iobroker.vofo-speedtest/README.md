![Logo](admin/vofo-speedtest.png)
# ioBroker.vofo-speedtest

![Number of Installations (latest)](http://iobroker.live/badges/vofo-speedtest-installed.svg)
![Number of Installations (stable)](http://iobroker.live/badges/vofo-speedtest-stable.svg)
[![NPM version](http://img.shields.io/npm/v/iobroker.vofo-speedtest.svg)](https://www.npmjs.com/package/iobroker.vofo-speedtest)

![Test and Release](https://github.com/peterbaumert/iobroker.vofo-speedtest/workflows/Test%20and%20Release/badge.svg)
[![Downloads](https://img.shields.io/npm/dm/iobroker.vofo-speedtest.svg)](https://www.npmjs.com/package/iobroker.vofo-speedtest)

[![NPM](https://nodei.co/npm/iobroker.vofo-speedtest.png?downloads=true)](https://nodei.co/npm/iobroker.vofo-speedtest/)

**This adapter uses the service [Sentry.io](https://sentry.io) to automatically report exceptions and code errors and new device schemas to me as the developer.** More details see below!


## vofo-speedtest adapter for ioBroker

Speedtest of Vodafone.de

Implements same technique as https://speedtest.vodafone.de

## What is Sentry.io and what is reported to the servers of that company?
Sentry.io is a service for developers to get an overview about errors from their applications. And exactly this is implemented in this adapter.

When the adapter crashes or another Code error happens, this error message that also appears in the ioBroker log is submitted to Sentry.
When you allowed to ioBroker GmbH to collect diagnostic data, then also your installation ID (this is just a unique ID **without** any additional infos about you, email, name or such) is included.
This allows Sentry to group errors and shows how many unique users are affected by such an error. All of this helps me to provide error-free adapters that basically never crash.

## Changelog
<!--
	Placeholder for the next version (at the beginning of the line):
	### **WORK IN PROGRESS**
-->
### 1.0.1 (2023-09-13)
* (bluefox) Updated packages and refactored code

### 1.0.0 (2023-09-13)
* (bluefox) Updated packages and refactored code

### 0.0.13 (2022-06-06)
* some more "already running" fixes

### 0.0.12 (2022-05-28)
* re-release for 0.0.11 because of a missing version in io-package.json

### 0.0.11 (2022-05-27)
* updating dependencies
* adding some timeouts trying to fix "already running with pid"
* fix extracting API key from js-code (thanks Zwer2k) [#112][pr112]

### 0.0.10 (2022-01-07)
* Fix version numbers

### 0.0.9 (2022-01-03)
* Fix to work with new Vodafone Endpoint

### 0.0.8 (2021-07-01)
* Renamed Adapter due to legal reasons
* Fixed some dependencies

### 0.0.7 (2021-05-21)
* Fixed some vulnerabilities in dev-dependencies
* Fixed js-controller 3* issues
* Fixed node 16 compatability

### 0.0.6 (2021-01-21)
* Added Sentry.io Integration

### 0.0.5 (2020-05-26)
* Added ping results
* Added calculated values by actual raw data

### 0.0.4 (2020-04-30)
* Changed Adapter start type to scheduled (re-installation might be needed)
* Bug fixes and feedback implementation

### 0.0.3 (2020-04-24)
* Implemented feedback from Forum and GitHub issue

### 0.0.2 (2020-04-19)
* Added actual settings in Admin interface
* first version ready for testing

### 0.0.1 (2020-04-18)
* (Peter Baumert) initial release

## Disclaimer
Vodafone is a trademark of Vodafone GmbH. I am in no way endorsed by or affiliated with Vodafone GmbH, or any associated subsidiaries, logos or trademarks

## License
MIT License

Copyright (c) 2020-2023 Peter Baumert

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