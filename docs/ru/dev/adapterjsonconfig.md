---
translatedFrom: en
translatedWarning: Если вы хотите отредактировать этот документ, удалите поле «translationFrom», в противном случае этот документ будет снова автоматически переведен
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/ru/dev/adapterjsonconfig.md
title: Конфигурация JSON ioBroker
hash: LexY9A0at19A+Ujovu4Yx+sKBDambx+4gyh2wEa98vM=
---
# Конфигурация JSON ioBroker
Администратор (начиная с версии 6) поддерживает конфигурацию JSON для адаптеров.
Можно определить конфигурацию в файле JSON, а затем использовать ее в администраторе.

Пример файла `jsonConfig.json` с несколькими вкладками можно найти здесь: https://github.com/ioBroker/ioBroker.admin/blob/master/admin/jsonConfig.json5, а пример с одной панелью здесь: https:/ /github.com/ioBroker/ioBroker.dwd/blob/master/admin/jsonConfig.json

Вы можете определить настройки в формате JSON или JSON5. JSON5 более удобен для чтения и поддерживает комментарии.

Кроме того, для файла JSON необходимо определить в `io-package.json` части `common`:

```json
...
"adminUI": {
  "config": "json"
}
...
```

сказать, что адаптер поддерживает конфигурацию JSON.

Вы сможете увидеть почти все компоненты в действии, если протестируете этот адаптер: https://github.com/mcm1957/ioBroker.jsonconfig-demo.
Вы можете установить его через значок GitHub в администраторе, введя `iobroker.jsonconfig-demo` на вкладке npm.

Все метки, тексты, справочные тексты могут быть многоязычными или просто строками.

*Если имя атрибута начинается с «_», оно не будет сохранено в объекте.*

## Возможные типы управления
Возможные типы:

- `tabs` - Вкладки с элементами
  - `items` - Объект с панелями `{"tab1": {}, "tab2": {}...}`
  - `iconPosition` — `bottom`, `end`, `start` или `top`. Только для панелей с атрибутом «icon». По умолчанию: `старт`

- `panel` - Вкладка с предметами
  - `icon` - вкладка может иметь значок (base64, например `data:image/svg+xml;base64,...`) или изображения `jpg/png` (оканчивается на `.png`)
  - `label` - Метка вкладки
  - `items` - Объект `{"attr1": {}, "attr2": {}}...`
  - `складной` - возможно только как часть вкладок [jsonConfig.json](..%2F..%2F..%2F..%2F..%2FioBroker.ring%2Fadmin%2FjsonConfig.json)
  - `color` - цвет сворачиваемого заголовка `primary` или `вторичный` или ничего.

- `text` - текстовый компонент
  - `maxLength` - максимальная длина текста в поле
  - `readOnly` - поле только для чтения
  - `trim` - по умолчанию true. Установите для этого атрибута значение false, если обрезка не требуется.
  - `minRows` — по умолчанию установлено значение 1. Установите для этого атрибута значение `2` или более, если вы хотите иметь текстовое поле с более чем одной строкой.
  - `maxRows` - максимальное количество строк текстовой области. Используется только если `minRows` > 1.

- `число`
  - `min` - минимальное значение
  - `max` - максимальное значение
  - `шаг` - шаг

- `color` - выбор цвета

- `checkbox` - показать флажок

- `slider` - показать слайдер (только Admin6)
  - `мин` - (по умолчанию 0)
  - `макс` - (по умолчанию 100)
  - `шаг` - (по умолчанию `(макс - мин) / 100`)
  - `unit` - Единица слайдера

- `ip` - адрес привязки
  - `listenOnAllPorts` - добавьте 0.0.0.0 к опции
  - `onlyIp4` - показывать только адреса IP4
  - `onlyIp6` - показывать только адреса IP6
  - `noInternal` - не показывать внутренние IP-адреса

- `user` — выберите пользователя из system.user. (с цветом и значком)
  - `short` - нет system.user.

- `room` - выбрать комнату из `enum.room` (с цветом и значком) - (только Admin6)
  - `short` - нет `enum.rooms`.
  - `allowDeactivate` - разрешить пустовать комнату

- `func` — выберите функцию из `enum.func` (с цветом и значком) - (только Admin6)
  - `short` - нет `enum.func.`
  - `allowDeactivate` - разрешить пустую функциональность

- `выбрать`
  - `options` - `[{label: {en: "option 1"}, value: 1}, ...]` или

                `[{"items": [{"label": "Val1", "value": 1}, {"label": "Val2", value: "2}], "name": "group1"}, {"items": [{"label": "Val3", "value": 3}, {"label": "Val4", value: "4}], "name": "group2"}, {"label": "Val5", "value": 5}]`

