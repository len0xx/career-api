# Получение access_token

Метод для обмена `code` на `access_token`

### Для получения токена доступа необходимо выполнить запрос:
```
POST /api/auth/
```

### В теле запроса необходимо передать следующие параметры:
* `client_id` — Идентификтор приложения (см. [регистрация приложения](https://xn--80adjbxl0aeb4ii6a.xn--p1ai/wp-admin/admin.php?page=apps))
* `client_secret` — Секретный код приложения (см. [регистрация приложения](https://xn--80adjbxl0aeb4ii6a.xn--p1ai/wp-admin/admin.php?page=apps))
* `grant_type = authorization_code`
* `redirect_uri` — Адрес, на который пользователь будет перенаправлен после того как подтвердит авторизацию
* `code` — Код, который будет выдан после того, как пользователь подвердит авторизацию

### Пример запроса
```javascript
{
    "client_id": 0,
    "client_secret": "b35ef4fe21294ac5",
    "grant_type": "authorization_code",
    "redirect_uri": "https://len0xx.space/authorize/success.php",
    "code": "0F105F4A110ECB23"
}
```

### Пример ответа:
```javascript
{
    "success": true,
    "access_token": "CDF0EF87990394A8D5A7C7CA7FB80349", 
    "refresh_token": "4897FDEC0898880C8156B85666BD4EF3",
    "account_id": 44957
}
```

Данный `access_token` имеет срок жизни, равный **одному часу** с момента выдачи. При повторном запросе ранее выданный токен **отзывается** и выдается новый. `refresh_token` имеет срок жизни = один месяц, после истечения этого срока полученный `access_token` будет нельзи обновить.

## Ошибки

В случае ошибки будет выдан соответствующий ответ с описанием проблемы. Например:
```javascript
{
    "success": false,
    "error": "the code has already expired"
}
```
Такой ответ говорит о том, что срок жизни токена истёк и необходимо обновить этот токен с помощью [update-token](https://github.com/len0xx/career-api/blob/main/docs/update-token.md) или заполучить новый

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
