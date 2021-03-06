# Содержание проекта GeocodingYandex-FoliumMapExample

**Для лучшего отображения всех аутпутов и правильной работы интерактивной карты в конце, можно открыть Jupyter Notebook по ссылке: https://nbviewer.org/github/Gundeundefined1/GeocodingYandex-FoliumMapExample/blob/main/Direct%20geocoding%20with%20Yandex%20geocoder.ipynb**

## Часть 1. Прямой геокодинг (geopy.geocoders Yandex) адресов из базы, подготовка датасета для дальнейшей визуализации на карте.
  1. geopy - основная билбиотека, которая будет использоваться в проекте для прямого геокодирования с помощью API Yandex
  2. Так как прямое геокодирование большого количества адресов достаточно долгая процедура, в качестве теста, добавим оповещение в Telegramm (это позволит в цикле каждые, например, 10 000 адресов, отправлять сообщение с статусом работы)
  3. Загрузка первичной базы data_test.csv с адресами 500 строк (Публичный источник: Адресный справочник Челябинска - https://ts.domspravka.com/adres/chelyabinsk/, дополнительно поля name и birth изменены)
  4. Подключение Геокодер API Яндекс.Карт и проверка работы прямого геокодирования Яндекс API (https://yandex.ru/dev/maps/geocoder/)
  5. Применение геокодера Яндекс для получения координат адресов из загруженного списка
  6. Заполнение полей конкретными числовыми значениями координат (разделение столбца 'point' на столбцы 'latitude', 'longitude','altitude')
  
## Часть 2. Отрисовка полученных координат на карте (folium) с группами маркеров
  1. folium - основная билбиотека, которая будет использоваться в проекте для создания интерактивных карт
  2. Создание функции для формирования HTML таблиц с значениями из датафрейма (при клике по значку на карте откроется данная таблица с детальной информацией. Формат приведен для примера, реально применение всей палитры возможностей языка HTML)
  3. Создание функций для динмаической окраски значков на карте по заданным условиям (дата рождения и есть ли e-mail)
  4. Преобразование данных датафрейма в geojson для последующего использования в качестве входных данных построения карты
  5. Создание самого объекта map библиотеки folium, инициализация начальных парметров (приближение/стиль карт) и фильтров для поиска по ключевым значениям
  6. Отрисовываем на карте все элементы из geojson, в соответствии с заданными параметрами (используя функции color_change и back_color_change для цветовой индикации)
  7. Финальная визуализация карты
  
## Итог
  **Из простой базы с информацией по клиентам, содержащей только его адрес в качестве ориентира (возможно в различных форматах его написания, в т.ч. с ошибками и опечатками) на выходе получится интерактивная карта с кластеризацией отметок в группы, цветовой индикацие по желаемому параметру, дополнительными плашками с информацией по клику на значок (рис.1) и полями с поиском по конкретным значениям (рис.2).**

**Рис.1**
![image](https://user-images.githubusercontent.com/87270547/156922150-ff24c3f0-9ba5-46dd-b0ff-84b87ec41ae3.PNG)

**Рис.2**
![image](https://user-images.githubusercontent.com/87270547/156922722-b848c0d7-4812-4618-bb3f-68903eff94d0.png)
