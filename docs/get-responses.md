# Получение списка откликов на вакансии компании

Метод для получения всех существующих откликов на вакансии компании, к которой относится пользователь

При успешном выполнении отклики возвращаются в виде массива объектов отклика. Описание объекта можно посмотреть по ссылке — [response](https://github.com/len0xx/career-api/blob/main/docs/response.md)

### Для получения откликов необходимо выполнить запрос:
```
POST /api/get-responses/
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
    "responses": [
        {
            "id": "1600",
            "company_id": "1120",
            "vacancy_id": "52184",
            "user_id": "8905",
            "resume_id": "6812",
            "status": "order",
            "interview_date": "0",
            "comment": "",
            "showed": "1",
            "showed_date": "1626437809",
            "create_date": "1622696312",
            "update_date": "0",
            "create_day_period": "morning",
            "create_day_of_week": "4"
        },
        {
            "id": "1826",
            "company_id": "1120",
            "vacancy_id": "34821",
            "user_id": "15602",
            "resume_id": "10223",
            "status": "decline",
            "interview_date": "0",
            "comment": "",
            "showed": "1",
            "showed_date": "1626437809",
            "create_date": "1621591263",
            "update_date": "1621592230",
            "create_day_period": "evening",
            "create_day_of_week": "0"
        }
    ]
}
```

## Ошибки

В случае ошибки будет выдан соответствующий ответ с описанием проблемы. Например:
```javascript
{
    "success": false,
    "error": "invalid scope for this method"
}
```
Такой ответ говорит о том, что у переданного `access_token` нет доступа к этому типу запросов. Подробнее -  [user-authorization](https://github.com/len0xx/career-api/blob/main/docs/user-authorization.md#%D0%B2%D0%BE%D0%B7%D0%BC%D0%BE%D0%B6%D0%BD%D1%8B%D0%B5-%D0%B7%D0%BD%D0%B0%D1%87%D0%B5%D0%BD%D0%B8%D1%8F-scope)

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
* `could not collect the vacancies` — во время получения вакансий на сервере произошла непредвиденная ошибка, пожалуйста, попробуйте повторить запрос позднее
