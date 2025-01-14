# Настройка эндпоинта-источника {{ CH }}

При [создании](../index.md#create) или [изменении](../index.md#update) эндпоинта вы можете задать:

* Настройки подключения к [кластеру {{ mch-full-name }}](#managed-service) или [пользовательской инсталляции](#on-premise), в т. ч. на базе виртуальных машин {{ compute-full-name }}. Эти параметры обязательные.
* [Дополнительные параметры](#additional-settings).

## Кластер {{ mch-name }} {#managed-service}

Подключение к БД с указанием идентификатора кластера в {{ yandex-cloud }}. Доступно только для кластеров, развернутых в сервисе [{{ mch-name }}](../../../../managed-clickhouse/).

{% list tabs %}

- Консоль управления

    {% include [Managed ClickHouse UI](../../../../_includes/data-transfer/necessary-settings/ui/managed-clickhouse.md) %}

{% endlist %}

## Пользовательская инсталляция {#on-premise}

Подключение к БД с явным указанием сетевых адресов и портов.

{% list tabs %}

- Консоль управления

    {% include [On premise ClickHouse UI](../../../../_includes/data-transfer/necessary-settings/ui/on-premise-clickhouse.md) %}

{% endlist %}

## Дополнительные настройки {#additional-settings}

{% list tabs %}

- Консоль управления

    * **Включенные таблицы** — будут передаваться данные только из таблиц этого списка. Задается с помощью регулярных выражений.
    * **Исключенные таблицы** — данные таблиц из этого списка передаваться не будут. Задается с помощью регулярных выражений.

    Для обоих списков поддерживаются выражения вида:

    * `<имя схемы>.<имя таблицы>` — полное имя таблицы;
    * `<имя схемы>.*` — все таблицы в указанной схеме;
    * `<имя таблицы>` — таблица в схеме по умолчанию.

{% endlist %}
