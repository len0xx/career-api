# Описание объекта отклика

Отклики, как и другие сущности в рамках API, представляются в виде JSON объектов

### Структура объекта отклика

Название поля | Тип данных | Описание
------------ | ------------- | -------------
id | integer | Идентификатор отклика
vacancy_id | integer | Идентификатор вакансии
user_id | integer | Идентификатор откликнувшегося пользователя
resume | resume | Объект типа [resume](https://github.com/len0xx/career-api/blob/main/docs/resume.md)
status | enum | Статус отклика (`order`, `decline`, `interview`, `abort` или `''`)
comment | string | Комментарий
showed | integer | Был ли показан отклик (1 или 0)
showed_date | date | Дата показа (в формате `YYYY-mm-dd hh:mm:ss`)
create_date | date | Дата создания (в формате `YYYY-mm-dd hh:mm:ss`)
update_date | date | Дата обновления (в формате `YYYY-mm-dd hh:mm:ss`)
interview_date | date | Дата интервью (в формате `YYYY-mm-dd hh:mm:ss`)

### Пример отклика:
```javascript
{
    "id": 1600,
    "company_id": 1120,
    "vacancy_id": 52184,
    "user_id": 8905,
    "resume": {
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
        "deleted": "0"
    },
    "status": "order",
    "comment": "",
    "showed": 1,
    "showed_date": "2021-07-16 12:16:49",
    "create_date": "2021-06-03 04:58:32",
    "update_date": 0,
    "interview_date": 0
}
```
