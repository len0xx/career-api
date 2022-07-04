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
* [auth/update-token — Обновить access_token](https://github.com/len0xx/career-api/blob/main/docs/auth-update-token.md)
* [userinfo — Получить основную информацию о пользователе](https://github.com/len0xx/career-api/blob/main/docs/userinfo.md)
* [categories — Получить список категорий вакансий](https://github.com/len0xx/career-api/blob/main/docs/categories.md)
* [areas — Получить список населённых пунктов](https://github.com/len0xx/career-api/blob/main/docs/areas.md)
* [response/list — Получить список откликов на вакансии компании авторизованного пользователя](https://github.com/len0xx/career-api/blob/main/docs/response-list.md)
* [vacancy/create — Создать вакансию](https://github.com/len0xx/career-api/blob/main/docs/vacancy-create.md)
* [vacancy/edit — Редактировать вакансию](https://github.com/len0xx/career-api/blob/main/docs/vacancy-edit.md)
* [vacancy/get — Получить конкуртную вакансию](https://github.com/len0xx/career-api/blob/main/docs/vacancy-get.md)
* [vacancy/delete — Удалить вакансию](https://github.com/len0xx/career-api/blob/main/docs/vacancy-delete.md)
* [vacancy/list — Получить все вакансии компании](https://github.com/len0xx/career-api/blob/main/docs/vacancy-list.md)
