# Получение access_token

Метод для обмена `code` на `access_token`

### Для получения токена доступа необходимо выполнить запрос:
```javascript
GET /api/auth/
```

### В теле запроса необходимо передать следующие параметры:
* `client_id` — Идентификтор приложения (см. [регистрация приложения](https://xn--80adjbxl0aeb4ii6a.xn--p1ai/wp-admin/admin.php?page=apps))
* `client_secret` — Секретный код приложения (см. [регистрация приложения](https://xn--80adjbxl0aeb4ii6a.xn--p1ai/wp-admin/admin.php?page=apps))
* `grant_type = authorization_code`
* `redirect_uri` — Адрес, на который пользователь будет перенаправлен после того как подтвердит авторизацию
* `code` — Код, который будет выдан после того, как пользователь подвердит авторизацию

### Пример ответа:
```javascript
{
    "success": true,
    "access_token": "CDF0EF87990394A8D5A7C7CA7FB80349", 
    "refresh_token": "4897FDEC0898880C8156B85666BD4EF3",
    "account_id": 44957
}
```
