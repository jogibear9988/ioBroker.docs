---
lastChanged: 24.01.2022
translatedFrom: de
translatedWarning: Если вы хотите отредактировать этот документ, удалите поле «translationFrom», в противном случае этот документ будет снова автоматически переведен
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/ru/basics/roles.md
title: Роли точек данных
hash: MLon33fkDPXEUvl6ebdPNQ3ihE1hkWlkVAqvJrZe6UA=
---
# Роли точек данных
Для объектов типа `state` свойство `common.role` должно быть установлено на одну из ролей, определенных в списке ниже.
Информация о роли является очень важной информацией и позволяет адаптерам визуализации и интеллектуального помощника распознавать функцию объекта, а также то, как он связан с другими объектами в том же канале, устройстве или папке.

Пример: RGB-лампа может иметь следующие три объекта (или более) с разными ролями, которые принадлежат друг другу:

* `switch` - (вкл./выкл.)
* `level.color.rgb` с цветовым кодом лампы #RRGGBB
* `level.brightness` со значением яркости

См. [репозиторий детектора типа](https://github.com/ioBroker/ioBroker.type-detector/blob/master/DEVICES.md) для различных шаблонов устройств, используемых для обнаружения с обязательными и необязательными объектами и их ролями.

## Общий
* `state` - очень общее назначение, используется, когда роль элемента данных неизвестна.
* `текст` `common.type = строка`
* `text.url` `common.type = string` val содержит URL-адрес для использования в якоре, iframe или img
* `html` `common.type=string`
* `json` `common.type = строка`
* `список` `common.type = массив`
* `date` `common.type = string` - анализируется строкой `new Date(ddd)`
* `дата` `common.type = число` - `секунды эпохи * 1000`

## Датчик (логический, только для чтения)
`common.type=boolean, common.write=false`

* `sensor.window` - окно открыто-`true` или закрыто-`false`
* `sensor.door` - дверь открыта-`true` или закрыта-`false`
* `sensor.alarm` - некоторые общие тревоги
* `sensor.alarm.flood` - утечка воды
* `sensor.alarm.fire` - Датчик пожара
* `sensor.alarm.secure` - открыта дверь, открыто окно или обнаружено движение при включенной тревоге.
* `sensor.alarm.power` - Нет питания (`voltage = 0`)
* `sensor.light` - обратная связь от лампы, что она горит
* `sensor.lock` - текущее положение замка
* `sensor.motion` - датчик движения
* `sensor.rain` - Обнаружен дождь
* `sensor.noise` - обнаружен шум

## Ключи (логические, только запись)
`common.type=boolean, common.write=true, common.read=false`

* `кнопка`
* `кнопка.long`
* `button.stop` - например, слепая остановка,
* `кнопка.стоп.наклон`
* `кнопка.старт`
* `кнопка.открыть.дверь`
* `кнопка.окно.открыть`
* `кнопка.открыть.блайнд`
* `кнопка.открыть.наклон`
* `кнопка.закрыть.жалюзи`
* `кнопка.закрыть.наклон`
* `кнопка.режим`*
* `кнопка.режим.авто`
* `кнопка.режим.ручной`
* `кнопка.режим.тихий`

## Ключи как датчики
`common.type=boolean, common.write=false, common.read=true`

* `кнопка` - разница в том, что `common.write=false`. Пожалуйста, избегайте этой роли и используйте `button.press` или `button.long`.
* `кнопка.long`
* `кнопка.нажмите`

## Значения (числа, только для чтения)
`common.type=number, common.write=false`

* `значение`
* `value.window` (`common.states={"0": "ЗАКРЫТО", "1": "НАКЛОН", "2": "ОТКРЫТО"}`) Важно (`ЗАКРЫТО/НАКЛОНЕНО/ ОТКРЫТО" ) Значения могут отличаться.
* `value.temperature` (`common.unit='°C' или '°F' или 'K'')
* `значение.влажность`
* `value.brightness` - яркость (единица измерения: люкс, )
* `значение.мин`
* `value.max`
* `значение.по умолчанию`
* `value.battery` - уровень заряда батареи
* `value.valve` - уровень клапана
* `value.time` - getTime() объекта Date()
* `value.interval` (common.unit='sec') - интервал в секундах (может быть 0,1 или меньше)
* ~~value.date (common.type=string) - дата в формате 2015.01.01 (без времени)~~
* ~~value.datetime (common.type=string) - дата и время в системном формате~~
* `value.gps.longitude` - координаты долготы GPS
* `value.gps.latitude` - Широта GPS
* `value.gps.elevation` - высота GPS
* `value.gps` - долгота и широта вместе, например, "5,56;43,45"
* `value.gps.accuracy` - точность текущего измерения GPS
* `value.gps.radius` - радиус текущего измерения GPS
* `value.power` - фактическая мощность (единица измерения = Вт или кВт)
* `value.power.consumption` - потребление энергии (единица измерения=Втч или кВтч)
* `value.power.reactive` - реактивная мощность (единица измерения = ВАр)
* `value.direction` - (common.type=число ~~или строка~~, указывает вверх/вниз, влево/вправо, 4-позиционный переключатель, направление ветра, ...)
* `value.curtain` - текущее положение шторки
* `value.blind` - текущее положение жалюзи (`max=полностью открыто, min=полностью закрыто`)
* `value.tilt` - текущая позиция наклона (`max = полностью открыто, min = полностью закрыто`)
* `value.lock` - текущая позиция замка
* `value.speed` - скорость ветра
* `значение.давление` - (единица измерения: мбар)
* `значение.расстояние`
* `значение.расстояние.видимость`
* `value.severity` - некоторая серьезность (можно указать состояния), чем выше, тем важнее
* `value.warning` - некоторые предупреждения (состояния можно указать), чем выше, тем важнее
* `value.sun.elevation` - высота солнца в °
* `value.sun.azimuth` - азимут солнца в °
* `value.voltage` - напряжение в вольтах, `unit=V`
* `value.current` - ток в амперах, `unit=A`
* `value.fill` - уровень заполнения, `unit=l,ml,m3,%`
* `value.blood.sugar` - значение сахара в крови, `unit=mmol,mgdl`

## Индикаторы (логические, только для чтения)
`common.type=boolean, common.write=false`

Разница между *индикаторами* и *сенсорами* заключается в том, что индикаторы отображаются в виде маленького значка. Датчики как реальная ценность.
Так что индикатор не должен быть один в канале. Это должен быть еще один важный статус в канале.

* `индикатор`
* `indicator.working` — указывает, что целевая система что-то делает, например открывает жалюзи или открывает замки.
* `indicator.reachable` — Когда устройство подключено к сети
* `indicator.connected` - используется только для экземпляров. Используйте `indicator.reachable` для устройств
* `indicator.maintenance` - отображает системные предупреждения/ошибки, аварийные сигналы, сервисные сообщения, разряд батареи и т.п.
* `indicator.maintenance.lowbat`
* `indicator.maintenance.unreach`
* `indicator.maintenance.alarm`
* `indicator.lowbat` - верно, если батарея разряжена
* `indicator.alarm` - как и Indicator.maintenance.alarm
* `indicator.alarm.fire` - Обнаружен пожар
* `indicator.alarm.flood` - Обнаружен флуд
* `indicator.alarm.secure` - дверь или окно открыты
* `indicator.alarm.health` - проблемы со здоровьем

## Уровень (числа, чтение-запись)
С помощью **Уровней** вы можете контролировать или устанавливать числовое значение.

`common.type=number, common.write=true`

* `уровень`
* `level.co2` - качество воздуха 0-100%
* `level.dimmer` - яркость также уменьшается
* `level.blind` - установить положение жалюзи (max = полностью открыто, min = полностью закрыто)
* `level.temperature` - установить желаемую температуру
* `level.valve` - уставка положения клапана
* `уровень.цвет.красный`
* `уровень.цвет.зеленый`
* `уровень.цвет.синий`
* `level.color.white` - rgbW
* `level.color.hue` - цвет в ° `0-360; 0=красный, 120=зеленый, 240=синий, 360=красный (циклический)`
* `уровень.цвет.насыщенность`
* `level.color.rgb` - шестнадцатеричный цвет, например `#rrggbb`
* `уровень.цвет.яркость`
* `level.color.temperature` - цветовая температура в K° `2200° теплый белый, 6500° холодный белый`
* `уровень.таймер`
* `level.timer.sleep` - таймер сна. 0 - выключено или в минутах
* ...
* `level.volume` - (`min=0, max=100`) - объем, но min, max могут отличаться. минимум < максимум
* `level.volume.group` - (`min=0, max=100`) - громкость, для группы устройств
* `level.curtain` - Установить положение шторы
* `level.tilt` - установить положение наклона жалюзи (max = полностью открыто, min = полностью закрыто)

## Переключатель (логический, чтение-запись)
Переключатель управляет логическим устройством (`true = ON, false = OFF`)

`common.type=boolean, common.write=true`

* `переключатель`
* `switch.lock` - блокировка (`true - открыть блокировку, false - закрыть блокировку`)
* `switch.lock.door` - дверной замок
* `switch.lock.window` - блокировка окна
* `switch.mode.boost` - Термостат запускает/останавливает режим форсирования
* `switch.mode.party` - запуск/остановка режима вечеринки термостата
* `switch.power` - вкл/выкл термостат или кондиционер
* `switch.light`
* `switch.comfort` - комфортный режим
* `переключатель.включить`
* `switch.power` - включение/выключение питания
* `switch.mode`*
* `switch.mode.auto` - включение/выключение автоматического режима
* `switch.mode.manual` - включение/выключение ручного режима
* `switch.mode.silent` - вкл/выкл беззвучный режим
* `switch.mode.moonlight` - включение/выключение режима лунного света
* `switch.mode.color` - включение/выключение цветового режима
* `switch.gate` - закрывает (false) или открывает (true) ворота

## Кондиционер или термостат
* `level.mode.fan` - `АВТО, ВЫСОКИЙ, НИЗКИЙ, СРЕДНИЙ, ТИХИЙ, ТУРБО`
* `level.mode.swing` - `АВТО, ГОРИЗОНТАЛЬНО, СТАЦИОНАРНО, ВЕРТИКАЛЬНО`
* `level.mode.airconditioner` - кондиционер: `AUTO, COOL, DRY, ECO, FAN_ONLY, HEAT, OFF`, термостат отопителя: `AUTO, MANUAL, VACATION`,
* `level.mode.thermostat` - термостат: `AUTO, MANUAL, VACATION`,

 В дополнение к этим состояниям для сопоставления кондиционера обычно требуются `level.temperature` и `switch.power`.

TODO: Подумайте об ионизации и осцилляции.

## Пылесос
* `level.mode.cleanup` - перечисление `AUTO, ECO, EXPRESS, NORMAL, QUIET`. Требуются только «АВТО» и «НОРМАЛЬНЫЙ».
* `level.mode.work` - перечисление `AUTO, FAST, MEDIUM, SLOW, TURBO`. Необязательное состояние.
* `value.water` - уровень воды 0-100%.
* `value.waste` - уровень мусорного бака 0-100%. (0% - пусто, 100% - заполнено)
* `indicator.maintenance.waste` - мусорка тупая.
* `value.state` - `ДОМ, ЧИСТКА, ПАУЗА` и так далее.

В дополнение к этим состояниям обычно требуются `switch.power` для связывания пылесоса. `switch.power` в этом случае работает как: `true` — чисто, `false` — домой.
Дополнительные `value.battery` и

## Цель
* `switch.gate` - закрывает (false) или открывает (true) ворота (обязательно)
* `value.position` - положение ворот в процентах (100% открыто, 0% - закрыто)
* `value.gate` - то же, что и `value.position`
* `button.stop` - остановить движение ворот

## Средства массовой информации
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
* `media.state` - ['воспроизведение','стоп','пауза'] или [0 - пауза, 1 - воспроизведение, 2 - остановка] или [true - воспроизведение/false - пауза]
* `медиа.артист`
* `медиа.альбом`
* `медиа.название`
* `медиа.название.следующий`
* `media.cover` - URL обложки
* `media.cover.big` - URL большой обложки
* `media.cover.small` - крошечный URL обложки
* `media.duration.text` - например, "2:35"
* `media.duration` - (`common.type=число`) секунд
* `media.elapsed.text` - например, "1:30"
* `media.elapsed` - (`common.type=число`) секунд
* `media.broadcastDate` - (`common.type=string`) дата трансляции
* `media.mute` - (`common.type=boolean`) true означает отключение звука
* `media.season` - (`common.type=string`) номер сезона (важно, чтобы тип действительно был "string", чтобы можно было показать отсутствующий сезон с помощью "")
* `media.episode` - (`common.type=string`) номер эпизода (важно, чтобы тип действительно был "string", чтобы можно было указать отсутствующий эпизод с помощью "")
* `media.mute.group` - (`common.type=boolean`) Группа устройств отключения звука
* `media.tts` - Преобразование текста в речь
* `media.bitrate` - кбит/с
* `media.genre` - жанр песни
* `media.date` - песня года
* `media.track` - (`common.type=string`) идентификатор текущей воспроизводимой дорожки [0 - ~] (важно, чтобы тип действительно был `string`, чтобы можно было указать отсутствующую дорожку с помощью "".
* `media.playid` - идентификатор трека медиаплеера
* `media.add` - добавить текущий плейлист
* `media.clear` - очистить текущий плейлист (только запись)
* `media.playlist` - массив json, например
* `media.url` - URL для воспроизведения или текущий URL
* `media.url.announcement` - URL для воспроизведения объявления
* `media.jump` - количество элементов для перехода в плейлист (может быть отрицательным)
* `media.content` - тип воспроизводимого медиа, например аудио/mp3
* `media.link` - состояние с текущим файлом
* `media.input` - номер или строка входа (AUX, AV, TV, SAT, ...)
* `level.bass` - уровень баса
* `level.treble` - уровень высоких частот
* `switch.power.zone` - зона мощности

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
* `value.temperature` - Текущая температура
* `value.temperature.windchill` - Фактическое охлаждение ветром
* `value.temperature.dewpoint` - Текущая точка росы
* `value.temperature.feelslike` - Фактическая температура "на ощупь"
* `value.temperature.min` - Минимальная температура за последние 24 часа
* `value.temperature.max` - Максимальная температура за последние 24 часа
* `value.humidity` - фактическая или средняя влажность
* `value.humidity.min` - фактическая влажность
* `value.humidity.max` - фактическая влажность
* `value.speed.wind` - текущая или средняя скорость ветра
* `value.speed.max.wind` - максимальная скорость ветра за последние 24 часа
* `value.speed.min.wind` - минимальная скорость ветра за последние 24 часа
* `value.speed.wind.gust` - фактическая скорость порыва ветра
* `value.direction.wind` - текущее или среднее направление ветра в градусах
* `value.direction.max.wind` - текущее направление ветра в градусах
* `value.direction.min.wind` - текущее направление ветра в градусах
* `weather.direction.wind` - текущее или среднее направление ветра в виде текста, например, NNW
* `date` - текущая дата или дата последнего чтения информации
* `date.sunrise` - Рассвет на сегодня
* `date.sunset` - закат на сегодня
* `dayofweek` - день недели в виде текста
* `location` - текстовое описание местоположения (например, адрес)
* `weather.icon` - Текущий URL значка статуса на данный момент
* `weather.icon.wind` - Текущий URL значка ветра на данный момент
* `weather.icon.name` - Текущее название значка статуса
* `weather.state` - Текущее описание погоды
* `value.precipitation` - (`type: number, unit: mm`) Количество осадков за последние 24 часа дождь/снег (осадки сегодня для снега или дождя)
* `value.precipitation.hour` - Фактические осадки за последний час
* `value.precipitation.today` - Текущее количество осадков за сегодня (до 0:00)
* `value.precipitation.chance` - Фактическая вероятность осадков за сегодня
* `value.precipitation.type` - Текущий тип осадков за сегодня. (`Тип: Число`) Состояния: 0 - НЕТ, 1 - ДОЖДЬ, 2 - СНЕГ, 3 - ГРАД
* `value.radiation` - Фактическое солнечное излучение
* `value.uv` - Фактическое значение UV
* `value.clouds` - облака на небе. 0% - облаков нет, 100% - много облаков.
* `value.rain` - Фактическое количество осадков за последние 24 часа.
* `value.rain.hour` - Фактическое количество дождя за последний час
* `value.rain.today` - Текущее количество дождя на сегодня (до 0:00)
* `value.snow` - Фактический уровень снега за последние 24 часа
* `value.snow.hour` - Фактический уровень снега за последний час
* `value.snow.today` - Текущий уровень снега на сегодня (до 0:00)
* `value.snowline` - Фактическая линия снега в метрах
* `weather.chart.url` - URL-адрес графика истории погоды.
* `weather.chart.url.forecast` - URL-адрес для отображения прогноза погоды.
* `weather.html` - объект HTML с описанием погоды
* `waether.title` - Очень краткое описание
* `weather.title.short` — Очень-очень короткое описание (одно слово)
* `weather.type` - тип информации о погоде
* `weather.json` — объект JSON с определенными данными
* `value.speed.wind.forecast.0` - прогноз скорости ветра на сегодня
* `weather.state.forecast.0` - описание погоды на сегодня
* `value.direction.wind.forecast.0` - Прогноз направления ветра на сегодня в градусах
* `weather.direction.wind.forecast.0` - Текущий прогноз направления ветра в виде текста
* `value.pressure.forecast.0` - прогноз давления на сегодня
* `value.temperature.min.forecast.0` - прогноз минимальной температуры на сегодня
* `value.temperature.max.forecast.0` - Прогноз максимальной температуры на сегодня
* `value.precipitation.forecast.0` - (`type: number, unit: %`) Прогноз вероятности осадков на сегодня
* `value.prepitation.forecast.0` - (`type: number, unit: mm`) Прогноз уровня осадков на сегодня
* `weather.title.forecast.0` - Очень краткое описание завтрашнего дня
* `value.precipitation.day.forecast.0` - Прогноз осадков на день
* `value.precipitation.night.forecast.0` - прогноз осадков на ночь

* `date.forecast.1` - завтрашняя дата
* `weather.icon.forecast.1` - иконка на завтра
* `weather.state.forecast.1` - Состояние погоды на завтра
* `значение.температура.мин.прогноз.1`
* `значение.температура.мин.прогноз.1`
* `value.prepitation.forecast.1` - (`type: number, unit: %`) Прогноз вероятности осадков на завтра
* `value.prepitation.forecast.1` - (`type: number, unit: mm`) Прогноз уровня осадков на завтра
* `значение.направление.ветер.прогноз.1`
* `значение.скорость.ветер.прогноз.1`
* `значение.давление.прогноз.1`

## Информация
* `info.ip` - IP устройства
* `info.mac` — Mac устройства
* `info.name` - имя устройства
* `info.address` - другой адрес (например, KNX)
* `info.serial` - серийный номер
* `info.firmware` - версия прошивки
* `info.hardware` - аппаратная версия
* `info.port` - порт TCP
* `info.standby` - true, если устройство находится в режиме ожидания
* `info.status` - статус устройства
* `info.display` - Информация, отображаемая на дисплее устройства
* `date.start` - строка или число
* `date.end` - строка или число

## Здоровье
`common.type=number, common.read=true, common.write=false`

* `value.health.fat` - индекс жира в организме в %
* `value.health.weight` - масса тела в кг, фунты
* `value.health.bmi` - индекс ИМТ
* `value.health.calories` - сожженные калории
* `value.health.steps` - выполненные шаги
* `value.health.bpm` - удары сердца в минуту

## Другой
* `адрес`
* `url.icon` - иконка (кроме того, любой объект может иметь `common.icon`)
* `url.cam` - URL веб-камеры
* `url.blank` - открыть URL в новом окне
* `url.same` - Открыть URL в этом окне
* `url.audio` - URL аудиофайла
* `text.phone` - номер телефона