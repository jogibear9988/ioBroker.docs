---
translatedFrom: en
translatedWarning: Если вы хотите отредактировать этот документ, удалите поле «translationFrom», в противном случае этот документ будет снова автоматически переведен
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/ru/dev/stateroles.md
title: Государственные роли
hash: doDBQOCUroqOqEg/zuugGZ5piBB2jwVQwARblcrlYVk=
---
# Государственные роли
Для объектов типа `state` необходимо, чтобы их свойство `common.role` было установлено на одну из ролей, определенных в списке ниже.
Информация о роли является очень важной информацией и позволяет адаптерам визуализации и Smart-Assistant определять функцию объекта, а также то, как/относятся ли они к другим объектам в том же канале, устройстве или папке.

Пример: RGB-лампа может иметь следующие три объекта (или более) с разными ролями, которые принадлежат друг другу:

* `переключатель` - (Вкл./Выкл.)
* `level.color.rgb` с цветовым кодом лампы #RRGGBB
* `level.brightness` со значением яркости

Различные шаблоны Устройств, используемые для обнаружения с обязательными и необязательными объектами и их ролями, можно найти в [Репозиторий детекторов типов](https://github.com/ioBroker/ioBroker.type-detector/blob/master/DEVICES.md).

## Общий
* `state` - очень распространенное назначение. Если вы не знаете, какую роль играет государство, используйте эту.
* `текст` `common.type = строка`
* `text.url` `common.type = string` state val содержит URL-адрес для использования в привязке, iframe или img
* `html` `common.type = строка`
* `json` `common.type = строка`
* `список` `common.type = массив`
* `date` `common.type = string` - анализируется строкой `new Date(ddd)`
* `дата` `common.type = число` - `секунды эпохи * 1000`

## Датчик (логические значения, только для чтения)
`common.type=boolean, common.write=false`

* `sensor.window` - окно открыто-`true` или закрыто-`false`
* `sensor.door` - дверь открыта-`true` или закрыта-`false`
* `sensor.alarm` - какая-то общая тревога
* `sensor.alarm.flood` - протечка воды
* `sensor.alarm.fire` - датчик пожара
* `sensor.alarm.secure` - открыта дверь, открыто окно или обнаружено движение во время тревоги.
* `sensor.alarm.power` - Нет питания (`voltage = 0`)
* `sensor.light` - обратная связь от лампы, что она включена
* `sensor.lock` - фактическое положение замка
* `sensor.motion` - датчик движения
* `sensor.rain` - обнаружен дождь
* `sensor.noise` - обнаружен шум

## Кнопки (логические, только для записи)
`common.type=boolean, common.write=true, common.read=false`

* `кнопка`
* `кнопка.long`
* `button.stop` - напр. ролло стоп,
* `кнопка.стоп.наклон`
* `кнопка.старт`
* `кнопка.резюме`
* `кнопка.открыть.дверь`
* `кнопка.открыть.окно`
* `кнопка.открыть.блайнд`
* `кнопка.открыть.наклон`
* `кнопка.закрыть.жалюзи`
* `кнопка.закрыть.наклон`
* `кнопка.режим.`*
* `кнопка.режим.авто`
* `кнопка.режим.ручной`
* `кнопка.режим.тихий`

## Кнопки как сенсор
`common.type=boolean, common.write=false, common.read=true`

* `button` - разница, что `common.write=false`. Пожалуйста, избегайте этой роли и используйте `button.press` или `button.long`.
* `кнопка.long`
* `кнопка.нажмите`

## Значения (числа, только для чтения)
`common.type=number, common.write=false`

* `значение`
* `value.window` (`common.states={"0": "ЗАКРЫТО", "1": "НАКЛОН", "2": "ОТКРЫТО"}`) Важно иметь (`ЗАКРЫТО/НАКЛОНЕНО/ ОТКРЫТЬ`). Значения могут отличаться.
* `value.temperature` (`common.unit='°C' или '°F' или 'K'`)
* `значение.влажность`
* `value.co2` - CO2 (единица измерения: ppm)
* `value.brightness` - уровень яркости (единица измерения: люкс, )
* `значение.мин`
* `value.max`
* `значение.по умолчанию`
* `value.battery` - уровень заряда батареи
* `value.valve` - уровень клапана
* `value.time` - getTime() объекта Date()
* `value.interval` (common.unit='sec') - Интервал в секундах (может быть 0,1 или меньше)
* ~~value.date (common.type=string) - Дата в формате 2015.01.01 (без времени)~~
* ~~value.datetime (common.type=string) - Дата и время в системном формате~~
* `value.gps.longitude` - координаты долготы GPS
* `value.gps.latitude` - широта GPS
* `value.gps.elevation` - высота по GPS
* `value.gps` - долгота и широта вместе, например, "5,56;43,45"
* `value.gps.accuracy` - точность текущего измерения GPS
* `value.gps.radius` - радиус текущего измерения GPS
* ~~`value.power.consumption` - потребление энергии (единица измерения=Втч или КВтч)~~
* ~~`value.power.production` - производство энергии (единица измерения=Втч или КВтч)~~
* `value.energy` - энергия (единица измерения=Втч, кВтч или м3 для бензина)
* `value.energy.active` - активная энергия (единица измерения=Ws, Wh, kWh)
* `value.energy.reactive` - реактивная энергия (единица измерения=варс, кВарч)
* `value.energy.consumed` - потребляемая энергия (единица измерения = Вт, Втч, кВтч)
* `value.energy.produced` - произведенная мощность (единица измерения = Вт, Втч или кВтч)
* `value.power` - мощность энергии (единица измерения = Вт или кВт)
* `value.power.active` - активная мощность (единица измерения=Вт, кВт)
* `value.power.reactive` - реактивная мощность (единица измерения=вар, кВар)
* `value.power.consumed` - потребляемая мощность (единица измерения = Вт или кВт)
* `value.power.produced` - произведенная мощность (единица измерения = Вт или кВт)
* `value.direction` - (common.type=число ~~или строка~~, указывает вверх/вниз, влево/вправо, 4-позиционные переключатели, направление ветра, ... )
* `value.curtain` - фактическое положение шторы
* `value.blind` - фактическое положение жалюзи (`max=полностью открыто, min=полностью закрыто`)
* `value.tilt` - фактическое положение наклона (`max = полностью открыто, min = полностью закрыто`)
* `value.lock` - фактическое положение замка
* `value.speed` - скорость ветра
* `значение.давление` - (единица измерения: мбар)
* `значение.расстояние`
* `значение.расстояние.видимость`
* `value.severity` - некоторая серьезность (могут быть указаны состояния), чем выше, тем важнее
* `value.warning` - какое-то предупреждение (могут быть указаны состояния), чем выше, тем важнее
* `value.sun.elevation` - высота солнца в °
* `value.sun.azimuth` - азимут солнца в °
* `value.voltage` - Напряжение в вольтах, `unit=V`
* `value.current` - ток в амперах, `unit=A`
* `value.fill` - Уровень заполнения, `unit=l,ml,m3,%`
* `value.blood.sugar` - значение сахара в крови, `unit=mmol,mgdl`

## Индикаторы (логические, только для чтения)
`common.type=boolean, common.write=false`

Отличие *Индикаторов* от *Датчиков* в том, что индикаторы будут отображаться в виде маленькой иконки. Сенсоры как реальная ценность.
Так что индикатор может быть не один в канале. Это должно быть какое-то другое основное состояние внутри канала.

* `индикатор`
* `indicator.working` - указывает, что целевые системы что-то выполняют, например, жалюзи или открытие замка.
* `indicator.reachable` — если устройство подключено к сети
* `indicator.connected` - используется только для экземпляров. Используйте `indicator.reachable` для устройств
* `indicator.maintenance` - показывает системные предупреждения/ошибки, аварийные сигналы, сервисные сообщения, разряженную батарею и тому подобное
* `indicator.maintenance.lowbat`
* `indicator.maintenance.unreach`
* `indicator.maintenance.alarm`
* `indicator.lowbat` - верно, если батарея разряжена
* `indicator.alarm` - то же, что и Indicator.maintenance.alarm
* `indicator.alarm.fire` - обнаружен пожар
* `indicator.alarm.flood` - обнаружен флуд
* `indicator.alarm.secure` - дверь или окно открыто
* `indicator.alarm.health` - проблемы со здоровьем

## Уровни (числа, чтение-запись)
С помощью **уровней** вы можете контролировать или устанавливать некоторое числовое значение.

`common.type=number, common.write=true`

* `уровень`
* `level.humidity` - влажность как уставка, т.е. для увлажнителей/климат-контролей
* `level.battery` - целевое напряжение/емкость батареи, т.е. для загрузки
* `level.battery.min` - минимальное напряжение/емкость аккумулятора
* `level.battery.max` - максимальное напряжение/емкость аккумулятора
* `level.valve` - значение открытия клапанов
* `уровень.давление` -
* `level.pressure.min` - минимально допустимое значение давления воздуха или масла
* `level.pressure.max` - максимально допустимое значение давления воздуха или масла
* `level.voltage` - целевое напряжение для генераторов
* `level.voltage.min` - минимальное напряжение для генераторов
* `level.voltage.max` - максимальное напряжение для генераторов
* `level.current` - целевой ток для, например, загрузки аккумуляторных устройств
* `level.current.min` - минимальный ток для т.е. загрузки аккумуляторных устройств
* `level.current.max` - максимальный ток для, т.е. загрузки аккумуляторных устройств
* `level.fill` - уставка для любых состояний уровня заполнения контейнера
* `level.min` - минимально допустимый уровень
* `level.max` - максимально допустимый уровень
* `level.default` - уровень по умолчанию
* `level.dimmer` - яркость тоже уменьшается
* `level.blind` - установить положение жалюзи (max = полностью открыто, min = полностью закрыто)
* `level.temperature` - установить желаемую температуру
* `level.valve` - уставка положения клапана
* `уровень.цвет.красный`
* `уровень.цвет.зеленый`
* `уровень.цвет.синий`
* `level.color.white` - rgbW
* `level.color.hue` - цвет в ° `0-360; 0=красный, 120=зеленый, 240=синий, 360=красный (циклический)`
* `уровень.цвет.насыщенность`
* `level.color.rgb` - шестнадцатеричный цвет, например `#rrggbb` (`common.type=string`)
* `level.color.rgbw` - шестнадцатеричный цвет, например `#rrggbbww` (`common.type=string`)
* `level.color.cie` - цвет cie в форме `[x, y]` (`common.type=string)
* `уровень.цвет.яркость`
* `level.color.temperature` - цветовая температура в К° `2200° теплый-белый, 6500° холодный белый`
* `уровень.таймер`
* `level.timer.sleep` - таймер сна. 0 - выключено или в минутах
* ...
* `level.volume` - (`min=0, max=100`) - громкость звука, но min, max могут отличаться. мин < макс
* `level.volume.group` - (`min=0, max=100`) - громкость звука, для группы устройств
* `level.curtain` - установить положение шторы
* `level.tilt` - установить положение наклона жалюзи (max = полностью открыто, min = полностью закрыто)

## Переключатели (булевы значения, чтение-запись)
Переключатель управляет логическим устройством (`true = ON, false = OFF`)

`common.type=boolean, common.write=true`

* `переключатель`
* `switch.lock` - блокировка (`true - открыть блокировку, false - закрыть блокировку`)
* `switch.lock.door` - дверной замок
* `switch.lock.window` - блокировка окна
* `switch.mode.boost` - запуск/остановка форсированного режима термостата
* `switch.mode.party` - запуск/остановка режима вечеринки термостата
* `switch.power` - вкл/выкл термостат или кондиционер
* `switch.light`
* `switch.comfort` - комфортный режим
* `переключатель.включить`
* `switch.power` - включение/выключение питания
* `переключить.режим.`*
* `switch.mode.auto` - вкл/выкл автоматический режим
* `switch.mode.manual` - включение/выключение ручного режима
* `switch.mode.silent` - вкл/выкл беззвучный режим
* `switch.mode.moonlight` - включение/выключение режима лунного света
* `switch.mode.color` - включение/выключение цветового режима
* `switch.gate` - закрывает (false) или открывает (true) ворота

## Кондиционер или термостат
* `level.mode.fan` - `АВТО, ВЫСОКИЙ, НИЗКИЙ, СРЕДНИЙ, ТИХИЙ, ТУРБО`
* `level.mode.swing` - `АВТО, ГОРИЗОНТАЛЬНО, СТАЦИОНАРНО, ВЕРТИКАЛЬНО`
* `level.mode.airconditioner` - кондиционер: `AUTO, COOL, DRY, ECO, FAN_ONLY, HEAT, OFF`, термостат нагрева: `AUTO, MANUAL, VACATION`,
* `level.mode.thermostat` - термостат: `AUTO, MANUAL, VACATION`,

 В дополнение к этим состояниям обычно требуются `level.temperature` и `switch.power`, необходимые для сопоставления кондиционера.

TODO: Подумайте об ионизации и осцилляции.

## Пылесос
* `level.mode.cleanup` - Перечисление 'AUTO, ECO, EXPRESS, NORMAL, QUIET'. Требуются только «АВТО» и «НОРМАЛЬНЫЙ».
* `level.mode.work` - Перечисление `AUTO, FAST, MEDIUM, SLOW, TURBO`. Необязательное состояние.
* `value.water` - уровень воды 0-100%.
* `value.waste` - уровень мусорного бака 0-100%. (0% - пусто, 100% - заполнено)
* `indicator.maintenance.waste` - Мусорное ведро дура.
* `value.state` - `ДОМ, ЧИСТКА, ПАУЗА` и так далее.

Кроме того, в этих состояниях обычно требуется `switch.power` для сопоставления пылесоса. `switch.power` в этом случае работает как: `true` — убрать, `false` — вернуться домой.
Опционально `value.battery` и

## Ворота
* `switch.gate` - закрывает (false) или открывает (true) ворота (обязательно)
* `value.position` - позиция ворот в процентах (100% открыты, 0% - закрыты)
* `value.gate` - то же, что и `value.position`
* `button.stop` - остановить движение ворот

## СМИ
Специальные роли для медиаплееров

* `кнопка.стоп`
* `кнопка.играть`
* `кнопка.далее`
* `кнопка.предыдущий`
* `кнопка.пауза`
* `переключатель.пауза`
* `кнопка.вперед`
* `кнопка.реверс`
* `кнопка.fastforward`
* `кнопка.fastreverse`
* `кнопка.громкость.вверх`
* `кнопка.громкость.вниз`
* `media.seek` - (`common.type=число`) %
* `media.mode.shuffle` - (`common.type=number`) 0 - нет, 1 - все, 2 - один
* `media.mode.repeat` - (`common.type=boolean`)
* `media.state` - `['play','stop','pause']` или `[0 – пауза, 1 – воспроизведение, 2 – остановка]` или `[true – воспроизведение/false – пауза]`
* `медиа.артист`
* `медиа.альбом`
* `медиа.название`
* `медиа.название.следующий`
* `media.cover` - URL обложки
* `media.cover.big` - URL большой обложки
* `media.cover.small` - маленькая ссылка на обложку
* `media.duration.text` - например, "2:35"
* `media.duration` - (`common.type=число`) секунд
* `media.elapsed.text` - например, "1:30"
* `media.elapsed` - (`common.type=число`) секунд
* `media.broadcastDate` - (`common.type=string`) Дата трансляции
* `media.mute` - (`common.type=boolean`) true отключен
* `media.season` - (`common.type=string`) номер сезона (важно, что тип действительно "string", чтобы можно было указать отсутствие сезона с помощью "")
* `media.episode` - (`common.type=string`) номер эпизода (важно, что тип действительно "string", чтобы можно было указать отсутствие эпизода с помощью "")
* `media.mute.group` - (`common.type=boolean`) отключение звука группы устройств
* `media.tts` - преобразование текста в речь
* `media.bitrate` - кбит/с
* `media.genre` - жанр песни
* `media.date` - год песни
* `media.track` - (`common.type=string`) идентификатор текущей воспроизводимой дорожки `[0 - ~]` (важно, чтобы тип действительно был `string`, чтобы можно было указать отсутствие дорожки с помощью "")
* `media.playid` - идентификатор трека медиаплеера
* `media.add` - добавить текущий плейлист
* `media.clear` - очистить текущий плейлист (только для записи)
* `media.playlist` - массив json, например
* `media.url` - URL для воспроизведения или текущий URL
* `media.url.announcement` - URL для воспроизведения объявления
* `media.jump` - Количество элементов для перехода в плейлисте (может быть отрицательным)
* `media.content` - тип воспроизводимого медиафайла, например аудио/mp3.
* `media.link` - состояние с текущим файлом
* `media.input` - номер или строка входа (AUX, AV, TV, SAT, ...)
* `level.bass` - Уровень баса
* `level.treble` - Уровень высоких частот
* `switch.power.zone` - зона питания

```
[
    {
        "artist": "",
        "album": "",
        "bitrate":0,
        "title": "",
        "file": "",
        "genre": "",
        "year": 0,
        "len": "00:00",
        "rating": "",
        "cover": ""
    }
]
```

* `media.browser` - массив json типа "файлы"

```
[
    {
        "fanart": "",
        "file": "",//smb://192.168.1.10/music/AtlantidaProject/
        "filetype": "", //directory
        "label": "",
        "lastmodified": "",
        "mimetype": "",
        "size": 0,
        "thumbnail": "",
        "title": "",
        "type": "",
        "lastmodified": "2016-02-27 16:05:46",
        "time": "88",
        "track": "01",
        "date": "2005",
        "artist": "yonderboy (H)",
        "album": "splendid isolation",
        "genre": "Trip-Hop"
    }
]
```

## Погода
* `value.temperature` - Фактическая температура
* `value.temperature.windchill` - Фактическое охлаждение ветром
* `value.temperature.dewpoint` - Фактическая точка росы
* `value.temperature.feelslike` - Фактическая температура "по ощущениям"
* `value.temperature.min` - Минимальная температура за последние 24 часа
* `value.temperature.max` - Максимальная температура за последние 24 часа
* `value.humidity` - фактическая или средняя влажность
* `value.humidity.min` - фактическая влажность
* `value.humidity.max` - фактическая влажность
* `value.speed.wind` - фактическая или средняя скорость ветра
* `value.speed.max.wind` - максимальная скорость ветра за последние 24 часа
* `value.speed.min.wind` - минимальная скорость ветра за последние 24 часа
* `value.speed.wind.gust` - фактическая скорость порыва ветра
* `value.direction.wind` - фактическое или среднее направление ветра в градусах
* `value.direction.max.wind` - фактическое направление ветра в градусах
* `value.direction.min.wind` - фактическое направление ветра в градусах
* `weather.direction.wind` - фактическое или среднее направление ветра в виде текста, например. ССЗ
* `date` - фактическая дата или дата последнего чтения информации
* `date.sunrise` - Восход солнца на сегодня
* `date.sunset` - Закат на сегодня
* `dayofweek` - день недели в виде текста
* `location` - Текстовое описание местоположения (например, адрес)
* `weather.icon` - URL значка фактического состояния на данный момент
* `weather.icon.wind` - актуальный URL значка ветра на данный момент.
* `weather.icon.name` - Текущее имя значка состояния на данный момент
* `weather.state` - описание фактической погоды.
* `value.precipitation` - (`type: number, unit: mm`) осадки за последние 24 часа дождь/снег (Niederschlag heute für Schnee oder Regen / осадки сегодня снега или дождя)
* `value.precipitation.hour` - Фактический уровень осадков за последний час
* `value.precipitation.today` - Фактический уровень осадков за сегодня (до 0:00)
* `value.precipitation.chance` - Фактическая вероятность осадков за сегодня
* `value.precipitation.type` - Фактический тип осадков за сегодня. (`type: number`) Состояния: 0 - НЕТ, 1 - ДОЖДЬ, 2 - СНЕГ, 3 - ГРАД
* `value.radiation` - Фактический уровень солнечной радиации
* `value.uv` - Фактический уровень УФ
* `value.clouds` - Облака на небе. 0% - облаков нет, 100% - много облаков.
* `value.rain` - Фактический уровень дождя за последние 24 часа.
* `value.rain.hour` - Фактический уровень дождя за последний час
* `value.rain.today` - Фактический уровень дождя на сегодня (до 0:00)
* `value.snow` - Фактический уровень снега за последние 24 часа.
* `value.snow.hour` - Фактический уровень снега за последний час
* `value.snow.today` - Фактический уровень снега на сегодня (до 0:00)
* `value.snowline` - Фактическая линия снега в метрах
* `weather.chart.url` - URL-адрес графика для истории погоды
* `weather.chart.url.forecast` - URL-адрес для отображения прогноза погоды.
* `weather.html` - объект HTML с описанием погоды
* `weather.title` — Очень краткое описание
* `weather.title.short` - очень, очень короткое описание (одно слово)
* `weather.type` - Тип информации о погоде
* `weather.json` — объект JSON с определенными данными
* `value.speed.wind.forecast.0` - прогноз скорости ветра на сегодня
* `weather.state.forecast.0` - Описание погоды на сегодня
* `value.direction.wind.forecast.0` - прогноз направления ветра на сегодня в градусах
* `weather.direction.wind.forecast.0` - прогноз направления ветра на сегодня в виде текста
* `value.pressure.forecast.0` - прогноз давления на сегодня
* `value.temperature.min.forecast.0` - прогноз минимальной температуры на сегодня
* `value.temperature.max.forecast.0` - Прогноз максимальной температуры на сегодня
* `value.precipitation.forecast.0` - (`type: number, unit: %`) Прогноз вероятности осадков на сегодня
* `value.precipitation.forecast.0` - (`type: number, unit: mm`) Прогноз уровня осадков на сегодня
* `weather.title.forecast.0` - Очень краткое описание завтрашнего дня
* `value.precipitation.day.forecast.0` - Прогноз осадков на дневное время
* `value.precipitation.night.forecast.0` - Прогноз осадков на ночное время

* `date.forecast.1` - завтрашняя дата
* `weather.icon.forecast.1` - иконка завтрашнего дня
* `weather.state.forecast.1` - состояние погоды на завтра
* `значение.температура.мин.прогноз.1`
* `значение.температуры.макс.прогноз.1`
* `value.precipitation.forecast.1` - (`type: number, unit: %`) Прогноз вероятности осадков на завтра
* `value.precipitation.forecast.1` - (`type: number, unit: mm`) Прогноз уровня осадков на завтра
* `значение.направление.ветер.прогноз.1`
* `значение.скорость.ветер.прогноз.1`
* `значение.давление.прогноз.1`

## Информация
* `info.ip` - ip устройства
* `info.mac` - mac устройства
* `info.name` - имя устройства
* `info.address` - другой адрес (например, KNX)
* `info.serial` - серийный номер
* `info.firmware` - версия прошивки
* `info.hardware` - аппаратная версия
* `info.port` - tcp-порт
* `info.standby` - true, если устройство находится в режиме ожидания
* `info.status` - статус устройства
* `info.display` - информация, отображаемая на дисплее устройства
* `date.start` - строка или число
* `date.end` - строка или число

## Здоровье
`common.type=number, common.read=true, common.write=false`

* `value.health.fat` - индекс жира в организме в %
* `value.health.weight` - масса тела в кг, фунты
* `value.health.bmi` - индекс ИМТ
* `value.health.calories` - сожженные калории
* `value.health.steps` - выполненные шаги
* `value.health.bpm` - количество ударов сердца в минуту

## Другие
* `адрес`
* `url.icon` - иконка (дополнительно у каждого объекта может быть `common.icon`)
* `url.cam` - адрес веб-камеры
* `url.blank` - открыть URL в новом окне
* `url.same` - открыть URL в этом окне
* `url.audio` - URL аудиофайла
* `text.phone` - номер телефона
* `time.span` - разница во времени в мс (common.type=number), т.е. время с момента последнего обновления, продолжительность операции, время до следующей попытки, ...
* `time.interval` - значение интервала в мс (common.type=number), т.е. некоторый интервал опроса
* `time.timeout` - значение таймаута в мс (common.type=number), т.е. таймауты для запросов связи
* `chart` - массив JSON с данными диаграммы, например `[{ts: 1678575600000, val: 1}, {ts: 1678579200000, val: 2}]`

* `adapter.messagebox` (`common.type=object, common.write=true`) используется для отправки сообщений на электронную почту, pushover и другие адаптеры.
* `adapter.wakeup` (`common.type=boolean, common.write=true`) пробуждает адаптер из приостановленного режима