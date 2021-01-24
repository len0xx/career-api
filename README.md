# API «Время Карьеры»
## Общая информация

* Весь API работает по протоколу HTTPS.
* Авторизация осуществляется по протоколу OAuth2.
* Все данные доступны только в формате JSON.
* Базовый URL — `https://времякарьеры.рф/api/`

## Регистрация приложения

Для того, чтобы взаимодействовать с API «Время Карьеры», необходимо для начала зарегистрировать своё приложение на сайте «Время Карьеры». Сделать это можно по [этой ссылке](https://xn--80adjbxl0aeb4ii6a.xn--p1ai/wp-admin/admin.php?page=apps). После регистрации для дальнейшего использования необходимо сохранить пару `client_id`-`client_secret`. Эти данные необходимы для любого запроса к API.

## Авторизация пользователя

Чтобы получить `access_token` необходимо сначала авторизовать пользователя. Сделать это можно, перенаправив пользователя по [этой ссылке](https://xn--80adjbxl0aeb4ii6a.xn--p1ai/office/authorize). После того, как пользователь подтвердит доступ Вашему приложению к своим данным, он будет перенаправлен по ссылке, которую вы укажете в качестве `redirect_uri` при регистрации приложения. Вместе с этим перенаправлением в адресе в качестве GET параметра будет передан код доступа `code`, который необходимо обменять на `access_token` при помощи метода [auth](https://github.com/len0xx/career-api/blob/master/docs/auth.md).

## Доступные методы

* [auth](https://github.com/len0xx/career-api/blob/master/docs/auth.md)
* [update-token](https://github.com/len0xx/career-api/blob/master/docs/update-token.md)
* [userinfo](https://github.com/len0xx/career-api/blob/master/docs/userinfo.md)
* [get-categories](https://github.com/len0xx/career-api/blob/master/docs/get-categories.md)
* [get-vacancy](https://github.com/len0xx/career-api/blob/master/docs/get-vacancy.md)
* [get-vacancies](https://github.com/len0xx/career-api/blob/master/docs/get-vacancies.md)
* [create-vacancy](https://github.com/len0xx/career-api/blob/master/docs/create-vacancy.md)
* [edit-vacancy](https://github.com/len0xx/career-api/blob/master/docs/edit-vacancy.md)
* [delete-vacancy](https://github.com/len0xx/career-api/blob/master/docs/delete-vacancy.md)
