# CurrexApp
## Тестовое приложение - "обмен валют"

Приложение реализует модель обмена валют в кассе банка.
Реализовано:
1. База данных SQL derby.
1. Web-сервис принимающий запросы по протоколу http.
1. Web-интерфейс пользователя.
1. Web-интерфейс администратора   

## Описание
При запуске база пуста, и автоматически инициализируется значениями по умолчанию. 
Для демонстрации база определена как **база в памяти**.
Изменить настройки базы можно в application.properties.

- Для инициализации на **экране справочников** в консоли администрирования нужно обновить справочник 
валют нажатием кнопки **"обновить"**. Будут потянуты данные с серверов Приватбанка и НБУ.
- Для проведения операции обмена применяется экран обмена.
Здесь есть:
  - выпадающий список валют
  - курс по выбранной валюте
  - переключатель продажа/покупка
  - 2 поля для ввода валюты и гривны соответственно.
  - кнопка обмен осуществляет операцию обмена.
- Экран справочника отображает таблицу с валютами.

  В таблице собраны данные о валютах
  - числовой код валюты
  - символьный код валюты
  - название
  - курс НБУ
  - курс покупки Приватбанка 
  - курс продажи Приватбанка

  **для администраторов** есть дополнительная кнопка обновления справочников.
- стартовый экран содержит 2 кнопки для перехода в консоль пользователя или администратора
- Экран операций.

  В таблице собраны данные о пользовательских операциях
  - дата
  - валюта покупки
  - валюта продажи
  - сумма покупки
  - сумма продажи
  - курс
  - статус **для администратора** с кнопкой удаления записи
## Реализация
- Доступ к данным реализован:
  - для клиентов через чистый jdbc
  - для администраторов через JdbcTemplate.
- Отображение страниц реализовано с использованием JSP и JSTL.
- Для демонстрации используется встроенный сервер "Tomcat"
- Для курсов валют с сервера НБУ использован XML формат данных. 
- Для курсов валют с сервера Приватбанка использован JSON формат данных. 
- Реализован механизм Spring Security на базе base auth.
## Запуск 

сборка и запуск осуществляется с помощью maven:
```maven
mvn tomcat7:run
```