- `автозаполнение`
  - `options` - `["value1", "value2", ...]` или `[{"value": "value", "label": "Value1"}, "value2", ...]`
  - `freeSolo` — установите для `freeSolo` значение `true`, чтобы текстовое поле могло содержать любое произвольное значение.

- `image` - сохраняет изображение как файл объекта `adapter.X` или как base64 в атрибуте
  - `filename` - имя файла является именем структуры. В приведенном ниже примере `login-bg.png` — это имя файла для `writeFile("myAdapter.INSTANCE", "login-bg.png")`
  - `accept` - атрибут принятия HTML, например `image/*,.pdf`
  - `maxSize` - максимальный размер загружаемого файла
  - `base64` - если true, изображение будет сохранено как URL-адрес данных в атрибуте, иначе как двоичный файл в хранилище файлов.
  - `!maxWidth`
  - `!maxHeight`
  - `!crop` - если true, разрешить пользователю обрезать изображение
  - `!square` - ширина должна быть равна высоте, или обрезка должна допускать только квадратную форму.

```
  "login-bg.png": {
       "type": "image",
       "accept": "image/png",
       "label": {
         "en": "Upload image"
       },
       "crop": true
     },
     "picture": {
       "type": "image",
       "base64": true,
       "accept": "image/*",
       "label": {
         "en": "Upload image"
       },
       "crop": true
     }
  }
```

- `objectId` — идентификатор объекта: показать его с именем, цветом и значком.
    - `types` - Желаемый тип: `channel`, `device`, ... (по умолчанию имеет только `state`). Это единственное число, потому что `type` уже занят.
    - `root` - [необязательно] Показать только этот корневой объект и его дочерние элементы
    - `customFilter` - [необязательно] Невозможно использовать вместе с настройками `type`. Примеры

`{common: {custom: true}}` - показывать только объекты с некоторыми пользовательскими настройками `{common: {custom: 'sql.0'}}` - показывать только объекты с пользовательскими настройками sql.0 (только конкретного экземпляра) `{common: {custom: '_dataSources'}}` - показывать только объекты адаптеров §§SSSSSS_5§ § или `sql` или `history` `{common: {custom: 'adapterName.'}}` — показывать только объекты пользовательских настроек конкретного адаптера (все экземпляры) `{type: 'channel'}` — показывать только каналы `{type: ['channel', 'device']}` — показывать только каналы и устройства `{common: {type: 'number'}` - показывать только состояния типа 'number `{common: {type: ['number', 'string']}` - показывать только состояния типа 'number и string `{common: {role: 'switch']}` - показывать только состояния с ролями, начинающимися с коммутатора `{common: {role: ['switch', 'button]}` - показывать только состояния с ролями, начинающимися с `switch` и `button`

- `password` - поле пароля

