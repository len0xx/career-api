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
* `you are not allowed to delete this vacancy` — вакансия относится к другой компании, поэтому с помощью переданного `access_token` нельзя удалить эту вакансию
* `this vacancy is already deleted` — эта вакансия уже удалена
* `the vacancy you are looking for does not exist` — не существует вакансии с таким значением `vacancy_id`
* `invalid access_token` — передан несуществующий `access_token`
* `the access_token has already expired` — срок жизни токена истёк
* `this access_token is no longer available` — существует более новый токен для этого пользователя
* `account with such account_id does not exist` — пользователя с таким `id` (привязанным к `access_token`) не существует
* `invalid scope for this method` — у переданного токена нет доступа к этому методу
* `could not delete the vacancy` — во время создания вакансии на сервере произошла непредвиденная ошибка, пожалуйста, попробуйте повторить запрос позднее
