# Создание вакансии

Метод для создания новой вакансии на сайте «Время Карьеры»

При успешном выполнении возвращает `ID` созданной вакансии

### Для получения вакансии необходимо выполнить запрос:
```
POST /api/create-vacancy/
```

### В теле запроса необходимо передать следующие параметры:
* `client_id` — Идентификтор приложения (см. [регистрация приложения](https://xn--80adjbxl0aeb4ii6a.xn--p1ai/wp-admin/admin.php?page=apps))
* `client_secret` — Секретный код приложения (см. [регистрация приложения](https://xn--80adjbxl0aeb4ii6a.xn--p1ai/wp-admin/admin.php?page=apps))
* `access_token` — Токен доступа (см. [получение токена](https://github.com/len0xx/career-api/blob/main/docs/auth.md))
* `title` — Название новой вакансии
* `description` — Текстовое описание новой вакансии

### Также можно передать дополнительные параметры:
* `duties` — Обязанности новой вакансии (текст)
* `description` — Текстовое описание новой вакансии
* `min_salary` — Минимальная заработная плата (целое число)
* `max_salary` — Максимальная заработная плата (целое число)
* `categories` — Массив категорий новой вакансии (в виде id) (все категории можно получить с помощью [get-categories](https://github.com/len0xx/career-api/blob/main/docs/get-categories.md))
* `city` — Город, в котором актуальна новая вакансия (в виде названия города)
* `employment` — Занятость (см. [employments](https://github.com/len0xx/career-api/blob/main/docs/employments.md)),
* `requirements` — Текстовое описание требований к соискателю
* `contact_fio` — ФИО контактного лица (строка)
* `contact_phone` — Контактный номер (строка, в формате +7 (999) 888 7654)
* `contact_email` — Контактый email (строка)
* `working_conditions` — Условия работы (строка)

### Пример запроса
```javascript
{
    "client_id": 0,
    "client_secret": "b35ef4fe21294ac5",
    "access_token": "8248D5F9C68BF23F9C296D3B10119F01"
    "title": "Инженер",
    "description": "Описание новой вакансии",
    "duties": "Обязанности новой вакансии",
    "min_salary": 40000,
    "max_salary": 60000,
    "categories": [
        620, 534
    ],
    "city": "Екатеринбург",
    "employment": "full",
    "requirements": "Требования к соискателю",
    "contact_fio": "Иванов Иван Иванович",
    "contact_phone": "+7 (800) 500 4040",
    "contact_email": "contact@example.com",
    "working_conditions": "Условия работы"
}
```

### Пример ответа:
```javascript
{
    "success": true,
    "vacancy_id": 200
}
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
