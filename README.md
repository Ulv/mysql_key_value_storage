# Хранилище key/value на mysql.

Просто хранилище. Может испольлзоваться как хранилище для сессий

Идея:

- использовать табл. mysql для хранения key/value
- engine таблицы - MEMORY или InnoDB (указ. в конструкторе)
- в случае MEMORY - работать непосредственно с табл (get/set).
- в случае InnoDB - в конструкторе читаем все записи в массив,
работаем с ним, в деструкторе пишем все назад в табл. INSERT'ы
завернуты в транзакции.

!!! В mysql дефолтное ограничение по размеру табл. MEMORY - 16Mb !!!