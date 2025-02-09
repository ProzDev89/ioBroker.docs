---
translatedFrom: en
translatedWarning: Если вы хотите отредактировать этот документ, удалите поле «translationFrom», в противном случае этот документ будет снова автоматически переведен
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/ru/adapterref/iobroker.iqontrol/README.md
title: ioBroker.iqontrol
hash: yPlSOWOfUmmCRavKRHYsIIn8Z9xAqmbptjwO0Apc+jk=
---
![логотип](../../../en/adapterref/iobroker.iqontrol/admin/iqontrol.png)

![Версия NPM](http://img.shields.io/npm/v/iobroker.iqontrol.svg)
![Загрузки](https://img.shields.io/npm/dm/iobroker.iqontrol.svg)
![Статус зависимости](https://img.shields.io/david/sbormann/iobroker.iqontrol.svg)
![Известные уязвимости](https://snyk.io/test/github/sbormann/ioBroker.iqontrol/badge.svg)
![NPM](https://nodei.co/npm/iobroker.iqontrol.png?downloads=true)
![Трэвис-CI](http://img.shields.io/travis/sbormann/ioBroker.iqontrol/master.svg)
![AppVeyor](https://ci.appveyor.com/api/projects/status/github/sbormann/ioBroker.iqontrol?branch=master&svg=true)

# IoBroker.iqontrol
** Тесты: **

| Linux / Mac / Windows: | Кросс-браузерная проверка: |
| --- | --- |

\ **Если вам это нравится, рассмотрите пожертвование:**

[![PayPal] (https://www.paypalobjects.com/en_US/DK/i/btn/btn_donateCC_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=LDHZMNPXKRX2N&source=url)

****

## Адаптер iqontrol для ioBroker
Быстрое веб-приложение для визуализации.

![пример](img/screenshot1.jpg) ![пример](../../../en/adapterref/iobroker.iqontrol/img/screenshot2.jpg)

Работает в любом браузере.
Вы можете сохранить его как веб-приложение на домашнем экране iOS, и оно будет выглядеть как родное приложение.
Это полностью настраиваемый.

## Тебе нужно...
* Nodejs 8 или выше
* socketIO должен быть включен в веб-адаптере

## Как пользоваться
* Начните создавать представления.

Вы можете рассматривать представления как что-то вроде страницы.

* Затем создайте устройства на этих представлениях.

У устройств есть роль, которая определяет функцию устройства, какие значки используются и так далее.
В зависимости от этой роли вы можете связать несколько состояний с устройством. Это даст устройству его функциональность.
Если вы выберете «Ссылка на другой вид» в качестве роли, вы сможете создавать ссылки на другие виды. Я предлагаю скины Ссылки на другие виды с тем же фоном, который есть у связанного вида.
Вы также можете попробовать использовать функцию автоматического создания, чтобы выбрать существующее устройство из дерева объектов iobroker. Autocreate пытается выяснить роль и сопоставить как можно больше состояний.

* После этого вы можете создать панель инструментов, которая отображается в виде нижнего колонтитула.

Панель инструментов-Entrys - это ссылки на виды.
Первая панель инструментов будет вашей «Домашней панелью» и будет загружена при запуске.

* Чтобы придать всему модный стиль, вы можете загрузить свои собственные изображения.

Вы можете использовать свои изображения в качестве фоновых изображений для представлений или для устройств.
Бесплатные встроенные демо-обои от www.pexels.com.

## Форум
Посетите [форум iobroker](https://forum.iobroker.net/topic/22039/neuer-adapter-visualisierung-iqontrol).

## URL-параметры
* Интерфейс вызывается через `` http [s]: // <url или ip iobroker>: <порт веб-адаптера> / iqontrol / index.html``
    * `` <порт веб-адаптера> `` обычно 8082
* Чтобы открыть указанный экземпляр, вы можете добавить `` namespace = iqontrol. <Номер-экземпляра> `` в качестве URL-параметра
* Чтобы открыть указанный вид в качестве домашней страницы, вы можете добавить `` home = <viewID> `` в качестве URL-параметра

**Пример:**

* `` https://192.168.1.1: 8082 / iqontrol / index.html? namespace = iqontrol.1 & home = iqontrol.1.Views.Living-Room``
    * Обратите внимание на верхний и нижний регистр

## Описание ролей и связанных состояний
Каждое устройство имеет роль, которая определяет функцию устройства. Каждая роль генерирует набор состояний, которые могут быть связаны с соответствующим состоянием io-брокера.
Если вы используете функцию автоматического создания, вы можете выбрать существующее устройство из дерева объектов io-broker. Autocreate пытается выяснить роль и сопоставить как можно больше состояний.
Это будет работать только для известных устройств. Для неизвестных устройств, а также для предоставления устройствам расширенных функций, вы можете добавить их вручную с помощью кнопки (+) - или отредактировать устройства, созданные с помощью автоматического создания.
Чтобы отредактировать роль и состояния устройства, нажмите на карандаш позади устройства. Ниже вы найдете краткое описание ролей и используемых состояний:

### Общие положения:
Каждая роль имеет следующие три состояния:

* **BATTERY** *boolean* - при значении true будет отображаться маленький значок батареи
* **ОШИБКА** *логическое* - при значении true будет отображаться маленький значок с восклицательным знаком
* **UNREACH** *логический* - при значении true будет отображаться маленький значок беспроводной сети

Почти все роли имеют состояние STATE и / или LEVEL. В большинстве случаев это представляет собой основную функцию устройства. Вы можете назначить ему состояния io-broker следующих типов:

* *boolean* - если возможно, он будет переведен в содержательный текст, такой как «вкл / выкл», «открыт / закрыт» или тому подобное. Если вы щелкнете по значку плитки, он попытается переключить логическое значение (например, чтобы включить или выключить свет). Если он не предназначен только для чтения, в диалоговом окне появится сальто-переключатель.
* *число* - будет отображаться с соответствующим ему блоком и генерировать слайдер в диалоге.
* *string* - текст для отображения
* *список значений* - будет отображаться выбранное значение. Если он не защищен от записи, в диалоговом окне появится раскрывающееся меню.
  * Технически *value-list* - это значение с соответствующим переводом-списком, определенным в объекте 'native.states' или 'common.states' точки данных:

````
"native": {
    "states": {"true": "Text for true", "false": "Text for false"},
    ...
}
````

    * Вы можете создать свой собственный список значений, добавив объект states в `` `` "native": {} `` `` часть datapoint. Это будет прочитано только iQontrol и не будет влиять на другие скрипты.
    * Объект состояния внутри части `` `` "common": {} `` `` также будет распознаваться iQontrol, но с более низким приоритетом. Если вы измените его здесь, это может повлиять на другие сценарии. Более того, он может быть перезаписан адаптером, который создал точку данных.

Однако не каждый тип имеет смысл для каждой роли. Так, например, СОСТОЯНИЕ переключателя будет в большинстве случаев булевым, чтобы его можно было переключать между включением и выключением. Строка может отображаться, но переключатель не будет работать.

### Ссылка на другой вид:
* Не имеет больше состояний
* **связанный-вид-свойство** открывается напрямую

### <img src="img/icons/switch_on.png" width="32"> Switch, <img src="img/icons/fan_on.png" width="32"> Поклонник:
* **STATE** *boolean* - отображать и устанавливать вкл / выкл
* **POWER** *number* - энергопотребление, которое будет отображаться маленьким в верхнем правом углу

### <img src="img/icons/light_on.png" width="32"> Свет:
Каждый источник света может иметь одно или оба из следующих состояний:

* **STATE** *boolean* - отображать и устанавливать вкл / выкл
* **УРОВЕНЬ** *число* - показать и установить уровень освещенности

По желанию вы можете определить следующие состояния:

* Для цветных светодиодов (HSB-цвет-пространство):
  * **HUE** * number * - цвет света от 0 до 360 ° (формат оттенка)
  * **НАСЫЩЕННОСТЬ** * число * - насыщенность света (от белого до чистого цвета)
  * **COLOR_BRIGHTNESS** * число * - яркость цветных светодиодов (это учитывается, только если на светодиодах имеются как цветные, так и белые светодиоды. Если у вас есть только один вид светодиодов, яркость контролируется УРОВНЕМ- Государственный)
* Для белых светодиодов:
  * **CT** * число * - цветовая температура света, если он имеет два оттенка белого
  * **WHITE_BRIGHTNESS** * число * - яркость белых светодиодов (это учитывается только в том случае, если свет имеет как белый, так и цветной светодиоды. Если у вас есть только один вид светодиодов, яркость контролируется УРОВНЕМ- Государственный)
* Альтернативные цветовые пространства **еще не реализованы**
  * **HUE_MILIGHT** * число * - Милайт использует другую отправную точку в оттенке цвета cirlce:

````
tHue = modulo(66 - (hue / 3.60), 100) * 2.55;
on modulo(n, m){ return ((n % m) + m) %m; }
````

  * **RGB_HUEONLY** * string * - вместо использования HUE вы можете использовать формат RGB_HUEONLY (шестнадцатеричный). В этом особом случае RGB-формат будет принимать только чистые насыщенные цвета цветового круга. Смешанный белый не допускается
  * **RGB** * string * - вместо использования HUE, SATURATION и COLOR_BRIGHTNESS вы можете использовать RGB-формат (шестнадцатеричный)
  * **RGBW** * string * - вместо использования HUE, SATURATION, COLOR_BRIGHTNESS и WHITE_BRIGHTNESS вы можете использовать RGBW-формат (шестнадцатеричный)
  * **RGBWWCW** * string * - вместо HUE, SATURATION, COLOR_BRIGHTNESS, CT и WHITE_BRIGHTNESS вы можете использовать формат RGBWWCW (шестнадцатеричный)
* Эффект-режим:
  * **EFFECT** * value-list * - эффект для воспроизведения
* **EFFECT_NEXT** *boolean* - если установлено значение true, будет воспроизводиться следующий эффект (в качестве альтернативы для устройств, которые не поддерживают список значений EFFECT)
* **EFFECT_SPEED_UP** / **EFFECT_SPEED_DOWN** *boolean* - если установлено значение true, эффект будет ускоряться вверх / вниз
* **POWER** *number* - энергопотребление, которое будет отображаться маленьким в верхнем правом углу

### <img src="img/icons/radiator.png" width="32"> Термостат:
* **SET_TEMPERATURE** *число* - цель-температура
* **ТЕМПЕРАТУРА** *число* - фактическая температура, отображаемая маленьким шрифтом в верхнем правом углу
* **ВЛАЖНОСТЬ** *число* - фактическая влажность отображается в маленьком правом верхнем углу
* **CONTROL_MODE** *список значений* - отобразить и установить режим термостата
* **WINDOW_OPENING_REPORTING** *boolean* - если true, отображается небольшое открытое окно
* **VALVE_STATES** массив имен и номеров - отображает открытие клапанов, связанных с термостатом

### <img src="img/icons/radiator.png" width="32"> Homematic Термостат:
В дополнение к обычному термостату вы можете определить:

* **PARTY_TEMPERATURE** *string* - строка в специальном формате для определения режима homematic-термостатов для вечеринки или праздника
* **BOOST_STATE** *число* - отображает оставшееся время ускорения термостатов homematic

### <img src="img/icons/temperature.png" width="32"> Датчик температуры, <img src="img/icons/humidity.png" width="32"> Датчик влажности:
* **СОСТОЯНИЕ** *число* - температура или влажность, которые будут отображаться в нижней части устройства
* **ТЕМПЕРАТУРА** *число* - температура, которая будет отображаться маленьким в верхнем правом углу
* **ВЛАЖНОСТЬ** *число* - влажность, которая будет отображаться маленьким в верхнем правом углу
* **связанный-вид-свойство** открывается напрямую

### <img src="img/icons/brightness_light.png" width="32"> Яркость-Sensor:
* **STATE** *число* - яркость, которая будет отображаться в нижней части устройства
* **BRIGHTNESS** *number* - яркость, которая будет отображаться маленьким в верхнем правом углу
* **связанный-вид-свойство** открывается напрямую

### <img src="img/icons/motion_on.png" width="32"> Датчик движения:
* **STATE** *логическое* - отображать, обнаружено движение или нет
* **связанный-вид-свойство** открывается напрямую

### <img src="img/icons/door_closed.png" width="32"> Дверь, <img src="img/icons/window_closed.png" width="32"> Окно:
* **STATE** *boolean* - отображать, открыта или закрыта дверь или окно.
  * В качестве альтернативы вы можете назначить *список значений* чтобы отобразить дополнительные состояния, такие как «наклон».
  * Вы также можете назначить *строку* для отображения любого текста, например «3 открытых окна» или «все закрыто».
* Уважайте **свойство связанных просмотров**

### <img src="img/icons/door_locked.png" width="32"> Дверь с замком:
* **STATE** *boolean* - отображать, открыта или закрыта дверь.
* **LOCK_STATE** *логический* - отображать, заблокирована или разблокирована дверь
* **LOCK_STATE_UNCERTAIN** *логическое значение* - СОСТОЯНИЕ будет отображаться курсивом, если true, чтобы показать, что точная позиция блокировки неизвестна
* **LOCK_OPEN** *boolean* - если установлено значение true, дверь полностью откроется

### <img src="img/icons/blind_middle.png" width="32"> Слепой:
* **УРОВЕНЬ** *число* - высота блайндов в процентах
* **DIRECTION** *список значений* - может быть Stop, Up и Down
* **STOP** *логическое* - если установлено значение true, слепой остановится
* **UP** / **DOWN** *boolean* - при значении true блайнд будет идти вверх / вниз (для устройств, которые используют точки данных UP и DOWN вместо LEVEL)

### <img src="img/icons/fire_on.png" width="32"> Fire-Sensor:
* **STATE** *логическое* - если true, датчик будет отображаться как сработавший
  * В качестве альтернативы вы можете назначить *список значений* чтобы отобразить дополнительные состояния, такие как «несанкционированный доступ».
  * Вы также можете назначить *строку* для отображения любого текста, например "огонь на верхнем этаже".
* **связанный-вид-свойство** открывается напрямую

### <img src="img/icons/alarm_on.png" width="32"> Тревога:
* **STATE** *логическое* - если true, датчик будет отображаться как сработавший
  * В качестве альтернативы вы можете назначить *список значений* чтобы отобразить дополнительные состояния, такие как «несанкционированный доступ».
  * Вы также можете назначить *строку* для отображения любого текста, например "огонь на верхнем этаже".

### <img src="img/icons/battery_full.png" width="32"> Батарея:
* **STATE** *число* - уровень заряда батареи в процентах
* **CHARGING** *boolean* - если true, отображается значок зарядки

### <img src="img/icons/value_on.png" width="32"> Значение:
* **СОСТОЯНИЕ** *любое* - любое допустимое состояние, которое будет отображаться (посмотрите раздел общих состояний)
* **LEVEL** *number* - создаст слайдер в диалоге

### <img src="img/icons/play_on.png" width="32"> Программа:
* **STATE** *boolean* - при значении true программа будет запущена

### <img src="img/icons/play.png" width="32"> Сцена:
* **STATE** *boolean* - отображается, если сцена активна. Если установлено значение true, сцена будет запущена

### <img src="img/icons/button.png" width="32"> Кнопка:
* **STATE** *any* - любой желаемый тип состояния
* **SET_VALUE** CONSTANT *string* - это константа (а не связанное состояние io-broker!), Которая будет назначена в STATE при нажатии кнопки

### <img src="img/icons/popup.png" width="32"> Неожиданно возникнуть:
* **STATE** *any* - может использоваться для отображения дополнительной информации
* **URL** CONSTANT *string* - этот URL будет открыт как всплывающее окно внутри всплывающего окна
* **HTML** CONSTANT *string* - эта разметка будет отображаться во всплывающем окне, если URL не указан

### <img src="img/icons/link.png" width="32"> Внешняя ссылка:
* **STATE** *any* - может использоваться для отображения дополнительной информации
* **URL** CONSTANT *string* - этот URL будет открыт

## Разработка
* Взгляните на [Принцип работы внешнего интерфейса] (Операция% 20Principle% 20of% 20Frontend.md)

****

## Changelog

### 0.0.42
* (Sebastian Bormann) Adjusted pathes of demo-files.

### 0.0.41
* (Sebastian Bormann) Major Change: The location of the uploaded userimages has changed, so the images can be accessed by backup-function of iobroker - the images will be moved to the new location automatically - please open admin-page for ALL instances and save the settings to adjust the filenames of used images automatically.
* (Sebastian Bormann) Inverted colortemperature-scale for hue-lights (now it uses the mired-scale = micro reciprocal degree-scale instead of kelvin).
* (Ansgar Schulte) Added Up and Down Buttons to Blinds.
* (Sebastian Bormann) When creating a directory it will be entered.
* (Sebastian Bormann) Added Effect-Section to Light
* (Sebastian Bormann) If a state is not set yet, a standard value will be used

### 0.0.40
* (Sebastian Bormann) Appended missing conn.js in admin-folder.

### 0.0.39
* (Sebastian Bormann) Now file-operations in admin should work (file and directory renaming and deleting).
* (Sebastian Bormann) Added Image-Popup in admin.
* (Sebastian Bormann) Renamed demo-images.

### 0.0.38
* (Sebastian Bormann) Again changes to forced touch for gained compatibility.

### 0.0.37
* (Sebastian Bormann) Some more little changes to forced touch.
* (Sebastian Bormann) Added option to open a view via url by adding 'home=<viewId>' to url-parameters.

### 0.0.36
* (Sebastian Bormann) Added compatibility for some android devices to forced touch.
* (Sebastian Bormann) Changed the way hue and ct is displayed for better compatibility to some devices.

### 0.0.35
* (Sebastian Bormann) Fixed crash of frontend, if a device has no role and added info to admin to chose a role.
* (Sebastian Bormann) Removed filtering of states in select-id-dialog for autocreate.
* (Sebastian Bormann) Further improvments of forced touch with force-indicator and hopefully a better compatibility with more devices.

### 0.0.34
* (Sebastian Bormann) Added forced touch menu (press hard or press long on unsupported devices), wich will give more room for extended features in future.
* (Sebastian Bormann) Linked Views can now be set for all roles and are available in the dialog and by a forced touch.
* (Sebastian Bormann) Added timestamp for Window, Door, Fire, Temperature, Humidity, Brightness and Motion.
* (Sebastian Bormann) Fixed issure 49 (state for role switch if type is number).

### 0.0.33
* (Sebastian Bormann) Added WINDOW_OPENING_REPORTING to thermostat and homematic-thermostat.
* (Sebastian Bormann) Fixed marquee not always starting correctly.

### 0.0.32
* (Sebastian Bormann) Added Battery.
* (Sebastian Bormann) Heaters are displayed as inactive, if set-value is at its minimum.
* (Sebastian Bormann) Added meta.user object to allow backup of user uploaded files via iobroker backup.
* (Sebastian Bormann) Added check for existance of common.role before rendering view.

### 0.0.31
* (Sebastian Bormann) Fixed some typos.
* (Sebastian Bormann) Enhanced colour-mixing of light with seperate brightness-datapoints for color and white.
* (Sebastian Bormann) Rewritten rendering of view as praparation for further enhancements.
* (Sebastian Bormann) Rewritten rendering of dialog as praparation for further enhancements.
* (Sebastian Bormann) Added option to colorize Device-Texts.

### 0.0.30
* (Sebastian Bormann) Fixed io-package.json

### 0.0.29
* (Sebastian Bormann) changed parts of the code to be backward-compatible to older browsers like ie 11.
* (Sebastian Bormann) Now its possible to define a value list for a data point under .native.states wich will have a greater priority than a value list under .common.states. 
* (Sebastian Bormann) Updated dependency for axios to 0.0.19 to fix a scurity issue.

### 0.0.28
* (Sebastian Bormann) Added datapoint POWER to switch, fan and light.
* (Sebastian Bormann) Fixed marquee for small info texts in the upper right corner at big screen sizes.
* (Sebastian Bormann) Added more options for configuring header-colors and device-colors (experimental state). Text-color ist not configurable yet.

### 0.0.27
* (Sebastian Bormann) Added marquee (scrolling text) for long states and device names (can be configured  in options). 
* (Sebastian Bormann) Added more toolbar-options. 
* (Sebastian Bormann) Enhanced handling of value lists. 
* (Sebastian Bormann) Disabled swiping when dialog is opened.

### 0.0.26
* (Sebastian Bormann) Added brightness to motion-sensor.
* (Sebastian Bormann) Added options tab. You can now configure colors of toolbar.
* (Sebastian Bormann) Fixed rendering of constants.
* (Sebastian Bormann) Resized the demo-wallpapers for faster loading.

### 0.0.25
* (Sebastian Bormann) Added motion-sensor.
* (Sebastian Bormann) Added description, how the frontend works: [Operating Principle of Frontend](Operating%20Principle%20of%20Frontend.md).
* (Sebastian Bormann) Added dialog for editing constants like SET_VALUE, URL or HTML.
* (Sebastian Bormann) Changed the way arrays are stored.
* (Sebastian Bormann) Added submit-button for values of type string.
* (Sebastian Bormann) Added saturation to hue-lights.
* (Sebastian Bormann) Better icons for color-temperature and brightness-sensor.

### 0.0.24
* (Sebastian Bormann) Fixed jittering on Safari while scrolling (was related to Pull2Refresh).
* (Sebastian Bormann) System language of iobroker will be loaded and used.

### 0.0.23
* (Sebastian Bormann) Rewrote how constant values (instead of linkedStates) are handeled - this is a requirement for further development.
* (Sebastian Bormann) Fixed Pull2Refresh on android devices / chrome.
* (Sebastian Bormann) Added external links
* (Sebastian Bormann) Added popups with iframes

### 0.0.22
* (watcherkb) Improved german translation.
* (BramTown) Improved german translation.
* (Sebastian Bormann) Short after another coming reconnect-events (<5s) are ignored now.

### 0.0.21
* (Sebastian Bormann) Added Pull2Refresh on mobile devices - reloads whole page when pulling down on homepage, otherwise only the acual view is reloaded.
* (Sebastian Bormann) Improved reloading on reconnect (hoepefully to get it finally good working on iOS 12.2).

### 0.0.20
* (Sebastian Bormann) New trial to get it working in iOS 12.2.

### 0.0.19
* (Sebastian Bormann) Improved reloading of page in new PWA-Mode of iOS 12.2.

### 0.0.18
* (Sebastian Bormann) Improved fetching of VALVE_STATES.
* (Sebastian Bormann) Changed Button Icon.
* (Sebastian Bormann) Added Loading-Spinner if disconnected.
* (Sebastian Bormann) Due to new iOS 12.2 PWA-Mode added visibility-check and connectivity-check.
* (Sebastian Bormann) Added role-icons to role-selectbox in edit device dialog.
* (Sebastian Bormann) Fixed missing value-list for states of the type string.

### 0.0.17
* (Sebastian Bormann) Changed description of slider (level/dimmer/value/height).

### 0.0.16
* (Sebastian Bormann) Role of device is displayed in devices-table.
* (Sebastian Bormann) VALVE_STATES is now editable via GUI (show opening of valves associated with a thermostat in percentage).
* (Sebastian Bormann) Added Role 'Button': You can define a constant SET_VALUE wich will be written to the ID that is linked with STATE if the button is pressed.
* (Sebastian Bormann) Rewritten parts of front-end to guarentee better compatibility. Boost-Mode for Homematic-Thermostat should work now.
* (Sebastian Bormann) Added state BOOST_STATE for Homematic-Thermostat - ability to display remaining boost-time if in boost-mode.
* (Sebastian Bormann) Added dessription of roles and corresponding states.
* (Sebastian Bormann) Temperature und Humidity-Sensors can now display a STATE at bottom of device, and both, TEMPERATURE and HUMIDITY, in small in the upper right corner.
* (Sebastian Bormann) Better handling of Auto-Create of Temperature- und Humidity-Sensors.
* (Sebastian Bormann) German translation: 'geöffnet' lower case.
* (Sebastian Bormann) Zigbee humidity and temperature added to auto-creation.
* (Sebastian Bormann) Fixed not scrollable selectbox at devices tab.

### 0.0.15
* (Sebastian Bormann) Improved check for value type of states.
* (Sebastian Bormann) Improved slider-tooltip to lower font-size at large numbers.

### 0.0 14
* (Sebastian Bormann) If role of state is not further specified, then check for role of parent object.

### 0.0.13
* (Sebastian Bormann) Doors and Windows now force true/false to be translated to opened/closed.
* (Sebastian Bormann) Double Entrys on WelcomeScreen/Overview removed.
* (Sebastian Bormann) States are now set with the correct value type.
* (Sebastian Bormann) Changed recognition of state types. I hope there are no new bugs now!

### 0.0.12
* (Sebastian Bormann) Check for unallowed chars in object names.
* (Sebastian Bormann) Check for duplicates in view names.
* (Sebastian Bormann) Level fires a slider in dialog - even when it has a state list (HUE again :)).
* (Sebastian Bormann) Added Blinds (Homematic) - please test it, i don't have one to test.

### 0.0.11
* (Sebastian Bormann) Added compatibility for edge and firefox. 
* (Sebastian Bormann) Again Hue bugfixes.
* (Sebastian Bormann) Removed Tooltip from Toolbar.

### 0.0.10
* (Sebastian Bormann) Added ColorTemperature. Hoepfully HUE works now? Can't test ist, because i do not own any hue lamp :)

### 0.0.9
* (Sebastian Bormann) Philips HUE added to autocreate (colortemp is not working yet!).  
* (Sebastian Bormann) LinkedView now also works on windows, doors and fire-sensor.
* (Sebastian Bormann) Added translation (thanks ldittmar!).

### 0.0.8
* (Sebastian Bormann) Added icons to image selectboxes.

### 0.0.7
* (Sebastian Bormann) Changed order of tabs
* (Sebastian Bormann) Autocreate for shelly should work now (i hope so, can't test it here)

### 0.0.6
* (Sebastian Bormann) Improved speed of select id and autocreate
* (Sebastian Bormann) Set filter to channel on autocreate

### 0.0.5
* (Sebastian Bormann) Bugfix: creation of many devices schould work now

### 0.0.4
* (Sebastian Bormann) Bugfix: copy device created just a reference to old object
* (Sebastian Bormann) Addes Toolbar-Icons

### 0.0.3
* (Sebastian Bormann) various bugfixes

### 0.0.2
* (Sebastian Bormann) first partly running version

### 0.0.1
* (Sebastian Bormann) initial release

## License
MIT License

Copyright (c) 2019 Sebastian Bormann

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