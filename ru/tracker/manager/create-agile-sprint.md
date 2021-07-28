---

__system: {"dislikeVariants":["Нет ответа на мой вопрос","Рекомендации не помогли","Содержание не соответсвует заголовку","Другое"]}
---
# Спринты

{% note warning %}

Работа со спринтами возможна только на досках типа **Скрам**.

{% endnote %}

{{ tracker-name }} поможет вам организовать работу по методологии Cкрам. При таком подходе работа делится на спринты — итерации разработки определенной продолжительности. В начале каждой итерации происходит оценка задач и планирование работы на ближайший спринт.

## Спланировать спринт {#section_sjg_111_2gb}

#### Шаг 1. Оцените трудоемкость задач

Оцените трудоемкость задач бэклога. Трудоемкость оценивается в условных единицах Story Points, которые определяют сложность задач проекта относительно друг друга. Каждая команда самостоятельно договаривается, как именно определять трудоемкость своих задач.

Чтобы провести совместную командную оценку трудоемкости задач, используйте [покер планирования на доске задач](planning-poker.md).

Если у вас уже есть оценка трудоемкости задачи, вы можете [указать ее на странице задачи](../user/edit-ticket.md#section_jqw_ppn_jz) в поле **Story Points**.

Чтобы указать оценки трудоемкости для нескольких задач при планировании спринта:

1. На верхней панели {{ tracker-name }} нажмите **Доски** и выберите вашу доску.

1. В правом верхнем углу страницы нажмите кнопку **Спринты**.

1. Если задач слишком много, скройте лишние с помощью [фильтров](#section_ync_v5r_yfb).

1. Наведите курсор на задачу в колонке **Бэклог**.

1. Введите количество **Story Points** в поле справа.

    Чтобы добавить задачу на страницу покера для [командной оценки](planning-poker.md), нажмите кнопку ![](../../_assets/tracker/context-menu.png) и выберите пункт **Добавить в покер**.

#### Шаг 2. Создайте новый спринт {#create_sprint}

1. Нажмите кнопку ![](../../_assets/tracker/add-sprint.png) в правой части блока **Спринты**.

1. Введите название спринта и время его начала и окончания.

1. Нажмите кнопку **Сохранить**.

#### Шаг 3. Добавьте задачи в спринт

Добавить задачу в спринт можно несколькими способами:

- На странице **Спринты** перетащите задачу из колонки **Бэклог** в колонку спринта. Если задач слишком много, скройте лишние с помощью [фильтров](#section_ync_v5r_yfb).

- На странице задачи укажите спринт в соответствующем поле на панели справа.

- Чтобы быстро добавить много задач, воспользуйтесь [массовым редактированием](bulk-change.md#section_x2j_4kr_fgb): отфильтруйте задачи и укажите спринт в соответствующем поле при редактировании.

## Изменить статус спринта {#section_f1f_21r_yfb}

Статус указывает на готовность задач спринта. Чтобы изменить статус спринта:

1. На верхней панели {{ tracker-name }} нажмите **Доски** и выберите вашу доску.

1. В правом верхнем углу страницы нажмите кнопку **Спринты**.

1. Нажмите значок ![](../../_assets/tracker/edit-sprint.png) справа от названия спринта.

1. Выберите один из статусов:

    Статус | Описание
    ----- | -----
    Открыт | Задачи спринта не взяты в работу.
    В работе | Задачи спринта находятся в работе.
    Решен | Задачи спринта решены.
    В архиве | Спринт перемещен в архив и не отображается в общем списке спринтов. Чтобы открыть список архивных спринтов, нажмите кнопку **Архивные спринты**.<br/><br/>В архивный спринт нельзя добавить задачу.

1. Нажмите кнопку **Сохранить**.

## Объединить задачи в эпик {#section_vj5_4f5_zfb}

Эпик — тип задачи, который позволяет группировать задачи из разных очередей и планировать трудозатраты.

На доске можно [создавать эпики и добавлять в них задачи](epic.md).

## Применить фильтры {#section_ync_v5r_yfb}

Чтобы на вкладке **Спринты** отобразились только те задачи, которые обладают определенными параметрами, примените фильтры. Для этого:

1. На верхней панели {{ tracker-name }} нажмите **Доски** и выберите вашу доску.

1. В правом верхнем углу страницы нажмите кнопку **Спринты**.

1. В левой части страницы выберите параметры отбора задач. Для этого нажмите кнопку фильтра:

    - **Резолюция**

        Чтобы на странице отобразились закрытые задачи с определенной резолюцией, выберите одну или несколько резолюций из списка.

    - **Статус**

        Чтобы на странице отобразились задачи с определенным статусом, выберите один или несколько статусов из списка.

    - **Я исполнитель**

        На странице спринта отобразятся задачи, которые пользователь выполняет.

    - **Я автор**

        На странице спринта отобразятся задачи, которые пользователь создал.

    - [**Эпики**](epic.md)

        Чтобы выбрать задачи, которые входят в эпик, нажмите на блок с названием эпика.

        Чтобы выбрать задачи, которые не объединены в эпики, нажмите кнопку **Без эпиков**.

    - **Версии**

        Чтобы на странице отобразились задачи, которые принадлежат к определенной версии, нажмите на блок с названием эпика.

    - **Компоненты**

        Чтобы на странице отобразились задачи с определенным компонентом, нажмите на блок с названием компонента.

    - **Теги**

        Чтобы на странице отобразились задачи с определенным тегом, нажмите на блок с названием тега.

## Настроить отображение спринтов {#section_jyp_w25_xgb}

Вы можете настроить страницу спринтов так, чтобы список задач и спринты отображались в одной колонке. Для этого:

1. {% include [open-personal-settings](../../_includes/tracker/open-personal-settings.md) %}

1. Выберите опцию **Отображать спринты и задачи в одной колонке**.

1. Нажмите кнопку **Сохранить**.
