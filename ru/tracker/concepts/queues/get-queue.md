---

__system: {"dislikeVariants":["Нет ответа на мой вопрос","Рекомендации не помогли","Содержание не соответсвует заголовку","Другое"]}
---
# Получить параметры очереди

Запрос позволяет получить информацию об очереди.

## Формат запроса {#section_rnm_x4j_p1b}

Для получения информации об очереди используйте HTTP-запрос с методом `GET`:

```json
GET /v2/queues/<queue-id>?
expand=<дополнительные поля в ответе>
Host: {{ host }}
Authorization: OAuth <OAuth-токен>
{{ org-id }}
```

{% include [headings](../../../_includes/tracker/api/headings.md) %}

#### Параметры запроса {#req-params}

- **\<queue-id\>**
    
    Идентификатор или ключ очереди. Ключ очереди чувствителен к регистру символов.

- **expand (необязательный)**

    Дополнительные поля, которые будут включены в ответ. Возможные значения:
	
    - `all` — в ответ будут включены все дополнительные поля очереди;
    - `projects` — проекты очереди;
    - `components` — компоненты очереди;
    - `versions` — версии очереди;
    - `types` — типы задач;
    - `team` — список участников команды очереди;
    - `workflows` — список жизненных циклов;
    - `fields` — обязательные поля очереди;
    - `issueTypesConfig` — настройки типов задач очереди.

> Запрос очереди:
> 
> - Используется HTTP-метод GET.
> - В ответе включено отображение всех дополнительных полей.
> 
> ```
> GET /v2/queues/TEST?expand=all HTTP/1.1
> Host: {{ host }}
> Authorization: OAuth <OAuth-токен>
> {{ org-id }}
> Cache-Control: no-cache
> ```

## Формат ответа {#section_xc3_53j_p1b}

```json
{
    "self": "{{ host }}/v2/queues/TEST",
    "id": 3,
    "key": "TEST",
    "version": 5,
    "name": "Test",
    "description": "Очередь, заведённая в тестовых целях",
    "lead": {
           "self": "{{ host }}/v2/users/1120000000016876",
           "id": "<id сотрудника>",
           "display": "<отображаемое имя сотрудника>"
    },
    "assignAuto": false,
    "defaultType": {
           "self": "{{ host }}/v2/issuetypes/1",
           "id": "1",
           "key": "bug",
           "display": "Ошибка"
    },
    "defaultPriority": {
           "self": "{{ host }}/v2/priorities/3",
           "id": "3",
           "key": "normal",
           "display": "Средний"
    },
    "teamUsers": [
           {
               "self": "{{ host }}/v2/users/1120000000016876",
               "id": "<id сотрудника>",
               "display": "<отображаемое имя сотрудника>"
           },
           ...
    ],
    "issueTypes": [
           {
               "self": "{{ host }}/v2/issuetypes/1",
               "id": "1",
               "key": "bug",
               "display": "Ошибка"
           },
           ...
    ],
    "versions": [
           {
               "self": "{{ host }}/v2/versions/4",
               "id": "4",
               "display": "Куку"
        }
    ],
    "workflows": {
           "dev": [
               {
                    "self": "{{ host }}/v2/issuetypes/1",
                    "id": "1",
                    "key": "bug",
                    "display": "Ошибка"
                },
                ...
           ]
    },
    "denyVoting": false,
    "issueTypesConfig": [
           {
               "issueType": {
                      "self": "{{ host }}/v2/issuetypes/1",
                      "id": "1",
                      "key": "bug",
                      "display": "Ошибка"
            },
            "workflow": {
                      "self": "{{ host }}/v2/workflows/dev",
                      "id": "dev",
                      "display": "dev"
            },
            "resolutions": [
                   {
                      "self": "{{ host }}/v2/resolutions/2",
                      "id": "2",
                      "key": "wontFix",
                      "display": "Не будет исправлено"
                   },
                ...
            ]
        },
        ...
    ]
}
```

#### Параметры ответа {#answer-params}

