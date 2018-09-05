# Взаимосвязь ресурсов в [!KEYREF mdb-short-name]

Все ресурсы в [!KEYREF mdb-short-name] можно разделить на 3 типа:
* _Основные_ ресурсы — [виртуальные машины](vm.md) и [диски](disk.md).
* _Вспомогательные_ ресурсы — [снимки](snapshot.md) и [образы](images.md). Эти ресурсы используются только для создания других ресурсов.
* _Информационные_ ресурсы — тип диска и зона доступности. Эти ресурсы доступны только для чтения.

Помимо этого при создании виртуальных машин используются ресурсы других сервисов: подсети и каталоги.


## Основные ресурсы

Сервис [!KEYREF mdb-short-name] позволяет создавать виртуальные машины и подключать к ним диски.

К виртуальной машине должен быть подключен как минимум один диск — загрузочный. Диск может быть восстановлен из снимка, из образа или создан пустым.


## Вспомогательные ресурсы

Основное назначение снимков и образов — сохранение и восстановление дисков с данными.

Снимок может быть создан только из диска. В информации о снимке содержится идентификатор диска, из которого снимок был сделан.

Образ может быть создан из диска, снимка, другого образа или из файла.


## Информационные ресурсы

При создании дисков и виртуальных машин необходимо указать зону доступности, в которой они будут находиться (образы и снимки дисков не привязываются к зонам доступности).

Вы можете посмотреть посмотреть список зон доступности и узнать их текущий статус.

При создании диска также указывается тип диска. Вы можете посмотреть возможные типы диска и узнать, в каких зонах они доступны.

## Связь с ресурсами других сервисов

При создании виртуальной машины указывается подсеть, к которой она будет подключена. [Подробнее об облачных сетях](../../vpc/concepts/network.md).

Все ресурсы [!KEYREF service-name-short] создаются внутри каталогов. Типы дисков и зоны доступности — публичные ресурсы, которые не относятся к каталогу. [Подробнее об иерархии ресурсов в Облаке](../../resource-manager/concepts/resources-hierarchy.md).