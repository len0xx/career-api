# Получение списка категорий

Метод для получения списка категорий, существующих на «Время Карьеры»

При успешном выполнении rатегории возвращаются в виде массива терминов, упорядоченных в алфавитном порядке. Описание объекта "термин" можно посмотреть по ссылке — [terms](https://github.com/len0xx/career-api/blob/main/docs/terms.md)

### Для получения списка категорий необходимо выполнить запрос:
```
POST /api/get-categories/
```

### В теле запроса необходимо передать следующие параметры:
* `client_id` — Идентификтор приложения (см. [регистрация приложения](https://xn--80adjbxl0aeb4ii6a.xn--p1ai/wp-admin/admin.php?page=apps))
* `client_secret` — Секретный код приложения (см. [регистрация приложения](https://xn--80adjbxl0aeb4ii6a.xn--p1ai/wp-admin/admin.php?page=apps))
* `access_token` — Токен доступа (см. [получение токена](https://github.com/len0xx/career-api/blob/main/docs/auth.md))

### Пример запроса
```javascript
{
    "client_id": 0,
    "client_secret": "b35ef4fe21294ac5",
    "access_token": "8248D5F9C68BF23F9C296D3B10119F01"
}
```

### Пример ответа:
```javascript
{
    "success": true,
    "categories": [
        {
            "id": 673,
            "title": "HR"
        },
        {
            "id": 41,
            "title": "Административный персонал"
        },
        {
            "id": 148,
            "title": "Аудит"
        }
    ]
}
```

## Ошибки

В случае ошибки будет выдан соответствующий ответ с описанием проблемы. Например:
```javascript
{
    "success": false,
    "error": "invalid access_token"
}
```
Такой ответ говорит о том, что был передан некорректный `access_token`

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
