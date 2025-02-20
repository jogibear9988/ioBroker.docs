---
BADGE-NPM version: https://img.shields.io/npm/v/iobroker.octoprint?style=flat-square
BADGE-Downloads: https://img.shields.io/npm/dm/iobroker.octoprint?label=npm%20downloads&style=flat-square
BADGE-Snyk Vulnerabilities for npm package: https://img.shields.io/snyk/vulnerabilities/npm/iobroker.octoprint?label=npm%20vulnerabilities&style=flat-square
BADGE-node-lts: https://img.shields.io/node/v-lts/iobroker.octoprint?style=flat-square
BADGE-Libraries.io dependency status for latest release: https://img.shields.io/librariesio/release/npm/iobroker.octoprint?label=npm%20dependencies&style=flat-square
BADGE-GitHub: https://img.shields.io/github/license/klein0r/iobroker.octoprint?style=flat-square
BADGE-GitHub repo size: https://img.shields.io/github/repo-size/klein0r/iobroker.octoprint?logo=github&style=flat-square
BADGE-GitHub commit activity: https://img.shields.io/github/commit-activity/m/klein0r/iobroker.octoprint?logo=github&style=flat-square
BADGE-GitHub last commit: https://img.shields.io/github/last-commit/klein0r/iobroker.octoprint?logo=github&style=flat-square
BADGE-GitHub issues: https://img.shields.io/github/issues/klein0r/iobroker.octoprint?logo=github&style=flat-square
BADGE-GitHub Workflow Status: https://img.shields.io/github/actions/workflow/status/klein0r/iobroker.octoprint/test-and-release.yml?branch=master&logo=github&style=flat-square
BADGE-Snyk Vulnerabilities for GitHub Repo: https://img.shields.io/snyk/vulnerabilities/github/klein0r/iobroker.octoprint?label=repo%20vulnerabilities&logo=github&style=flat-square
BADGE-Beta: https://img.shields.io/npm/v/iobroker.octoprint.svg?color=red&label=beta
BADGE-Stable: http://iobroker.live/badges/octoprint-stable.svg
BADGE-Installed: http://iobroker.live/badges/octoprint-installed.svg
translatedFrom: en
translatedWarning: 如果您想编辑此文档，请删除“translatedFrom”字段，否则此文档将再次自动翻译
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/zh-cn/adapterref/iobroker.octoprint/README.md
title: ioBroker.octoprint
hash: tYYCO+GmPMlasV2q2VC/77HRu5mmyVdNw97St4V4mw0=
---
![标识](../../../en/admin/octoprint.png)

#ioBroker.octoprint
**使用 [章鱼印](https://github.com/OctoPrint/OctoPrint/releases) 1.9.0 测试**

＃＃ 特征
＃＃＃ 信息
- 获取版本信息
- 获取打印机信息（当``可操作``）
- 获取当前打印作业信息（当``打印``）
- 获取文件列表信息（不打印时）

＃＃＃ 工具
- 设置工具温度（当``操作``）
- 设置床温（当``运行``）
- 挤出/缩回（当“可操作”时）

### 命令
- 打印机：连接、断开连接和回家
- 工作：开始、暂停、恢复、取消、重新开始
- SD 卡：初始化、刷新、释放
- 自定义打印机命令
- 系统命令
- 点动 X、Y 和 Z 轴
- 选择一个文件或打印它

### 支持的插件
- [显示层进度](https://github.com/OllisGit/OctoPrint-DisplayLayerProgress) - 测试版本 1.28.0（需要 **适配器版本 2.1.0** 或更高版本）
- [切片器缩略图](https://github.com/jneilliii/OctoPrint-PrusaSlicerThumbnails) - 使用版本 1.0.0 测试（需要 **适配器版本 2.2.0** 或更高版本）

＃＃ 重要的！
不要用这样的代码重启你的 OctoPrint 实例（或任何其他实例）：

```javascript
var obj = getObject('system.adapter.octoprint.0');
obj.common.enabled = false;
setObject('system.adapter.octoprint.0', obj);
```

由于 `API key` 自 1.1.0 版以来是受保护的属性，这将删除已配置的 API 密钥。原因是，`getObject` 不返回受保护的信息（因此 api 密钥不包含在返回的对象中）。当您保存对象时，您将保存一个没有密钥的对象。

请使用状态 `system.adapter.octoprint.0.alive` 停止/启动实例。

## Changelog

<!--
  Placeholder for the next version (at the beginning of the line):
  ### **WORK IN PROGRESS**
-->
### 5.0.1 (2023-05-30)

* (klein0r) Allow self-signed certificates

### 5.0.0 (2023-05-24)

Tested with OctoPrint 1.9.0

* (klein0r) Removed binary states (deprecated)
* (klein0r) Allow self-signed certificates
* (klein0r) Added Ukrainian language

### 4.1.0 (2022-12-14)

Tested with OctoPrint 1.8.6

* (klein0r) Dropped Admin 5 support
* (klein0r) Added Ukrainian language

### 4.0.1 (2022-10-14)

Tested with OctoPrint 1.8.4

* (klein0r) Just download every thumbnail once (requires plugin Slicer Thumbnails)

### 4.0.0 (2022-05-19)

NodeJS 14.x is required (NodeJS 12.x is EOL)

Tested with OctoPrint 1.8.0

* (klein0r) Added last and average layer duration (requires plugin Display Layer Progress)
* (klein0r) Moved thumbnail information of files to new structure **(BREAKING CHANGE - CHECK YOUR SCRIPTS AND VIS)**
* (klein0r) Improved handling of thumbnails and states for plugins

## License

The MIT License (MIT)

Copyright (c) 2023 Matthias Kleine <info@haus-automatisierung.com>

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