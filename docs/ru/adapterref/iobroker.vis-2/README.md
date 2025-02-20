---
translatedFrom: en
translatedWarning: Если вы хотите отредактировать этот документ, удалите поле «translationFrom», в противном случае этот документ будет снова автоматически переведен
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/ru/adapterref/iobroker.vis-2/README.md
title: Визуализация нового поколения для ioBroker: vis-2
hash: /XtZjIifd5fOIWxzaFqp8baBG5sSv18DL3sfRGKayMQ=
---
![Логотип](../../../en/adapterref/iobroker.vis-2/admin/vis-2.png)

![Количество установок](http://iobroker.live/badges/vis-2-stable.svg)
![НПМ-версия](http://img.shields.io/npm/v/iobroker.vis-2.svg)
![Загрузки](https://img.shields.io/npm/dm/iobroker.vis-2.svg)
![НПМ](https://nodei.co/npm/iobroker.vis-2.png?downloads=true)

# Визуализация нового поколения для ioBroker: vis-2
WEB-визуализация для платформы ioBroker.

## Установка и документация
![Демо-интерфейс](img/user0.png) ![Демо-интерфейс](../../../en/adapterref/iobroker.vis-2/img/user7.png)

[Онлайн-демо](https://iobroker.click/)

## Привязки объектов
Обычно большинство виджетов имеют атрибут ObjectID, и этот атрибут может быть связан с некоторым значением идентификатора объекта.
Но есть другой вариант привязки *любого* атрибута виджета к некоторому ObjectID.

Просто запишите в атрибут `{object.id}`, и он будет привязан к значению этого объекта.
Если вы используете специальный формат, вы даже можете выполнять с ним некоторые простые операции, например, умножение или форматирование.

Например, чтобы вычислить гипотенузу треугольника:

`{h:javascript.0.myCustom.height;w:javascript.0.myCustom.width;Math.max(20, Math.sqrt(h*h + w*w))}` будет интерпретироваться как функция:

```
value = await (async function () {
    var h = (await getState('javascript.0.myCustom.height')).val;
    var w = (await getState('javascript.0.myCustom.width')).val;
    return Math.max(20, Math.sqrt(h * h + w * w));
})();
```

или

`{h:javascript.0.myCustom.height;w:javascript.0.myCustom.width;h*w}` просто умножит высоту на ширину.

Вы можете использовать *любые* функции Javascript (браузера). Аргументы должны быть определены с помощью ':', в противном случае они будут интерпретироваться как формула.

Позаботьтесь о типах. Все они определены как строки. Чтобы быть уверенным, что это значение будет рассматриваться как число, используйте функцию parseFloat.

Итак, наш расчет гипотенузы будет:

```
{h:javascript.0.myCustom.height;w:javascript.0.myCustom.width;Math.max(20, Math.sqrt(Math.pow(parseFloat(h), 2) + Math.pow(parseFloat(w), 2)))}
```

### Устаревший формат
Паттен имеет следующий формат:

```
{objectID;operation1;operation2;...}
```

Поддерживаются следующие операции:

- `\*` - умножение. Аргумент должен быть в квадратных скобках, например «*(4)». В этом примере мы умножаем значение на 4.
- `\+` - доп. Аргумент должен быть в скобках, например «+(4.5)». В этом примере мы добавляем значение 4,5.
- `\-` - вычесть. Аргумент должен быть в скобках, например «-(-674,5)». В этом примере мы вычитаем из значения -674,5.
- `/` - деление. Аргумент должен быть в скобках, например «/(0,5)». В этом примере мы делим значение на 0,5.
- `%` - по модулю. Аргумент должен быть в скобках, например «%(5)». В этом примере мы берем по модулю 5.
- `round` - округлить значение.
- `round(N)` - округлить значение на N знаков после точки, например, 34.678;round(1) => 34.7
- `hex` - преобразовать значение в шестнадцатеричное значение. Все буквы в нижнем регистре.
- `hex2` - преобразовать значение в шестнадцатеричное значение. Все буквы в нижнем регистре. Если значение меньше 16, будет добавлен ведущий ноль.
- `HEX` - то же, что и шестнадцатеричное, но в верхнем регистре.
- `HEX2` - то же, что hex2, но в верхнем регистре.
- `date` - форматировать дату в соответствии с заданным форматом. Формат такой же, как в [iobroker.javascript](https://github.com/iobroker/iobroker.javascript/blob/master/README.md#formatdate).
- `min(N)` - если значение меньше N, взять N, иначе значение
- `max(M)` - если значение больше M, взять M, иначе значение
- `sqrt` - квадратный корень
- `pow(n)` - степень N.
- `pow` - степень 2.
- `floor` - Math.floor
- `ceil` - Math.ceil
- `random(R)` - Math.random() * R или просто Math.random(), если нет аргумента
- `formatValue(decimals)` - форматировать значение в соответствии с настройками системы и использовать десятичные дроби.
- `date(format)` - форматировать значение как дату. Формат такой: «ГГГГ-ММ-ДД чч:мм:сс.сс».
— `momentDate(format, useTodayOrYesterday)` — форматирует значение как дату с помощью Moment.js. [Утвержденные форматы необходимо вводить в соответствии с библиотекой moment.js](https://momentjs.com/docs/#/displaying/format/). При использовании `useTodayOrYesterday=true` формат `moment.js` `ddd`/`dddd` заменяется на сегодня/вчера.
- `array(element1,element2[,element3,element4])` - возвращает элемент индекса. например: `{id.ack;array(ack ложно,ack истинно)}`

Вы можете использовать этот шаблон в любом тексте, например

```
My calculations with {objectID1;operation1;operation2;...} are {objectID2;operation3;operation4;...}
```

или цветовые расчеты:

```
#{objectRed;/(100);*(255);HEX2}{objectGreen;HEX2}{objectBlue;HEX2}
```

Чтобы показать временную метку объекта, напишите `.ts` или `.lc` (для последнего изменения) в конце идентификатора объекта, например:

```
Last change: {objectRed.lc;date(hh:mm)}
```

### Специальные крепления
Существует ряд различных внутренних привязок для предоставления дополнительной информации в представлениях:

* `username` — показывает вошедшего в систему пользователя
* `view` - имя фактического просмотра
* `wname` — имя виджета
* `widget` - объект со всеми данными виджета. Может использоваться только в части JS, например `{a:a;widget.data.name}`
* `wid` - имя актуального виджета
* `язык` - может быть `de`, `en` или `ru`.
* `instance` — экземпляр браузера
* `login` - требуется ли вход в систему (например, чтобы показать/скрыть кнопку выхода из системы)
* `local_*` - если имя состояния начинается с `local_`, об этом не будет сообщено ioBroker, но будут обновлены все виджеты, которые зависят от этого состояния. (Локальная переменная для текущего сеанса браузера)

Примечание. Чтобы использовать «:» в вычислениях (например, в строковых формулах), используйте вместо этого «::».

**Помните**, что определения стилей будут интерпретироваться как привязки, поэтому используйте `{{style: value}}` или просто

```
{
	style: value
}
```

для этого.

## Фильтры
Чтобы визуализировать в одном представлении все количество виджетов, вы можете использовать фильтры, чтобы уменьшить количество виджетов, одновременно отображаемых в представлении.

У каждого виджета есть поле `filter`. Если вы установите для него какое-то значение, например. `light`, поэтому вы можете использовать другой виджет `(bars - filters, filter - dropdown)`, чтобы контролировать, какой фильтр на самом деле активен.

## Интерфейс управления
Vis создает 3 переменные:

- `control.instance` - Здесь должен быть написан экземпляр браузера или `FFFFFFFF`, если необходимо контролировать каждый браузер.
- `control.data` — параметр для команды. См. описание конкретной команды.
- `control.command` — имя команды. Запись этой переменной запускает команду. Это означает, что перед записью команды «экземпляр» и «данные» должны быть подготовлены с данными.

Команды:

* `alert` — показать окно оповещения в vis-2. «control.data» имеет следующий формат «сообщение;заголовок;jquery-значок». Название и значок jquery не являются обязательными. Названия значков можно найти [здесь](http://jqueryui.com/themeroller/). Чтобы отобразить значок «ui-icon-info», напишите `Message;;info`.
* `changeView` — переключиться на нужный вид. «control.data» должно иметь имя представления. Вы также можете указать имя проекта как «project/view». Проект по умолчанию — «main».
* `refresh` — перезагрузить vis-2, например, после изменения проекта для перезагрузки во всех браузерах.
* `reload` - то же, что и обновление.
* `dialog` - Показать диалоговое окно. Диалог должен существовать на виду. Один из:

    - `статический - HTML - Диалог`,
    - `статический - Значок - Диалог`,
    - `контейнер - HTML - просмотр в диалоге jqui`,
    - `контейнер - ext cmd - просмотр в диалоге jqui`,
    - `контейнер - Значок - просмотр в диалоге jqui`,
    - `контейнер - Кнопка - просмотр в диалоге jqui`.

    `control.data` должен иметь идентификатор виджета диалога, например. `w00056`.

* `диалогЗакрыть`
* `popup` — открывает новое окно браузера. Ссылка должна быть указана в `control.data`, например, http://google.com.
* `playSound` - воспроизвести звуковой файл. Ссылка на файл указывается в `control.data`, например, http://www.modular-planet.de/fx/marsians/Marsiansrev.mp3.

  Вы можете загрузить свой собственный файл в vis-2 и позволить ему воспроизводиться, например, `/vis-2.0/main/img/myFile.mp3`.

Если пользователь меняет представление или в начале, переменные будут заполнены vis-2 с помощью

- `control.instance`: экземпляр браузера и `ack=true`
- `control.data`: имя проекта и представления в форме `project/view`, например. `main/view` (и `ack=true`)
- `control.command`: `changedView` и `ack=true`

Вы можете записать JSON-строку или объект в `control.command` как `{instance: 'AABBCCDD', command: 'cmd', data: 'ddd'}`. В этом случае экземпляр и данные будут взяты из объекта JSON.

Пример адаптера JavaScript:

```
setState('vis-2.0.control.command', {"instance": "*", "command": "refresh", "data": ""});
```

## Вид по умолчанию
Вы можете определить для каждого вида желаемое разрешение (Меню=>Инструменты=>Разрешение).
Это всего лишь визуальная граница в режиме редактирования, показывающая размер экрана на определенном устройстве. В режиме реального времени она не будет видна и будут видны все виджеты за пределами границы.

Кроме того, вы можете определить, должно ли это представление использоваться по умолчанию для этого разрешения.

Таким образом, каждый раз, когда вызывается `index.html` (без `#viewName`), будет открываться наиболее подходящее для данного разрешения представление.
Если только одно представление имеет флаг *"По умолчанию"*, то это представление будет открываться независимо от разрешения или ориентации экрана.

Например, вы можете создать два вида «Альбомный-мобильный» и «Портрет-мобильный», и эти два вида будут автоматически переключаться при изменении ориентации или размера экрана.

Существует вспомогательный виджет «Основное - Разрешение экрана», который показывает фактическое разрешение экрана и наиболее подходящий вид по умолчанию для этого разрешения.

## Настройки
### Перезагрузить, если спит дольше, чем
Существует правило, что после некоторого периода отключения вся страница VIS будет перезагружена для синхронизации проекта.
Настроить это можно в меню «Настройки...». Если вы установите интервал «никогда», страница никогда не будет перезагружаться.

### Интервал повторного подключения
Установите интервал между попытками подключения в случае отключения. Если вы установите 2 секунды, соединение будет пытаться установить каждые 2 секунды.

### Темный экран повторного подключения
Иногда (ночью) требуется темный экран загрузки. С помощью этой опции вы можете установить его.

Обратите внимание, что эти настройки действительны только для повторного подключения, а не для первого подключения.

![Темный](../../../en/adapterref/iobroker.vis-2/img/dark_screen.png)

## SVG и currentColor
Ключевое слово currentColor в CSS позволяет элементам наследовать текущий цвет текста от родительского элемента.
Это может быть особенно полезно в SVG (масштабируемой векторной графике), поскольку обеспечивает более динамичное оформление и более простую интеграцию с HTML-контентом.

Вы можете использовать ключевое слово currentColor вместо определенного значения цвета для любого свойства внутри SVG, которое принимает значение цвета.
Вот простой пример с кругом в SVG:

```xml
<svg width="100" height="100" xmlns="http://www.w3.org/2000/svg">
    <circle cx="50" cy="50" r="40" fill="currentColor" />
</svg>
```

В этом случае SVG принимает цвет родительского элемента.
Например, если он использовался в меню и меню красного цвета, кружок будет красным.

## Делать
<!-- Заполнитель следующей версии (в начале строки):

### **РАБОТА В ПРОГРЕССЕ** -->

## Changelog
### 2.2.7 (2023-09-18)
* (bluefox) Improved icon selector: you can upload your own icon directly
* (bluefox) Optimized loading: do not load unused widget sets

### 2.2.6 (2023-09-17)
* (bluefox) Date binding corrected
* (bluefox) Optimized loading of widgeteria
* (bluefox) Horizontal navigation is fixed

### 2.2.5 (2023-09-12)
* (bluefox) Implemented horizontal navigation

### 2.2.4 (2023-09-04)
* (bluefox) Corrected license checking

### 2.2.2 (2023-08-16)
* (bluefox) Changed sentry settings

### 2.2.1 (2023-08-15)
* (bluefox) Added possibility to filter widgets in edit mode
* (bluefox) Added possibility to change the order of relative widgets with drag&drop

### 2.2.0 (2023-08-14)
* (bluefox) Release candidate 1

### 2.1.7 (2023-08-10)
* (bluefox) Optimized the rendering of the widgets

### 2.1.6 (2023-07-30)
* (bluefox) First beta release

### 2.1.4 (2023-07-19)
* (bluefox) Allowed to add widgets to widgets

### 2.0.36 (2023-06-21)
* (bluefox) Added widgeteria

### 2.0.29 (2023-05-17)
* (bluefox) Corrected errors

### 2.0.10 (2022-12-01)
* (bluefox) Added the file browser

### 2.0.8 (2022-11-26)
* (bluefox) Improved the error handling

### 2.0.0 (2022-10-21)
* (bluefox) Completely new visualization, but partly compatible with the previous version

## License
To use this adapter in `ioBroker` you need to accept the source code license of the adapter. The source code of this adapter is available under the CC BY-NC license.

Additionally, you need a license to use the adapter. The following license editions are available on https://iobroker.net/www/pricing 
* **Community-License: Free for private use!**: Get a free license by registering an account on [https://iobroker.net](https://iobroker.net). The license if checked online against the ioBroker license server when the vis-2 adapter is started, so an online connection at this time point is required!
* **Private use Offline-License**: For paying a small support fee, you can get rid of the required online license check on adapter startup. **Only for Private use!**
* **Commercial License**: When using Vis in a commercial environment or selling Vis as part of ioBroker packages to your customers, this license is for you. License check is also not requiring an online connection.

## License
 Copyright (c) 2021-2023 Denis Haev, https://github.com/GermanBluefox <dogafox@gmail.com>,
  
 Creative Common Attribution-NonCommercial (CC BY-NC)

 http://creativecommons.org/licenses/by-nc/4.0/

![CC BY-NC License](https://github.com/GermanBluefox/DashUI/raw/master/images/cc-nc-by.png)

Short content:
Licensees may copy, distribute, display and perform the work and make derivative works based on it only if they give the author or licensor the credits in the manner specified by these.
Licensees may copy, distribute, display, and perform the work and make derivative works based on it only for noncommercial purposes.
(Free for non-commercial use).