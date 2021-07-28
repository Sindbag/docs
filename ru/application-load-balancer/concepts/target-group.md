---

__system: {"dislikeVariants":["Нет ответа на мой вопрос","Рекомендации не помогли","Содержание не соответсвует заголовку","Другое"]}
---
# Целевая группа

Целевая группа L7-балансировщика — это набор IP-адресов ВМ, на которых запущены ваши сетевые приложения. Целевые группы указываются в конфигурациях [групп бэкендов](backend-group.md) для распределения запросов балансировщиком.

Целевые группы можно [создавать вручную](../operations/target-group-create.md) или создать целевую группу ВМ для L7-балансировщика в сервисе {{ ig-name }}. При изменении конфигурации ВМ {{ ig-name }} будет автоматически поддерживать актуальность IP-адресов машин в целевой группе. Если целевая группа подключена к группе бэкендов, {{ ig-name }} будет следить и за результатами проверок состояния, которые отправляет L7-балансировщик.