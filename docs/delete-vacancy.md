# Удаление вакансии

Метод для удаления конкретной вакансии на сайте «Время Карьеры», получаемой по её `ID`

Возвращает только статус выполнения (true|false)

### Для получения вакансии необходимо выполнить запрос:
```
POST /api/delete-vacancy/
```

### В теле запроса необходимо передать следующие параметры:
* `client_id` — Идентификтор приложения (см. [регистрация приложения](https://xn--80adjbxl0aeb4ii6a.xn--p1ai/wp-admin/admin.php?page=apps))
* `client_secret` — Секретный код приложения (см. [регистрация приложения](https://xn--80adjbxl0aeb4ii6a.xn--p1ai/wp-admin/admin.php?page=apps))
* `access_token` — Токен доступа (см. [получение токена](https://github.com/len0xx/career-api/blob/main/docs/auth.md))
* `vacancy_id` — ID вакансии, которую Вы хотите удалить (целое число)

### Пример запроса
```javascript
{
    "client_id": 0,
    "client_secret": "b35ef4fe21294ac5",
    "access_token": "8248D5F9C68BF23F9C296D3B10119F01"
    "vacancy_id": 56560
}
```

### Пример ответа:
```javascript
{ "success": true }
```

## Ошибки

В случае ошибки будет выдан соответствующий ответ с описанием проблемы. Например:
```javascript
{
    "success": false,
    "error": "invalid vacancy_id"
}
```
Такой ответ говорит о том, что вакансия с таким `vacancy_id` не существует

### Возможные ошибки
* `empty request` — получено пустое тело запроса
* `insufficient arguments passed` — не передан хотя бы один из обязательных параметров
* `invalid client_id` — передан несуществующий `client_id`
* `wrong client_secret` — передан некорректный `client_secret` (неподходящий для переданного `client_id`)
* `wrong redirect_uri` — некорректный `redirect_uri` (не совпадает с тем, что был указан при регистрации приложения)
* `invalid grant_type` — значение `grant_type` не равно `authorization_code`
* `invalid code`— передан несуществующий `code`
* `the code has already expired` — у переданного `code` истёк срок жизни
* `the code has already been used. you can not use it again` — переданный `code` уже был использован
* `invalid account_id` — очень редкая ошибка, возникает в том случае, если аккаунт пользователя на момент запроса уже не существует
* `the server could not create the access_token, please try again` — во время создания `access_token` на сервере произошла непредвиденная ошибка, попробуйте повторить запрос позднее
