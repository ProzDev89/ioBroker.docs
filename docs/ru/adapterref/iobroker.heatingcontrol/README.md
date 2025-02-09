---
translatedFrom: en
translatedWarning: Если вы хотите отредактировать этот документ, удалите поле «translationFrom», в противном случае этот документ будет снова автоматически переведен
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/ru/adapterref/iobroker.heatingcontrol/README.md
title: ioBroker.HeatingControl
hash: mCz3joKc77hO5pDqRqHgxexPv80ZNFVEKdMMnas3Ozo=
---
![логотип](../../../en/adapterref/iobroker.heatingcontrol/admin/heatingcontrol.png)

![Количество установок](http://iobroker.live/badges/heatingcontrol-stable.svg)
![Версия NPM](https://img.shields.io/npm/v/iobroker.heatingcontrol.svg)
![Загрузки](https://img.shields.io/npm/dm/iobroker.heatingcontrol.svg)
![тесты](https://travis-ci.org/rg-engineering/ioBroker.heatingcontrol.svg?branch=master)
![NPM](https://nodei.co/npm/iobroker.heatingcontrol.png?downloads=true)

# IoBroker.HeatingControl
Адаптер для управления термостатами.

Особенности:

* Контроль заданных уровней температуры всех термостатов в соответствии с расписанием
* Настройка нескольких периодов отопления для каждого дня и ночи
* Поддерживает различные термостаты homematic и max! Cube
* поддерживает несколько профилей (чтобы сделать)
* Если нет прямой связи между термостатом и приводом, привод можно отключить непосредственно от адаптера.
* В настоящее время привод отключается непосредственно при достижении заданного значения температуры. Как только заданная температура станет ниже фактической температуры, привод будет включен. (Для этого: реализовать улучшенный контроль)
* поддерживается до двух приводов
* Термостат и привод автоматически определяются для каждой комнаты. Для этого используется функция (например, «нагрев»).
* Комнаты могут быть исключены из интерфейса администратора, если комната содержит термостат, но не должна контролироваться
* Пример визуализации будет предоставлен позже

## Настройки
### Главный
* Использовать актеры =, если вы хотите управлять приводами напрямую от адаптера. На всякий случай нет прямой связи между термостатом и приводом.
* Gewerk = функция, которая будет использоваться для обнаружения термостатов и приводов на комнату
* Путь к термостатам = путь к термостатам, например "Гм-rpc.0."
* Путь к актерам = путь объекта к приводам, например, "Гм-rpc.0."
* часовой пояс = для использования cron для настройки заданий cron
* удалить все = удалить все настройки комнаты при открытии администратора. После этого начнется новое сканирование номеров

### Профиль
* Тип профиля = в данный момент только понедельник по воскресенье является сторонником. Другие будут реализованы в ближайшее время
* количество профилей = если вам нужно больше, то в профиле увеличьте это значение. Затем вы можете выбрать, какой профиль будет использоваться.
* количество периодов = определить, сколько ежедневных секций с различной температурой вам нужно. Чем больше вы установите, тем больше точек данных будет создано. Лучше использовать низкое значение (например, 5)
* public holyday = если вы отметите это, вы получите отдельную корректировку для государственных праздников (еще не реализовано)

### Устройства
* список всех комнат с термостатами и приводами. Вы можете отключить комнату здесь. Вы не должны изменять настройки для термостатов или приводов, потому что это будет перезаписано при следующем запуске администратора.

## Требования
* Требуется версия узла 8 или выше

## Проблемы и запросы функций
* Если вы столкнулись с какими-либо ошибками или у вас есть запросы на функции для этого адаптера, пожалуйста, создайте проблему в разделе проблем GitHub адаптера на [github] (https://github.com/rg-engineering/ioBroker.heatingcontrol/issues ). Любая обратная связь приветствуется и поможет улучшить этот адаптер.

## Changelog

### 0.0.5 (2019-07-08)
* (René) support for max!cube thermostats

### 0.0.4 (2019-06-23)
* (René) debugging

### 0.0.3 (2019-06-02)
* (René) ready to publish

### 0.0.2 (2019-05-19)
* (René) actuator handling added

### 0.0.1 (2019-04-27)
* (René) initial release

## License

Copyright (C) <2019>  <info@rg-engineering.eu>

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.