Параметр | Описание | Тип данных
----- | ----- | -----
self | Ссылка на очередь. | Строка
id | Идентификатор очереди. | Строка
key | Ключ очереди. | Строка
version | Версия очереди. Каждое изменение очереди увеличивает номер версии. | Число
name | Название очереди. | Строка
description | Текстовое описание очереди. | Строка
[lead](#lead) | Блок с информацией о владельце очереди. | Объект
assignAuto | Автоматически назначить исполнителя для новых задач очереди:<br/><br/>`true`— назначить.<br/><br/>`false`— не назначать. | Логический
[defaultType](#default-type) | Блок с информацией о типе задачи по умолчанию. | Объект
[defaultPriority](#default-priority) | Блок с информацией о приоритете задачи по умолчанию | Объект
[teamUsers](#team-users) | Массив с информацией об участниках команды очереди | Массив объектов
[issueTypes](#issue-types) | Массив с информацией о типах задач очереди. | Массив объектов
[versions](#versions) | Массив с информацией о версиях очереди | Массив объектов
[workflows](#workflows) | Список жизненных циклов очереди и их типов задач. | Массив
denyVoting | Признак возможности голосования за задачи. | Логический
[issueTypesConfig](#issue-types-config) | Массив с настройками задач очереди. | Массив объектов

**Поля объекта** `lead` {#lead}

Параметр | Описание | Тип данных
----- | ----- | -----
self | Ссылка на пользователя. | Строка
id | Идентификатор пользователя. | Строка
display | Отображаемое имя пользователя. | Строка

**Поля объекта** `defaultType` {#default-type}
	
Параметр | Описание | Тип данных
----- | ----- | -----
self | Ссылка на тип задачи. | Строка
id | Идентификатор типа задачи. | Строка
key | Ключ типа задачи. | Строка
display | Отображаемое название типа задачи. | Строка

**Поля объекта** `defaultPriority` {#default-priority}

Параметр | Описание | Тип данных
----- | ----- | -----
self | Ссылка на тип приоритета. | Строка
id | Идентификатор приоритета. | Строка
key | Ключ приоритета. | Строка
display | Отображаемое название приоритета. | Строка

**Поля объектов массива** `teamUsers` {#team-users}

Параметр | Описание | Тип данных
----- | ----- | -----
self | Ссылка на пользователя. | Строка
id | Идентификатор пользователя. | Строка
display | Отображаемое имя пользователя. | Строка

**Поля объектов массива** `issueTypes` {#issue-types}

Параметр | Описание | Тип данных
----- | ----- | -----
self | Ссылка на тип задачи. | Строка
id | Идентификатор типа задачи. | Строка
key | Ключ типа задачи. | Строка
display | Отображаемое название типа задачи. | Строка

**Поля объектов массива** `versions` {#versions}

Параметр | Описание | Тип данных
----- | ----- | -----
self | Ссылка на версию очереди. | Строка
id | Идентификатор версии. | Строка
display | Отображаемое название версии. | Строка

**Поля объектов массива** `workflows` {#workflows}

Параметр | Описание | Тип данных
----- | ----- | -----
self | Ссылка на тип задачи. | Строка
id | Идентификатор типа задачи. | Строка
key | Ключ типа задачи. | Строка
display | Отображаемое название типа задачи. | Строка

**Поля объектов массива** `issueTypesConfig` {#issue-types-config}

Параметр | Описание | Тип данных
----- | ----- | -----
[issueType](#issue-type) | Блок с информацией о типе задачи. | Объект
[workflow](#workflow) | Блок с информацией о жизненном цикле типа задачи. | Объект
[resolutions](#resolutions) | Массив с возможными резолюциями типа задачи. | Массив объектов

**Поля объекта** `issueType` {#issue-type}

Параметр | Описание | Тип данных
----- | ----- | -----
self | Ссылка на тип задачи. | Строка
id| Идентификатор типа задачи. | Строка
key | Ключ типа задачи. | Строка
display | Отображаемое название типа задачи. | Строка

**Поля объекта** `workflow` {#workflow}

Параметр | Описание | Тип данных
----- | ----- | -----
self | Ссылка на объект жизненного цикла. | Строка
id | Идентификатор жизненного цикла. | Строка
display | Отображаемое название жизненного цикла. | Строка

**Поля объектов массива** `resolutions` {#resolutions}

Параметр | Описание | Тип данных
----- | ----- | -----
self | Ссылка на объект резолюции. | Строка
id | Идентификатор резолюции. | Строка
key | Идентификатор резолюции. | Строка
display | Отображаемое название резолюции. | Строка

## Возможные коды ответа {#section_otf_jrj_p1b}

200
:   Запрос выполнен успешно.

404
:   Запрошенный объект не был найден. Возможно, вы указали неверное значение идентификатора или ключа объекта.
