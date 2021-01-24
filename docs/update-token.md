# Обновление токена

Метод для обновления истёкшего токен доступа с помощью пары `access_token`-`refresh_token`.

После того, как Вы заполучили `access_token`, он будет действителен в течение одного часа, а потом перестанет быть работоспособным. Однако для того, чтобы не просить пользователя авторизоваться в очередной раз, можно просто обновить токен доступа с помощью этого метода.

### Запрос:
```
POST /api/update-token/
```

### В теле запроса необходимо передать следующие параметры:
* `client_id` — Идентификтор приложения (см. [регистрация приложения](https://xn--80adjbxl0aeb4ii6a.xn--p1ai/wp-admin/admin.php?page=apps))
* `client_secret` — Секретный код приложения (см. [регистрация приложения](https://xn--80adjbxl0aeb4ii6a.xn--p1ai/wp-admin/admin.php?page=apps))
* `grant_type = refresh_token`
* `access_token` — Токен доступа, который выхотите обновить
* `refresh_token` — Токен для обновления истёкшего токена

### Необязательный параметр:
* `scope` — К каким данным Вы хотите получить доступ (см. [user-authorization](https://github.com/len0xx/career-api/blob/main/docs/user-authorization.md#%D0%B2%D0%BE%D0%B7%D0%BC%D0%BE%D0%B6%D0%BD%D1%8B%D0%B5-%D0%B7%D0%BD%D0%B0%D1%87%D0%B5%D0%BD%D0%B8%D1%8F-scope))

### Пример ответа:
```javascript
{
    "success": true,
    "access_token": "CDF0EF87990394A8D5A7C7CA7FB80349", 
    "refresh_token": "4897FDEC0898880C8156B85666BD4EF3",
    "account_id": 44957
}
```

Полученный токен доступа точно так же имеет срок жизни, равный **одному часу** с момента выдачи. При повторном запросе ранее выданный токен **отзывается** и выдается новый. `refresh_token` имеет срок жизни = один месяц, после истечения этого срока полученный `access_token` будет нельзя обновить.

## Ошибки

В случае ошибки будет выдан соответствующий ответ с описанием проблемы. Например:
```javascript
{
    "success": false,
    "error": "wrong refresh_token for this access_token"
}
```
Такой ответ говорит о том, что переданный `refresh_token` не подходит для этого `access_token` и, соответственно, сервер не может выдать новый токен.

### Возможные ошибки
* `empty request` — получено пустое тело запроса
* `insufficient arguments passed` — не передан хотя бы один из обязательных параметров
* `invalid client_id` — передан несуществующий `client_id`
* `wrong client_secret` — передан некорректный `client_secret` (неподходящий для переданного `client_id`)
* `wrong redirect_uri` — некорректный `redirect_uri` (не совпадает с тем, что был указан при регистрации приложения)
* `the refresh_token has already expired` — истёк срок жизни `refresh_token`
* `this refresh_token has already been used` — переданный `refresh_token` уже был использован
* `wrong refresh_token for this access_token` — передан некорректный `refresh_token` (неподходящий для переданного `access_token`)
* `invalid scope` — передано некорректное значение `scope` (см. [user-authorization](https://github.com/len0xx/career-api/blob/main/docs/user-authorization.md#%D0%B2%D0%BE%D0%B7%D0%BC%D0%BE%D0%B6%D0%BD%D1%8B%D0%B5-%D0%B7%D0%BD%D0%B0%D1%87%D0%B5%D0%BD%D0%B8%D1%8F-scope))
* `invalid access_token` — передан несуществующий `access_token`
* `account with such account_id does not exist` — пользователя с таким `id` (привязанным к `access_token`) не существует
* `the server could not create access_token, please try again` — во время создания `access_token` на сервере произошла непредвиденная ошибка, попробуйте повторить запрос позднее
