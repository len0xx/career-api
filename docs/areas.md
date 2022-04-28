# Получение списка населённых пунктов

Метод для получения списка населённых пунктов, существующих на «Время Карьеры»

При успешном выполнении населенные пункты возвращаются в виде массива терминов, упорядоченных в алфавитном порядке. Описание объекта "термин" можно посмотреть по ссылке — [terms](https://github.com/len0xx/career-api/blob/main/docs/terms.md)

### Для получения списка населённых пунктов необходимо выполнить запрос:
```
GET /api/areas/
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
    "areas": [
        {
            "id": 955,
            "parent": 362,
            "title": "Каменск-Уральский"
        },
        {
            "id": 1400,
            "parent": 361,
            "title": "Ковров"
        },
        {
            "id": 1187,
            "parent": 360,
            "title": "Комсомольск-на-Амуре"
        },
        {
            "id": 1405,
            "parent": 356,
            "title": "Кострома"
        },
        {
            "id": 1409,
            "parent": 370,
            "title": "Краснокаменск"
        },
        {
            "id": 1410,
            "parent": 365,
            "title": "Краснокамск"
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
* `invalid access_token` — передан несуществующий `access_token`
* `the access_token has already expired` — срок жизни токена истёк
* `this access_token is no longer available` — существует более новый токен для этого пользователя
* `account with such account_id does not exist` — пользователя с таким `id` (привязанным к `access_token`) не существует
* `invalid scope for this method` — у переданного токена нет доступа к этому методу (см. [user-authorization](https://github.com/len0xx/career-api/blob/main/docs/user-authorization.md#%D0%B2%D0%BE%D0%B7%D0%BC%D0%BE%D0%B6%D0%BD%D1%8B%D0%B5-%D0%B7%D0%BD%D0%B0%D1%87%D0%B5%D0%BD%D0%B8%D1%8F-scope))
* `could not collect the areas` — во время получения населённых пунктов на сервере произошла непредвиденная ошибка, пожалуйста, попробуйте повторить запрос позднее
