---
local: true
translatedFrom: en
translatedWarning: 如果您想编辑此文档，请删除“translatedFrom”字段，否则此文档将再次自动翻译
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/zh-cn/adapterref/iobroker.tr-064/README.md
title: ioBroker.tr-064
hash: rN4KkHkTgQi739/0GZDQZ274L23nvqhd+4OxJHA44Ww=
---
![标识](../../../en/adapterref/iobroker.tr-064/media/tr-064.png)

# IoBroker.tr-064
###信息
该适配器从 AVM Fritz!Box 读取主要信息，例如呼叫列表或应答机上的消息数量。
基于此[AVM 文档](https://avm.de/service/schnittstellen/)

### 简单的状态和函数
- 打开/关闭 2.4GHz 和 5GHz 的 wifi，
- 打开/关闭访客 wifi，
- 重新启动 Fritz!Box，
- 启动 WPS 进程，
- 重新连接互联网
- 外部IP地址

### 响铃（拨号）
- 当使用内部号码（如 **610）时，响铃状态将让该内部电话响铃。

例如：**610[,超时]

- 使用外部号码时，振铃状态会将您连接到外部号码。

当被叫电话被拿起时，FritzBox 将呼叫外部号码并且您的默认电话会响铃。
可以在 FritsBox 中配置默认电话：Telefonie/Anrufe/[Tab]Wahlhilfe/Wählhilfe verwenden

### ToPauseState
- 值：响铃、连接、结束
- 可用于在来电（响铃）或拿起电话（连接）时暂停视频播放器。
- 可以对最终值进行简历。

＃＃＃ 在场
您可以配置要收听的设备列表。
可由mDNS触发。使用 MDNS 时，无需轮询，速度更快

### AB - Anrufbeanworter（答录机）
可以开/关。
可以将状态 cbIndex 设置为应答机的地址 #。

### 通话监听
callmonitor 将为每个呼入和呼出创建实时状态。
如果启用电话簿（默认），号码将被解析为姓名。还有一个状态表明电话正在响铃。

＃＃＃ 电话簿
- 如果启用，电话簿将用于获取来电者电话号码的名称。
- 此外，还有三种状态可以解析数字或名称。如果可用，您还将获得联系人的图像 URL。

  例如：如果您设置状态 phonebook.number 所有 3 个状态，名称、号码和图像将设置为找到的联系人。注意，按名称搜索将首先比较完整名称，如果没有找到，则使用部分名称。

### 通话清单
输出格式：

- json
- html

通话清单是：

- 所有通话
- 未接来电
- 呼入电话
- 外拨电话

呼叫计数：呼叫计数可设置为 0。下一次呼叫将增加 1。

html输出可以通过模板配置

### 命令和命令结果状态
使用命令状态，您可以从此 [文件](https://avm.de/service/schnittstellen/) 调用每个 tr-064 命令。
例如

```
command = {
    "service": "urn:dslforum-org:service:WLANConfiguration:1",
    "action": "X_AVM-DE_SetWPSConfig",
    "params": {
        "NewX_AVM-DE_WPSMode": "pbc",
        "NewX_AVM-DE_WPSClientPIN": ""
    }
};
```

命令状态应设置为上述行的 JSON。所以 { ... } （没有 command = 和换行符）调用的回调将设置 commandResult 状态。

### 开启通话监听
要使用呼叫监控功能，必须首先在 AVM Fritz!Box 中启用它。
要启用呼叫监控拨号```#96*5*```，TCP/IP 端口 1012 将被打开。关闭端口拨号```#96*4*```。

### 预发布版本
在 npm 上可以使用带有 dev 标签的预发布版本。
您可以使用以下命令从 ioBroker 根目录安装它们：

```
npm install iobroker.tr-064@dev
iobroker upload tr-064
```

## Changelog
### 4.2.18 (2023-01-04)
* (Apollon77) Prepare for future js-controller verisons

### 4.2.17 (2022-09-16)
* (simatec/Apollon77) Prevent duplication of entries in configuration
* (Apollon77) Make sure active status of devices in jsonDeviceList is correct

### 4.2.16 (2022-03-21)
* (Apollon77) Fix info logs on callee/caller
* (Apollon77) Add special handling for potential broken external image links in phonebook
* (Apollon77) Prevent some crash cases reported by Sentry

### 4.2.15 (2021-12-08)
* (bluefox) fix crash case (Sentry IOBROKER-TR-064-35)

### 4.2.14 (2021-07-21)
* (Apollon77) Further optimizations for js-controller 3.3

### 4.2.13 (2021-07-12)
* (Apollon77) Optimize for js-controller 3.3 and prevent warnings (you pot. need to delete datapoints if you still see errors, they will be recreated)

### 4.2.12 (2021-04-16)
* (Apollon77) prevent html template for call lists to be overwritten by default one
* (Apollon77) fix crash case (Sentry IOBROKER-TR-064-2M)

### 4.2.11 (2021-03-12)
* (Apollon77) fix id-reset detection for single calls

### 4.2.10 (2021-03-11)
* (Apollon77) better handle caller id resets by reboots/FW updates to also update list specific counter and log when this happened

### 4.2.9 (2021-03-10)
* (Apollon77) try to better handle calllist resets on FW updates
* (Apollon77) Make sure jsonDeviceList do not get deleted on start
* (Apollon77) Better handle not initialized calllist templates

### 4.2.8 (2021-03-09)
* (Apollon77) Optimize customized HTML templates if state is empty

### 4.2.7 (2021-03-08)
* (Apollon77) Allow customized HTML templates again

### 4.2.6 (2021-02-18)
* (Apollon77) Fix crash case (IOBROKER-TR-064-20)
* (Apollon77) Get calllists working again

### 4.2.4 (2021-02-02)
* (Apollon77) Prevent crash case (Sentry IOBROKER-TR-064-1T)

### 4.2.3 (2021-01-16)
* (Apollon77) Crash case prevented (Sentry IOBROKER-TR-064-1N)

### 4.2.2 (2020-12-25)
* (Apollon77) Crash case prevented (Sentry IOBROKER-TR-064-1K)

### 4.2.1 (2020-11-13)
* (Apollon77) try to fix pot. not working disabling commands

### 4.2.0 (2020-11-09)
* (Apollon77) Crash case prevented (Sentry IOBROKER-TR-064-15, IOBROKER-TR-064-16)
* (Apollon77) Try to solve error 500 problem with offline devices
* (SliX185) Add IPv6 states
* (foxriver76) optimizations
* (Apollon77) Fix initialization if ip/host

### 4.1.0 (2020-09-17)
* (Apollon77) Fix crash case (Sentry IOBROKER-TR-064-14)
* (bazidibavaria) added tablesort to device search
* (bazidibavaria) added Fritzbox link to admin

### 4.0.13 (2020-08-17)
* (Apollon77) Crash prevented (Sentry IOBROKER-TR-064-10)

### 4.0.12 (2020-08-06)
* (Apollon77) Crash prevented (Sentry IOBROKER-TR-064-Y)

### 4.0.11 (2020-07-26)
* (Apollon77) Crash prevented (Sentry IOBROKER-TR-064-W)

### 4.0.9 (2020-07-01)
* (Apollon77) handle cases correctly when no hosts are existing on device (Sentry IOBROKER-TR-064-R)

### 4.0.8 (2020-06-20)
* (Apollon77) Make sure states are only subscribed if initialization is done (Sentry IOBROKER-TR-064-J)

### 4.0.7 (2020-06-09)
* (Apollon77) Fix Admin UI to allow setting poll Interval correctly again

### 4.0.4 (2020-06-05)
* (Apollon77) Make sure adapter do not crash of no calls were returned (Sentry IOBROKER-TR-064-D)
* (Apollon77) Make sure adapter do not crash when invalid parameter are provided (Sentry IOBROKER-TR-064-B)
* (Apollon77) https is not supported right now (Sentry IOBROKER-TR-064-E)

### 4.0.3 (2020-05-11)
* (Apollon77) Make sure adapter do not crash of no calls were returned (Sentry IOBROKER-TR-064-7)
* (Apollon77) Make sure adapter do not crash when providing a non string to "ring" state (Sentry IOBROKER-TR-064-8)

### 4.0.1 (2020-04-23)
* (Apollon77) handle case where no Phone deflections are available (Sentry IOBROKER-TR-064-1/2)

### 4.0.0 (2020-04-12)
* (Apollon77) update dependencies, use auto decrypt features with js-controller 3.0
* (foxriver76) make callmonitor compatible with js-controller 3.0

### 3.1.4 (2020-01-26)
* (Apollon77) fix error and check some other code check comments
* (Apollon77) Add proper meta data for buttons

### 3.1.1 (2020-01-25)
* (bluefox) Configuration dialog was improved
* (bluefox) Soef library was removed

### 3.0.0 (2020-01-24)
* (Apollon77) Switch Name back to tr064 because ewe got it from npmjs
* (maeb3) Enhance call handling and fix wrong data for currently active calls 
* (Apollon77) Remove unused state phonebook.ringing

### 2.0.3 (2019-12-17)
* (Jey Cee) fix delete last device from list

### 2.0.2 (2019-12-16)
* __requires js-controller v2__
* (foxriver76) no longer use adapter.objects
* (Apollon77) several fixes, Call lists working again, Phonebook fixed and many more

### 1.1.0 (2019-11-10)
* (jey cee) added Admin v3 support

### 1.0.0 (2019-04-01)
* (ldittmar) first version for the community

## License
The MIT License (MIT)

Copyright (c) 2015-2023 soef <soef@gmx.net>, ioBroker-Community-Developers

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