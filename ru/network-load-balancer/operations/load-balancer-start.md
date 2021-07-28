---

__system: {"dislikeVariants":["Нет ответа на мой вопрос","Рекомендации не помогли","Содержание не соответсвует заголовку","Другое"]}
---
# Запустить сетевой балансировщик

{% list tabs %}

- Консоль управления
  
  Чтобы запустить [сетевой балансировщик](../concepts/index.md):
  1. Откройте раздел **Load Balancer** в каталоге, где требуется запустить балансировщик.
  1. Нажмите значок ![image](../../_assets/vertical-ellipsis.svg) в строке балансировщика, который требуется запустить, или откройте страницу нужного балансировщика.
  1. Нажмите кнопку **Запустить**.
  1. В открывшемся окне нажмите кнопку **Запустить**.
  
- CLI
  
  Если у вас еще нет интерфейса командной строки {{ yandex-cloud }}, [установите его](https://cloud.yandex.ru/docs/cli/quickstart#install).
  
  {% include [default-catalogue](../../_includes/default-catalogue.md) %}
  
  1. Посмотрите описание команды CLI для запуска сетевого балансировщика:
  
     ```
     $ yc load-balancer network-load-balancer start --help
     ```
  
  1. Получите список всех балансировщиков:
  
     ```
     $ yc load-balancer network-load-balancer list
     +----------------------+--------------------+-------------+----------+----------------+------------------------+----------+
     |          ID          |        NAME        |  REGION ID  |   TYPE   | LISTENER COUNT | ATTACHED TARGET GROUPS |  STATUS  |
     +----------------------+--------------------+-------------+----------+----------------+------------------------+----------+
     ...
     | b7r97ah2jn5rmo6k1dsk | test-load-balancer | ru-central1 | EXTERNAL |              1 | b7r97ah2jn5rmo6k1dsk   | INACTIVE |
     ...
     +----------------------+--------------------+-------------+----------+----------------+------------------------+----------+
     ```
  
  1. Выберите идентификатор (`ID`) или имя (`NAME`) нужного балансировщика, находящегося в состоянии `INACTIVE`.
  1. Запустите балансировщик:
  
     ```
     $ yc load-balancer network-load-balancer start b7r97ah2jn5rmo6k1dsk
     ```
  
- API
  
  Запустить сетевой балансировщик можно с помощью метода API [start](../api-ref/NetworkLoadBalancer/start.md).
  
{% endlist %}