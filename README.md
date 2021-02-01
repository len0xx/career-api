# API «Время Карьеры»
## Общая информация

* Весь API работает по протоколу HTTPS.
* Авторизация осуществляется по протоколу OAuth2.
* Все данные доступны только в формате JSON.
* Базовый URL — `https://времякарьеры.рф/api/`

## Регистрация приложения

Для того, чтобы взаимодействовать с API «Время Карьеры», необходимо для начала зарегистрировать своё приложение на сайте «Время Карьеры». Сделать это можно по [этой ссылке](https://xn--80adjbxl0aeb4ii6a.xn--p1ai/wp-admin/admin.php?page=apps). После регистрации для дальнейшего использования необходимо сохранить пару `client_id`-`client_secret`. Эти данные необходимы для любого запроса к API.

## Авторизация пользователя

Чтобы получить `access_token` необходимо сначала авторизовать пользователя. Сделать это можно, перенаправив пользователя по специальной ссылке. 

Подробнее об авторизации пользователей тут — [user-authorization](https://github.com/len0xx/career-api/blob/main/docs/user-authorization.md)

## Доступные методы

* [auth — Получить access_token](https://github.com/len0xx/career-api/blob/main/docs/auth.md)
* [update-token — Обновить access_token](https://github.com/len0xx/career-api/blob/main/docs/update-token.md)
* [userinfo — Получить основную информацию о пользователе](https://github.com/len0xx/career-api/blob/main/docs/userinfo.md)
* [get-categories — Получить список категорий вакансий](https://github.com/len0xx/career-api/blob/main/docs/get-categories.md)
* [get-cities — Получить список городов](https://github.com/len0xx/career-api/blob/main/docs/get-cities.md)
* [get-regions — Получить список регионов](https://github.com/len0xx/career-api/blob/main/docs/get-regions.md)
* [get-vacancy — Получить конкретню вакансию по ID](https://github.com/len0xx/career-api/blob/main/docs/get-vacancy.md)
* [get-vacancies — Получить список вакансий компании авторизованного пользователя](https://github.com/len0xx/career-api/blob/main/docs/get-vacancies.md)
* [create-vacancy — Создать вакансию](https://github.com/len0xx/career-api/blob/main/docs/create-vacancy.md)
* [edit-vacancy — Редактировать вакансию](https://github.com/len0xx/career-api/blob/main/docs/edit-vacancy.md)
* [delete-vacancy — Удалить вакансию](https://github.com/len0xx/career-api/blob/main/docs/delete-vacancy.md)
