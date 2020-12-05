## Развертывание энвайронмент для работы с БД с помощью docker-compose

Разветывание инфраструктыры для локальной работы с базой данных с помощью docker-compose.

## Поднятие инфарструктуры `docker-compose up -d`

Создает **persisted volumes** персистентный сервис для работы с БД - PostgreSQL, а также management tools для работы с ним, которые биндится на порты:
 - PostgreSQL
    - 5432:5432
 - pgAdmin 4
	- 16543:80

Если при выполнении docker-compose up -d появляется ошибка подключения (no route to host), то необходимо выполнить:
1. сделать `docker network prune`
2. `docker-compose pull`
3. а потом `docker-compose up -d`


## Отключение `docker-compose down`

Порты свободны, но **persisted volumes** остаются.

##  Проверка подключения

После успешного запуска проверяем подключение к серверу:
1. Заходим в админку pgAdmin по адресу http://localhost:16543/ (user\password)
2. Добавляем сервер: Servers > Create > Server...
3. В закладке Connection заполняем параметры подключения:
 - креды (user\password)
 - порт (указан по умолчанию - 5432)
 - имя (postgres) или адрес хоста (можно посмотреть в соответствующем контейнере).