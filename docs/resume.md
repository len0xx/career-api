# Описание объекта резюме

Резюме, как и другие сущности в рамках API, представляются в виде JSON объектов

### Структура объекта резюме

Название поля | Тип данных | Описание
------------ | ------------- | -------------
id | integer | Идентификатор резюме
attachment_id | integer | Идентификатор прикреплённого документа (для обычных резюме — `null`)
link | string | Ссылка на резюме
photo_url | string | Ссылка на фотографию
create_date | date | Дата создания (в формате `YYYY-mm-dd hh:mm:ss`)
change_date | date | Дата обновления (в формате `YYYY-mm-dd hh:mm:ss`)
deleted | integer | Удалено ли резюме (`1` или `0`)
data | object | Описание ниже

### Структура объекта данных резюме (поле data)

Название поля | Тип данных | Описание
------------ | ------------- | -------------
achievements | array | Идентификатор резюме
area | integer | Идентификатор населённого пункта (см. [terms](https://github.com/len0xx/career-api/blob/main/docs/terms.md))
birthday | date | Дата рождения (в формате `YYYY-mm-dd`)
citizenship | string | Гражданство
courses | array | Массив пройденных курсов (см. [objects](https://github.com/len0xx/career-api/blob/main/docs/objects.md))
driving_license | array | Массив категорий прав (возможные значения: `a, b, c, d, e, be, ce, de, tm, tb`)
education | array | Массив образований (см. [objects](https://github.com/len0xx/career-api/blob/main/docs/objects.md))
email | string | Электронная почта
employment | enum | Тип трудоустройства (см. [objects](https://github.com/len0xx/career-api/blob/main/docs/objects.md))
experience | enum | Опыт работы (см. [objects](https://github.com/len0xx/career-api/blob/main/docs/objects.md))
firstname | string | Имя
gender | enum | Пол (см. [objects](https://github.com/len0xx/career-api/blob/main/docs/objects.md))
has_car | enum | Имеется ли собственный автомобиль (`yes` или `no`)
hobby | string | Хобби
languages | array | Массив иностранных языков (см. [objects](https://github.com/len0xx/career-api/blob/main/docs/objects.md))
metro_station | string | Станция метро
noexp_reason | string | Причина, по которой нет опыта работы
phone | string | Номер телефона
photo_loaded | integer | Загружена ли фотография (`1` или `0`)
places_of_work | array | Массив мест работы (см. [objects](https://github.com/len0xx/career-api/blob/main/docs/objects.md))
position | string | Желаемая позиция
relocative | enum | Согласен ли на переезд (`yes` или `no`)
salary | string | Желаемая заработная плата
schedule | string | Расписание работы
skills | array | Массив навыков (см. [objects](https://github.com/len0xx/career-api/blob/main/docs/objects.md))
social | array | Массив аккаунтов в социальных сетях (см. [objects](https://github.com/len0xx/career-api/blob/main/docs/objects.md))
spheres | array | Массив сфер деятельности (см. [terms](https://github.com/len0xx/career-api/blob/main/docs/terms.md))
surname | string | Фамилия

### Пример резюме:
```javascript
{
    "photo_url": "https://xn--80adjbxl0aeb4ii6a.xn--p1ai/resume/photo/6812.jpg",
    "attachment_id": null,
    "link": "https://xn--80adjbxl0aeb4ii6a.xn--p1ai/364c7b963682347/Открыть/Резюме.pdf",
    "data": {
        "achievements": [
            {
                "name": "Победа на олимпиаде",
                "description": "",
                "year": 2020
            },
            {
                "name": "Победа на хакатоне",
                "description": "",
                "year": 2021
            }
        ],
        "area": 6883,
        "birthday": "2000-08-19",
        "citizenship": "Россия",
        "courses": [
            {
                "title": "Школа разработчиков C++",
                "school": "Прософт-Системы"
            }
        ],
        "driving_license": [ "a", "b" ],
        "education": [
            {
                "name": "Уральский федеральный университет имени первого Президента России Б.Н. Ельцина, Екатеринбург",
                "start_year": "2018",
                "end_year": "2022",
                "faculty": "Институт радиоэлектроники и информационных технологий",
                "specialty": "Конструирование и технология электронных средств",
                "degree": "bachelor"
            }
        ],
        "email": "contact@email.com",
        "employment": "full",
        "experience": "onethree",
        "firstname": "Иван",
        "gender": "male",
        "has_car": "no",
        "hobby": "Люблю читать книги и статьи в свободное время",
        "languages": [
            {
                "title": "Английский",
                "level": "C1"
            },
            {
                "title": "Итальянский",
                "level": "B1"
            }
        ],
        "metro_station": "Чкаловская",
        "noexp_reason": "",
        "phone": "+7 (996) 176 43-43",
        "photo_loaded": "1",
        "places_of_work": [
            {
                "company": "УрФУ",
                "start_year": "2020-05-05",
                "end_year": "0",
                "no_end": "yes",
                "position": "Веб-разработчик",
                "duties": "Поддержка веб-сайтов основных проектов университета",
                "achievs": ""
            },
            {
                "company": "Прософт-Системы",
                "start_year": "2021-07-05",
                "end_year": "2021-08-01",
                "no_end": "no",
                "position": "Инженер-разработчик C++",
                "duties": "Разработка ПО для управления и настройки ПЛК Regul RX00",
                "achievs": ""
            }
        ],
        "position": "Веб-разработчик",
        "relocative": "no",
        "salary": "50000",
        "schedule": "remote",
        "skills": [
            {
                "title": "PHP",
                "level": "9"
            },
            {
                "title": "JavaScript",
                "level": "8"
            },
            {
                "title": "C/C++",
                "level": "7"
            }
        ],
        "social": {
            "vk": "https://vk.com/timeforcareer",
            "facebook": "https://facebook.com/time_career",
            "instagram": "@time_career",
            "behance": "https://behance.com/time_career",
            "habr": "https://habr.com/time_career",
            "github": "https://github.com/len0xx"
        },
        "spheres": [
            51
        ],
        "surname": "Иванов"
    },
    "id": 6812,
    "create_date": "2021-06-24 06:05:55",
    "change_date": "2021-09-21 05:42:33",
    "deleted": 0
}
```
