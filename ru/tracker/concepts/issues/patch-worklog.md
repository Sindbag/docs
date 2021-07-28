---

__system: {"dislikeVariants":["Нет ответа на мой вопрос","Рекомендации не помогли","Содержание не соответсвует заголовку","Другое"]}
---
# Редактировать запись о затраченном времени

Запрос позволяет изменить запись о времени, затраченном на выполнение задачи.

## Формат запроса {#section_q5n_mtk_gfb}

Чтобы изменить запись о затраченном на задачу времени, используйте HTTP-запрос с методом `PATCH`. Параметры запроса передаются в его теле в формате JSON:

```json
PATCH /{{ ver }}/issues/<issue-id>/worklog/<worklog-id>
Host: {{ host }}
Authorization: OAuth <токен>
{{ org-id }}

{
    "duration": "P3W",
    "comment": "время изменено!"
}
```

{% include [headings](../../../_includes/tracker/api/headings.md) %}

#### Ресурс {#req-resource}

- **\<issue-id\>**

    Идентификатор или ключ задачи.

- **\<worklog-id\>**

    Идентификатор записи о затраченном времени.


#### Тело запроса {#req-body-params}

Тело запроса содержит параметры задачи:

Параметр | Описание | Тип данных
-------- | -------- | ----------
duration | Затраченное время в формате ```PnYnMnDTnHnMnS, PnW``` в соответствии с [ISO 8601]({{ link-iso-8601 }}). | Строка
comment | Текст комментария к записи. Комментарий сохранится в Отчёте по затратам времени. | Строка

## Формат ответа {#section_gvv_tdl_gfb}

{% list tabs %}

- Запрос выполнен успешно

    В случае успешного выполнения запроса API возвращает ответ с кодом 200. Тело ответа содержит JSON-объект с измененной записью о времени, затраченном на выполнение задачи.

    #### Тело ответа {#answer-body}

    ```json
    {
      "self": "{{ host }}/v2/issues/TEST-324/worklog/1",
      "id": 1,
      "version": 1402121720882,
      "issue": {
        "self": "{{ host }}/v2/issues/TEST-324",
        "id": "515ec9eae4b09cfa984e2047",
        "key": "TEST-324",
        "display": "важная задача"
      },
      "comment": "важный комментарий",
      "createdBy": {
        "self": "{{ host }}/v2/users/1120000000014909",
        "id": "veikus",
        "display": "Artem Veikus"
      },
      "updatedBy": {
        "self": "{{ host }}/v2/users/1120000000014909",
        "id": "veikus",
        "display": "Artem Veikus"
      },
      "createdAt": "2014-06-06T08:42:06.258+0000",
      "updatedAt": "2014-06-06T08:42:06.258+0000",
      "start": "2014-06-06T08:41:58.000+0000",
      "duration": "P3W"
    }
    ```
    #### Параметры ответа {#answer-params}

    Параметр | Описание | Тип данных
    -------- | -------- | ----------
    self | Адрес ресурса API, который содержит запись о затраченном времени. | Строка
    id | Идентификатор записи о затраченном времени. | Строка
    version | Версия записи. Каждое изменение записи увеличивает номер версии. | Строка
    [issue](#issue) | Блок с информацией о задаче. | Объект
    comment | Текст комментария к записи. Комментарий сохранится в Отчёте по затратам времени. | Строка
    [createdBy](#createdBy) | Объект с информацией о создателе записи. | Объект
    [updatedBy](#updatedBy) | Объект с информацией о пользователе, внесшем изменение в запись. | Объект
    createdAt | Дата и время создания записи в формате: ```YYYY-MM-DDThh:mm:ss.sss±hhmm``` | Строка
    updatedAt | Дата и время обновления записи в формате: ```YYYY-MM-DDThh:mm:ss.sss±hhmm``` | Строка
    start | Дата и время начала работы над задачей в формате: ```YYYY-MM-DDThh:mm:ss.sss±hhmm``` | Строка
    duration | Затраченное время в формате ```PnYnMnDTnHnMnS, PnW``` в соответствии с [ISO 8601]({{ link-iso-8601 }}). | Строка

    **Поля объекта** `issue` {#issue}

    Параметр | Описание | Тип данных
    -------- | -------- | ----------
    self | Адрес ресурса API, который содержит информацию о задаче. | Строка
    id | Идентификатор задачи. | Строка
    key | Ключ задачи. | Строка
    display | Отображаемое название задачи. | Строка

    **Поля объекта** `createdBy` {#createdBy}

    Параметр | Описание | Тип данных
    -------- | -------- | ----------
    self | Адрес ресурса API, который содержит информацию о пользователе. | Строка
    id | Идентификатор пользователя. | Строка
    display | Отображаемое имя пользователя. | Строка

    **Поля объекта** `updatedBy` {#updatedBy}

    Параметр | Описание | Тип данных
    -------- | -------- | ----------
    self | Адрес ресурса API, который содержит информацию о пользователе. | Строка
    id | Идентификатор пользователя. | Строка
    display | Отображаемое имя пользователя. | Строка

- Запрос выполнен с ошибкой

    Если запрос не был успешно обработан, ответное сообщение содержит информацию о возникших ошибках:

    HTTP-код ошибки | Описание ошибки
    --------------- | ---------------
    400 Bad Request | Один из параметров запроса имеет недопустимое значение или формат данных.
    403 Forbidden | У пользователя или приложения нет прав на доступ к ресурсу, запрос отклонен.
    404 Not Found | Запрашиваемый ресурс не найден.
    422 Unprocessable Entity | Ошибка валидации JSON, запрос отклонен.
    500 Internal Server Error | Внутренняя ошибка сервиса. Попробуйте повторно отправить запрос через некоторое время.
    503 Service Unavailable | Сервис API временно недоступен.

{% endlist %}