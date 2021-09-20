# Описание объекта отклика

Отклики, как и другие сущности в рамках API, представляются в виде JSON объектов

### Структура объекта отклика

Название поля | Тип данных | Описание
------------ | ------------- | -------------
id | integer | Идентификатор отклика
vacancy_id | integer | Идентификатор вакансии
user_id | integer | Идентификатор откликнувшегося пользователя
resume_id | integer | Идентификатор резюме, которое пользователь прикрепил к отклику
status | string | Статус отклика (orded, decline, interview, abort или '')
interview_date | date | Дата интервью (в формате `YYYY-mm-dd hh:mm:ss`)
comment | string | Комментарий
showed | integer | Был ли показан отклик (1 или 0)
showed_date | date | Дата показа (в формате `YYYY-mm-dd hh:mm:ss`)
create_date | date | Дата создания (в формате `YYYY-mm-dd hh:mm:ss`)
update_date | date | Дата обновления (в формате `YYYY-mm-dd hh:mm:ss`)
create_day_period | string | Время суток, когда был создан отзыв (morning, afternoon, evening или night)
create_day_of_week | integer | День недели, когда был создан отзыв (0 - 6)

### Пример отклика:
```javascript
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
}
```
