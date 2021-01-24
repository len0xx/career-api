# Создание вакансии

Метод для создания новой вакансии на сайте «Время Карьеры»

При успешном выполнении возвращает `ID` созданной вакансии

Полное описание структуры вакансии можно найти здесь — [vacancy](https://github.com/len0xx/career-api/blob/main/docs/vacancy.md)

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
* `the fields title and description are required` — пустое или отсутствующее значение полей `title` или `description`
* `non-existent category id given` — передан id несуществующей категории
* `invalid access_token` — передан несуществующий `access_token`
* `the access_token has already expired` — срок жизни токена истёк
* `this access_token is no longer available` — существует более новый токен для этого пользователя
* `account with such account_id does not exist` — пользователя с таким `id` (привязанным к `access_token`) не существует
* `invalid city` — передан некорректное название города
* `invalid company` — компании, с которой связан пользователь не существует
* `invalid scope for this method` — у переданного токена нет доступа к этому методу (см. [user-authorization](https://github.com/len0xx/career-api/blob/main/docs/user-authorization.md#%D0%B2%D0%BE%D0%B7%D0%BC%D0%BE%D0%B6%D0%BD%D1%8B%D0%B5-%D0%B7%D0%BD%D0%B0%D1%87%D0%B5%D0%BD%D0%B8%D1%8F-scope))
* `could not create the vacancy` — во время создания вакансии на сервере произошла непредвиденная ошибка, пожалуйста, попробуйте повторить запрос позднее
