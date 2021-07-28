---
title: "Сетевой балансировщик нагрузки"
description: "Сетевой балансировщик используется для равномерного распределения нагрузки по облачным ресурсам. Балансировщик создается в каталоге и может обслуживать ресурсы из нескольких зон доступности. Сетевой балансировщик Yandex.Cloud работает на 4-м уровне сетевой модели OSI. При этом балансировщик использует технологии, работающие на 3-м уровне для ускорения обработки пакетов."

__system: {"dislikeVariants":["Нет ответа на мой вопрос","Рекомендации не помогли","Содержание не соответсвует заголовку","Другое"]}
---


# Сетевой балансировщик нагрузки

*Сетевой балансировщик* используется для равномерного распределения нагрузки по облачным ресурсам. Балансировщик создается в каталоге и может обслуживать ресурсы из нескольких зон доступности. К каждому балансировщику подключается только одна целевая группа, состояние ресурсов в которой проверяется одной [проверкой состояния](health-check.md). За прием трафика отвечает [обработчик](listener.md) балансировщика.

Сетевой балансировщик {{ yandex-cloud }} работает на 4-м уровне сетевой модели OSI. При этом балансировщик использует технологии, работающие на 3-м уровне для ускорения обработки пакетов.

Адресация трафика строится по принципу 5-tuple: учитывается адрес и порт отправителя, адрес и порт принимающего облачного ресурса и протокол передачи информации.

При создании сетевого балансировщика к нему подключается заранее созданная [целевая группа](target-resources.md) облачных ресурсов, по которой будет распределяться входящий трафик. Каждый облачный ресурс в целевой группе определяется парой из [внутреннего IPv4-адреса](../../vpc/concepts/address.md) и идентификатора [подсети](../../vpc/concepts/network.md#subnet). Целевые ресурсы одной группы должны находиться в одной облачной сети. В пределах одной зоны доступности целевые ресурсы должны находиться в одной подсети. 

При размещении ресурсов в разных зонах доступности обеспечивается отказоустойчивость: если целевые ресурсы есть во всех зонах доступности и они готовы принимать трафик, то трафик распределяется по всем зонам. Если все ресурсы одной из зон выйдут из строя, то трафик больше не будет направляться в эту зону, а будет распределяться по оставшимся ресурсам в оставшихся зонах. Подробные рекомендации по работе с балансировщиком читайте в разделе [Рекомендации](../best-practices.md). 

## Состояния сетевого балансировщика {#lb-statuses}

Созданный балансировщик может находиться в одном из состояний, определяющих его поведение:

* `CREATING` — балансировщик находится в процессе создания.
* `STARTING` — балансировщик запускается.
* `ACTIVE` — балансировщик работает, выполняет проверки состояния и передает трафик ресурсам из целевой группы.
* `STOPPING` — балансировщик останавливается.
* `STOPPED` — балансировщик остановлен, не выполняет проверки состояния и не передает трафик.
* `DELETING` — балансировщик удаляется.
* `INACTIVE` — состояние, указывающее, что у балансировщика нет обработчиков или в прикрепленных целевых группах нет целевых ресурсов. Балансировщик не выполняет проверки и не передает трафик.