Этот тип поля влияет только на пользовательский интерфейс.
Пароли и другие конфиденциальные данные следует хранить в зашифрованном виде! Для этого ключ должен быть указан в io-package.json в разделе [роднойЗашифрованный](https://github.com/ioBroker/ioBroker.js-controller#automatically-encryptdecrypt-configuration-fields).
Кроме того, вы можете защитить это свойство от передачи другим адаптерам, кроме `admin` и `cloud`, добавив его в `protectedNative` в файле `io-package.json`.

    - `repeat` - повторный пароль необходимо сравнить с паролем
    - `visible` — true, если разрешен просмотр пароля путем переключения кнопки просмотра.
    - `maxLength` - максимальная длина текста в поле

- `экземпляр`
    - `adapter` - имя адаптера. Со специальным именем `_dataSources` вы можете получить все адаптеры с флагом `common.getHistory`.
    - `allowDeactivate` - если правда. Показана дополнительная опция «деактивировать».
    - `long` — значение будет выглядеть как `system.adapter.ADAPTER.0`, а не `ADAPTER.0`
    - `short` — значение будет выглядеть как `0`, а не `ADAPTER.0`
    - `all` - Добавить к опциям опцию "all" со значением `*`

- `фишки` - пользователь может ввести слово, и оно будет добавлено (см. облако => сервисы => Белый список). Выходные данные представляют собой массив, если не определен разделитель.
    - `разделитель` - если он определен, то параметр будет сохранен как строка с разделителем, а не как массив. Например, используя `delimiter=;` вы получите `a;b;c` вместо `['a', 'b', 'c']`

- `alive` - просто указание, жив ли экземпляр, и его можно использовать в "скрытом" и "отключенном" состоянии (не будет сохранено в конфигурации)

  Просто текст: экземпляр запущен, экземпляр не запущен.

    - `instance` - проверить, жив ли экземпляр. Если не определено, будет использоваться текущий экземпляр. Вы можете использовать в тексте шаблон `${data.number}`.
    - `textAlive` — текст по умолчанию: `Экземпляр %s активен`, где %s будет заменен на `ADAPTER.0`.
    - `textNotAlive` — текст по умолчанию: `Экземпляр %s неактивен`, где %s будет заменен на `ADAPTER.0`.

- `pattern` - поле только для чтения с шаблоном типа "https://${data.ip}:${data.port}" (не будет сохранено в конфигурации)

  Ввод текста с флагом «только для чтения», отображающий шаблон.

    - `copyToClipboard` - если true - показать кнопку
    - `шаблон` - мой узор

- `sendto` — кнопка отправки запроса в экземпляр (https://github.com/iobroker-community-adapters/ioBroker.email/blob/master/admin/index_m.html#L128)
    - `команда` - (по умолчанию `отправить`)
    - `jsonData` - строка - `"{\"subject1\": \"${data.subject}\", \"options1\": {\"host\": \"${data.host}\" }}"`. Вы можете использовать специальные переменные `data._origin` и `data._originIp` для отправки экземпляра URL-адреса вызывающей стороны, например `http://127.0.0.1:8081/admin`.
    - `данные` - объект - `{"subject1": 1, "data": "static"}`. Вы можете указать jsonData или data, но не то и другое.
    - `result` - `{result1: {en: 'A'}, result2: {en: 'B'}}`
    - `error` - `{error1: {en: 'E'}, error2: {en: 'E2'}}`
    - `вариант` - `содержится`, `обрисовано` или ничего
    - `openUrl` - если true - открыть URL-адрес в новой вкладке, если ответ содержит атрибут `openUrl`, например `{"openUrl": "http://1.2.3.4:80/aaa", "window": "_blank" , "saveConfig": true}`. Если `saveConfig` имеет значение true, пользователю будет предложено сохранить конфигурацию.
    - `reloadBrowser` - если true - перезагрузить текущее окно браузера, если ответ содержит атрибут `reloadBrowser`, например `{"reloadBrowser": true}`.
    - `window` - если `openUrl` истинно, это имя нового окна. Может быть перезаписано, если ответ содержит атрибут Window.

      `this.props.socket.sendTo(adapterName.instance, command || 'send', data, result => {});`

    - `icon` - если значок должен отображаться: `auth`, `send`, `web`, `warning`, `error`, `info`, `search`. Вы можете использовать значки `base64` (например, `data:image/svg+xml;base64,...`) или изображения `jpg/png` (оканчиваются на `.png`). (Если вам нужно больше значков, запросите через Issue)
    - `useNative` - если адаптер возвращает результат с атрибутом `native`, он будет использован для настройки. Если `saveConfig` имеет значение true, пользователю будет предложено сохранить конфигурацию.
    - `showProcess` - Показывать счетчик во время выполнения запроса.
    - `timeout` - таймаут запроса в мс. По умолчанию: нет.

- `setState` - кнопка установки состояния экземпляра
    - `id` - `system.adapter.myAdapter.%INSTANCE%.test`, вы можете использовать заполнитель `%INSTANCE%`, чтобы заменить его текущим именем экземпляра.
    - `ack` - false (по умолчанию false)
    - `val` - '${data.myText}_test' или число. Тип будет определен автоматически по типу состояния, а также будет выполнено преобразование.
    - `okText` - Оповещение, которое будет показано при нажатии кнопки
    - `вариант` - `содержится`, `обрисовывается`, ''

- `staticText` — статический текст, подобный описанию
    - `label` - многоязычный текст
    - `текст` - то же, что и метка

- `staticLink` — статическая ссылка
    - `label` - многоязычный текст
    - `href` — ссылка. Ссылка может быть динамической, например `#tab-objects/customs/${data.parentId}`
    - `button` - показать ссылку как кнопку
    - `variant` - тип кнопки (`outlined`, `contained`, `text`)
    - `color` - цвет кнопки (например, `primary`)
    - `icon` - если значок должен отображаться: `auth`, `send`, `web`, `warning`, `error`, `info`, `search`, `book`, `help`, `upload` . Вы можете использовать значки `base64` (они начинаются с `data:image/svg+xml;base64,...`) или изображения `jpg/png` (оканчиваются на `.png`). (Если вам нужно больше значков, запросите через Issue)

- `staticImage` — статическое изображение
    - `href` — необязательная HTTP-ссылка
    - `src` - название картинки (из админки)

- `table` - таблица с элементами, которые можно удалять, добавлять, перемещать вверх и вниз.
    - `items` - `[{"type": см. выше, "width": px или %, "title": {"en": "header"}, "attr": "name", "filter": false , "sort": true, "default": ""}]`
    - `noDelete` — логическое значение, если удаление или добавление отключено. Если `noDelete` имеет значение false, добавление, удаление и перемещение вверх/вниз должно работать.
    - `objKeyName` - (устаревшая настройка, не использовать!) - имя ключа в `{"192.168.1.1": {delay: 1000, Enabled: true}, "192.168.1.2": {delay: 2000, включено: ложь}}`
    - `objValueName` - (устаревшая настройка, не используйте!) - имя значения в `{"192.168.1.1": "value1", "192.168.1.2": "value2"}`
    - `allowAddByFilter` - разрешено ли добавление, даже если фильтр установлен
    - `showSecondAddAt` — количество строк, из которых будет отображаться вторая кнопка добавления внизу таблицы. По умолчанию 5
    - `showFirstAddOnTop` — показывать первую кнопку плюса вверху первого столбца, а не слева.
    - `clone` - [необязательно] - если должна отображаться кнопка клонирования. Если это правда, будет показана кнопка клонирования. Если имя атрибута, это имя будет уникальным.
    - `export` - [необязательно] - должна ли отображаться кнопка экспорта. Экспортировать в файл csv.
    - `import` - [необязательно] - должна ли отображаться кнопка импорта. Импорт из csv-файла.
    - `uniqueColumns` - [необязательно] - укажите массив столбцов, записи в которых должны быть уникальными.

- `accordion` - аккордеон с элементами, которые можно удалять, добавлять, перемещать вверх и вниз (Admin 6.6.0 и новее)
    - `items` - `[{"type": см. выше, "attr": "name", "default": ""}]` - элементы можно размещать как на `panel` (xs, sm, md, LG и NewLine)
    - `titleAttr` - ключ списка элемента, который должен использоваться в качестве имени
    - `noDelete` — логическое значение, если удаление или добавление отключено. Если `noDelete` имеет значение false, добавление, удаление и перемещение вверх/вниз должно работать.
    - `clone` - [необязательно] - если должна отображаться кнопка клонирования. Если это правда, будет показана кнопка клонирования. Если имя атрибута, это имя будет уникальным.

- `jsonEditor` — редактор json

- `язык` - выбор языка
    - `system` - разрешить использование системного языка из `system.config` по умолчанию.

- «сертификат»
    - `certType` - один из: `public`, `private`, `chained`. Но начиная с версии 6.4.0 вы можете использовать тип «сертификаты».

— «сертификаты» — это универсальный тип, который управляет атрибутами «certPublic», «certPrivate», «certChained» и «leCollection».

  Пример:

```json
{
   "_certs": {
       "type": "certificates",
       "newLine": true,
       "hidden": "!data.secure",
       "sm": 12
   }
}
  ```

- `certCollection` — выберите коллекцию сертификатов или просто используйте все коллекции или вообще не используйте Let's Encrypt.

- `custom` (только Admin6)
    - `name` — имя компонента, которое будет предоставлено через реквизиты, например ComponentInstancesEditor.
    - `url` — Расположение компонента
        - `custom/customComponents.js`: в этом случае файлы будут загружены из `/adapter/ADAPTER_NAME/custom/customComponents.js`
        - `https://URL/myComponent`: напрямую с URL-адреса.
        - `./adapter/ADAPTER_NAME/custom/customComponent.js`: в этом случае файлы будут загружены из `/adapter/ADAPTER_NAME/custom/customComponents.js`
    - `i18n` - true, если файлы `i18n/xx.json` расположены в том же каталоге, что и компонент или объект перевода `{"text1": {"en": Text1"}}`

- `разделитель` - горизонтальная линия
    - `height` - необязательная высота
    - `color` - необязательный цвет разделителя или `основной`, `вторичный`

- `заголовок`
    - `текст`
    - `размер` - 1-5 => h1-h5

- `крон`
    - `complex` - показывать CRON с «минутами», «секундами» и т. д.
    - `simple` - показать простые настройки CRON

- `fileSelector` (только Admin6)
    - `pattern` - Шаблон расширения файла. Разрешено `**/*.ext` отображать все файлы из подпапок, `*.ext` для отображения из корневой папки или `folderName/*.ext` для отображения всех файлов в подпапке `folderName`. По умолчанию `**/*.*`.
    - `fileTypes` - [необязательный] тип файлов: `аудио`, `изображение`, `текст`
    - `objectID` - идентификатор объекта типа `мета`. Вы можете использовать специальный заполнитель %INSTANCE%: например, myAdapter.%INSTANCE%.files.
    - `upload` - путь, по которому будут храниться загруженные файлы. Как `имя_папки`. Если не определено, поле загрузки отображаться не будет. Чтобы загрузить в корень, установите в этом поле значение `/`.
    - `refresh` - Показать кнопку обновления рядом с выбором.
    - `maxSize` - максимальный размер файла (по умолчанию 2 МБ)
    - `withFolder` - показывать имя папки, даже если все файлы в одной папке
    - `delete` - Разрешить удаление файлов.
    - `noNone` - не показывать опцию `none`
    - `noSize` - Не показывать размер файлов

- `файл` (только Admin6)

  Поле ввода с выбором файла

    - `disableEdit` - если пользователь может ввести имя файла вручную, а не только через диалог выбора.
    - `limitPath` - ограничить выбор одним конкретным объектом типа `meta` и следующим путем (не обязательно)
    - `filterFiles` - например `['png', 'svg', 'bmp', 'jpg', 'jpeg']`
    - `filterByType` - `изображения, код, txt, аудио, видео`
    - `allowUpload` - разрешена загрузка файлов
    - `allowDownload` - разрешено скачивание файлов (по умолчанию true)
    - `allowCreateFolder` - разрешено создание папок
    - `allowView` - разрешенный просмотр плитки (по умолчанию true)
    - `showToolbar` - показать панель инструментов (по умолчанию true)
    - `selectOnlyFolders` - пользователь может выбирать только папки (например, для пути загрузки)

- `imageSendTo` — показывает изображение, полученное от бэкэнда в виде строки base64.
    - `width` - ширина QR-кода в пикселях.
    - `height` - высота QR-кода в пикселях
    - `команда` - команда sendTo
    - `jsonData` - строка - `{"subject1": "${data.subject}", "options1": {"host": "${data.host}"}}`. Эти данные будут отправлены на серверную часть
    - `данные` - объект - `{"subject1": 1, "data": "static"}`. Вы можете указать jsonData или data, но не то и другое. Эти данные будут отправлены на серверную часть, если jsonData не определен.

  Пример кода в серверной части:

```
adapter.on('message', obj => {
    if (obj.command === 'send') {
        const QRCode = require('qrcode');
        QRCode.toDataURL('3ca4234a-fd81-fdb8-5584-08c732f70e4d', (err, url) =>
            obj.callback && adapter.sendTo(obj.from, obj.command, url, obj.callback));
    }
});
```

- `выбратьОтправить`

  Показывает раскрывающееся меню с заданными значениями экземпляра.

    - `команда` - команда sendTo
    - `jsonData` - строка - `{"subject1": "${data.subject}", "options1": {"host": "${data.host}"}}`. Эти данные будут отправлены на серверную часть
    - `данные` - объект - `{"subject1": 1, "data": "static"}`. Вы можете указать jsonData или data, но не то и другое. Эти данные будут отправлены на серверную часть, если jsonData не определен.
    - `manual` - разрешить ручное редактирование. Без раскрывающегося меню (если экземпляр не в сети). По умолчанию «истина».
    - `multiple` - выбор множественного выбора
    - `showAllValues` - показать элемент, даже если для него не найдена метка (несколько раз), default=`true`
    - `noTranslation` - не переводить метки выбора

Чтобы использовать эту опцию, ваш адаптер должен реализовать обработчик сообщений: Результатом команды должен быть массив в форме `[{"value": 1, "label": "one"}, ...]`.

```
adapter.on('message', obj => {
   if (obj) {
       switch (obj.command) {
           case 'command':
               if (obj.callback) {
                   try {
                       const { SerialPort } = require('serialport');
                       if (SerialPort) {
                           // read all found serial ports
                           SerialPort.list()
                               .then(ports => {
                                   adapter.log.info(`List of port: ${JSON.stringify(ports)}`);
                                   adapter.sendTo(obj.from, obj.command, ports.map(item => ({label: item.path, value: item.path})), obj.callback);
                               })
                               .catch(e => {
                                   adapter.sendTo(obj.from, obj.command, [], obj.callback);
                                   adapter.log.error(e)
                               });
                       } else {
                           adapter.log.warn('Module serialport is not available');
                           adapter.sendTo(obj.from, obj.command, [{label: 'Not available', value: ''}], obj.callback);
                       }
                   } catch (e) {
                       adapter.sendTo(obj.from, obj.command, [{label: 'Not available', value: ''}], obj.callback);
                   }
               }

               break;
       }
   }
});
```

- `autocompleteSendTo`

  Показывает элемент управления автозаполнением с заданными значениями экземпляра.

  - `команда` - команда sendTo
  - `jsonData` - строка - `{"subject1": "${data.subject}", "options1": {"host": "${data.host}"}}`. Эти данные будут отправлены на серверную часть
  - `данные` - объект - `{"subject1": 1, "data": "static"}`. Вы можете указать jsonData или data, но не то и другое. Эти данные будут отправлены на серверную часть, если jsonData не определен.
  - `freeSolo` — установите для `freeSolo` значение `true`, чтобы текстовое поле могло содержать любое произвольное значение.
  - `alsoDependsOn` - при изменении каких атрибутов команду необходимо отправить повторно
  - `maxLength` - максимальная длина текста в поле

Чтобы использовать эту опцию, ваш адаптер должен реализовать обработчик сообщений: Результатом команды должен быть массив в форме `["value1", {"value": "value2", "label": "Value2"}, ...]`. Пример обработчика см. в `selectSendTo`.

- `textSendTo`

  Показывает управление только для чтения с заданными значениями экземпляра.

  - `контейнер` - div, текст
  - `copyToClipboard` - если true - показать кнопку
  - `alsoDependsOn` - при изменении каких атрибутов команду необходимо отправить повторно
  - `команда` - команда sendTo
  - `jsonData` - строка - `{"subject1": "${data.subject}", "options1": {"host": "${data.host}"}}`. Эти данные будут отправлены на серверную часть
  - `данные` - объект - `{"subject1": 1, "data": "static"}`. Вы можете указать jsonData или data, но не то и другое. Эти данные будут отправлены на серверную часть, если jsonData не определен.

Чтобы использовать эту опцию, ваш адаптер должен реализовать обработчик сообщений: Результатом команды должна быть строка.

```
adapter.on('message', obj => {
    if (obj) {
      switch (obj.command) {
        case 'command':
          obj.callback && adapter.sendTo(obj.from, obj.command, 'Received ' + JSON.stringify(obj.message), obj.callback);
          break;
      }
    }
});
```

- `координаты`

  Определяет текущее местоположение и используемые координаты `system.config`, если это невозможно, в форме «широта,долгота».

  - `divider` - разделитель между широтой и долготой. По умолчанию "," (используется, если longitudeName и latitudeName не определены)
  - `autoInit` - поле инициализации с текущими координатами, если оно пустое
  - `longitudeName` - если определено, долгота будет храниться в этом атрибуте, разделитель будет игнорироваться.
  - `latitudeName` - если определено, широта будет храниться в этом атрибуте, разделитель будет игнорироваться.
  - `useSystemName` - если определено, будет отображаться флажок «Использовать системные настройки», а широта и долгота будут считываться из system.config, логическое значение будет сохранено под заданным именем.

- `license` — показывает информацию о лицензии, если она еще не принята. Должен быть определен один из атрибутов `texts` или `licenseUrl`. Когда лицензия будет принята, для определенного атрибута конфигурации будет установлено значение true.
  - `texts` - массив абзацев с текстами, каждый из которых будет отображаться как отдельный абзац
  - `licenseUrl` — URL-адрес файла лицензии (например, https://raw.githubusercontent.com/ioBroker/ioBroker.docs/master/LICENSE)
  - `title` - Название диалога лицензии.
  - `agreeText` - Текст кнопки согласования
  - `checkBox` — если определено, будет показан флажок с заданным именем. Если этот флажок установлен, согласованная кнопка будет активирована.

- `checkLicense` — специальный компонент для проверки лицензии онлайн. В нативном коде требуются именно свойства `license` и `useLicenseManager`.
  - `uuid` - Проверить UUID
  - `версия` - Проверить версию

- `uuid` — Показать UUID iobroker
- `port` - Специальный ввод для портов. Он автоматически проверяет, используется ли порт другими экземплярами, и отображает предупреждение.

**Примечание: атрибуты или элементы управления, отмеченные знаком «!», еще не реализованы.**

## Общие атрибуты элементов управления
Все типы могут иметь:

- `sm` - ширина в 1/12 экрана на маленьком экране
- `md` - ширина в 1/12 экрана на средних экранах
- `lg` - ширина в 1/12 экрана на больших экранах.
- `xs` - ширина в 1/12 экрана на очень маленьких экранах.
- `newLine` - должен показываться с новой строки
- `label` — строка или объект типа {en: 'Name', ru: 'Имя'}
- `hidden` — функция JS, которая может использовать `native.attribute` для вычислений.
- `hideOnlyControl` - если скрыто, место будет показано, но без элемента управления
- `disabled` — функция JS, которая может использовать `native.attribute` для вычислений.
- `help` - текст справки (многоязычный)
- `helpLink` - href для справки (можно использовать только вместе с `help`)
- `style` — стиль css в нотации ReactJS: `radiusBorder`, а не `radius-border`.
- `darkStyle` - стиль CSS для темного режима.
- `валидатор` - функция JS: true нет ошибок, false - ошибка
- `validatorErrorText` — текст, отображаемый в случае сбоя валидатора.
- `validatorNoSaveOnError` - отключить кнопку сохранения в случае ошибки
- `tooltip` - необязательная всплывающая подсказка
- `default` - значение по умолчанию
- `defaultFunc` - функция JS для расчета значения по умолчанию.
- `defaultSendTo` - команда для запроса начального значения из работающего экземпляра, пример: `"myInstance": {"type": "text", "defaultSendTo": "fill"}`
  - `data` - статические данные
  - `jsonData` — статические данные
  - если `data` и `jsonData` не определены, будет отправлена следующая информация `{"attr": "<имя атрибута>", "value": "<текущее значение>"}`
  - `button` — метка кнопки для повторного запуска запроса от экземпляра
  - `buttonTooltip` — всплывающая подсказка кнопки (по умолчанию: `Запросить данные по экземпляру`)
  - `buttonTooltipNoTranslation` — не переводить подсказку кнопки.
- `placeholder` - заполнитель (для управления текстом)
- `noTranslation` - не переводить выделенные фрагменты или другие параметры (не для справки, метки или заполнителя)
- `onChange` — Структура в виде `{"alsoDependsOn": ["attr1", "attr2], "calculateFunc": "attr1 + attr2", "ignoreOwnChanges": true}`
- `doNotSave` - не сохранять этот атрибут, поскольку он используется только для внутренних вычислений.
- `noMultiEdit` - если для этого флага установлено значение true, это поле не будет отображаться, если пользователь выбрал для редактирования более одного объекта.
- `подтвердить`
  - `condition` - функция JS: true показать диалог подтверждения
  - `text` - текст диалога подтверждения
  - `title` - заголовок диалога подтверждения
  - `ok` — текст для кнопки ОК.
  - `cancel` — текст для кнопки «Отмена».
  - `type` - одно из: `info`, `warning`, `error`, `none`
  - `alsoDependsOn` - массив с атрибутами, чтобы проверить состояние и по этим атрибутам

```
{
    "type": "tabs",
    "items": {
        "options1": {
            "type": "panel",
            "label": "Tab1",
            "icon": "base64 svg", // optional
            "items": {
                myPort: {
                    "type": "number",
                    "min": 1,
                    "max": 65565,
                    "label": "Number",
                    "sm": 6, // 1 - 12
                    "validator": "'"!!data.name"'", // else error
                    "hidden": "data.myType === 1", // hidden if myType is 1
                    "disabled": "data.myType === 2" // disabled if myType is 2
                },
                "options.myType": { // name could support more than one levelhelperText
                    "newLine": true, // must start from new row
                    "type": "select",
                    "label": "Type",
                    "sm": 6, // 1 - 12
                    "options": [
                        {"label": "option 1", "value": 1},
                        {"label": "option 2", "value": 2}
                    ]
                },
                "myBool": {
                    "type": "checkbox",
                    "label": "My checkbox",
                }
            }
        },
        "tab2": {
            "label": "Tab2",
            "disabled": "data.myType === 1",
            "hidden": "data.myType === 2",
        }
    },
}
```

`Number`, `text`, `checkbox`, `select` поддерживают автозаполнение, позволяющее выбирать параметры, если они используются в качестве пользовательских настроек.
В этом случае значение будет предоставлено в виде массива всех возможных значений.

Пример:

```
...
   "timeout": {
      "type": "number",
      "label": "Timeout"
   }
...

data: {
   timeout: [1000, 2000, 3000]
}
```

В этом случае ввод должен быть текстом, где показано `__different__`, с опцией автозаполнения из 3 возможных значений.
Пользователи могут выбрать из раскрывающегося списка 1000, 2000 или 3000 или ввести собственное новое значение, например. 500.

Логическое значение должно поддерживать неопределенное значение, если значение равно [false, true]

Для неизмененных `__different__` должно быть возвращено другое значение:

```
Input:
data: {
   timeout: [1000, 2000, 3000]
}

Output if timeout was not changed:
newData: {
   timeout: "__different__"
}
```

Значение `__different__` зарезервировано, и ни один текстовый ввод не может принять его от пользователя.

Компонент должен выглядеть так

```
<SchemaEditor
    style={customStyle}
    className={classes.myClass}
    schema={schema}
    customInstancesEditor={CustomInstancesEditor}
    data={common.native}
    onError={(error, attribute) => error can be true/false or text. Attribute is optional}
    onChanged={(newData, isChanged) => console.log('Changed ' + isChanged)}
/>
```

Если схема не указана, схема должна быть создана автоматически на основе данных.

- `boolean` => флажок
- `text` => ввод текста
- `число` => число
- имя `bind` => ip
- имя `порт` => номер, min=1, max=0xFFFF
- имя `timeout` => число, help="ms"

Если у элемента нет атрибута `type`, предположим, что он имеет тип по умолчанию «панель».

## Стиль панели
Вы также можете задать стиль для панелей. Вот пример с фоном панели:

```json
{
  "i18n": true,
  "type": "panel",
  "style": {
    "backgroundImage": "url(adapter/mpd/background.png)",
    "backgroundPosition": "top",
    "backgroundRepeat": "no-repeat",
    "backgroundSize": "cover"
  },
  "items": {
    "...": {}
  }
}
```

## I18n
Есть несколько вариантов предоставления перевода.
Только первый из них совместим с нашим инструментом перевода сообщества Weblate, поэтому ему следует отдавать предпочтение перед остальными!

1. Пользователи могут предоставлять тексты из файлов.

На верхнем уровне структуры установите `i18n: true` и укажите файлы в администраторе:

- `admin/i18n/de/translations.json`
- `admin/i18n/en/translations.json`
- ...

или

- `admin/i18n/de.json`
- `admin/i18n/en.json`
- ...

Кроме того, пользователь может указать путь к файлам i18n, `i18n: "customI18n"`и предоставить файлы в администраторе:

- `admin/customI18n/de/translations.json`
- `admin/customI18n/en/translations.json`
- ...

или

- `admin/customI18n/de.json`
- `admin/customI18n/en.json`
- ...

2. Пользователь может предоставлять переводы непосредственно в ярлыке, например:

```
{
   "type": "text",
   "label: {
        "en": "Label",
        "de": "Taxt"
    }
}
```

3. Пользователь может предоставить переводы в атрибуте i18n:

```
{
    "18n": {
        "My Text: {
            "en": "My Text",
            "de": "Mein Text"
        },
        "My Text2: {
            "en": "My Text2",
            "de": "Mein Text2"
        },
    },
    "type": "panel",
    ...
}
```

Мы предлагаем использовать вариант 2, так как тексты можно будет обрабатывать с помощью Weblate.

## JS-функции
### Диалоговое окно конфигурации
JS-функция:

```
const myValidator = "_alive === true && data.options.myType == 2";

const func = new Function(
  'data',          // actual obj.native or obj.common.custom['adapter.X'] object
                   // If table, so data is current line in the table
  'originalData',  // data before changes
  '_system',       // system config => 'system.config'=>common
  '_alive',        // If instance is alive
  '_common',       // common part of instance = 'system.config.ADAPTER.X' => common
  '_socket',       // socket connection
  '_instance',     // instance number
  'arrayIndex',    // filled only by table and represents the row index
  'globalData',    // filled only by table and represents the obj.native or obj.common.custom['adapter.X'] object
  '_changed'       // indicator if some data was changed and must be saved
  myValidator.includes('return') ? myValidator : 'return ' + myValidator); // e.g. "_alive === true"

const isValid = func(data, systemConfig.common, instanceAlive, adapter.common, this.props.socket);

```

Если статус `alive` изменится, то все поля необходимо обновить, проверить, отключить, скрыть заново.

В JS-функции в настройках адаптера доступны следующие переменные:

- `data` - собственные настройки для данного экземпляра или текущей строки таблицы (для доступа ко всем настройкам используйте globalData)
- `_system` - конфигурация системы
- `_alive` — экземпляр жив
- `_common` — общие настройки для этого экземпляра
- `_socket` - сокет
- `_instance` - номер экземпляра
- `arrayIndex` - используется только в таблице и представляет текущую строку в массиве.
- `globalData` - используется только в таблице для всех настроек, а не только в одной строке таблицы.

### Диалоговое окно пользовательских настроек
JS-функция:

```
const myValidator = "customObj.common.type === 'boolean' && data.options.myType == 2";

const func = new Function(
  'data',
  'originalData',
  '_system',
  'instanceObj',
  'customObj',
  '_socket',
  arrayIndex,
  myValidator.includes('return') ? myValidator : 'return ' + myValidator); // e.g. "_alive === true"

const isValid = func(data || this.props.data, this.props.originalData, this.props.systemConfig, instanceObj, customObj, this.props.socket);
```

Следующие переменные доступны в функции JS в пользовательских настройках:

- `data` - текущие пользовательские настройки или текущая строка в таблице (для доступа ко всем настройкам используйте globalData)
- `originalData` - Неизмененные данные
- `_system` - конфигурация системы
- `instanceObj` - объект экземпляра адаптера
- `customObj` - сам текущий объект
- `_socket` - сокет
- `arrayIndex` - используется только в таблице и представляет текущую строку в массиве.
- `globalData` - используется только в таблице для всех настроек, а не только в одной строке таблицы.

## Пользовательский компонент
```
<CustomInstancesEditor
    common={common data}
    alive={isInstanceAlive}
    data={data}
    socket={this.props.socket}
    themeName={this.props.themeName}
    themeType={this.props.themeType}
    theme={this.props.theme}
    name="accessAllowedConfigs"
    onChange={(newData, isChanged) => {}}
    onError={error => error can be true/false or text}
/>
```

Примеры можно найти в адаптере [`telegram`](https://github.com/iobroker-community-adapters/ioBroker.telegram/tree/master/src-admin) или в [`pushbullet`](https://github.com/Jens1809/ioBroker.pushbullet/tree/master/src-admin).

## Схема
Схема — [здесь](https://github.com/ioBroker/adapter-react-v5/tree/master/schemas).