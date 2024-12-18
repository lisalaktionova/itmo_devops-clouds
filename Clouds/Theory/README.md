# Рубежка 1. Вариант №3
> Когда понадобится публичное облако, а когда частное?

Облака можно разделить по способу развертывания, то есть по тому, где находится облако. Это может быть либо `частное` облако у компании, например, у Яндекса есть свое облако, датацентры, которые они используют только внутри себя. Либо может быть `публичное` облако, например Yandex Cloud, который предоставляет свои сервисы всем пользователям. Также существует `гибридное` облако (то есть компания использует и то и другое - что-то хостится локально, а что-то в публичном облаке, и всё вместе это образует гибридную инфраструктуру).

Немного подробнее про каждое из облаков:

**Частное облако**
* Безопасность — данные хранятся в защищённом сегменте, а доступ к инфраструктуре регулируется правами доступа и ролями пользователей;
* Кастомизация — элементы облачной инфраструктуры могут быть изменены в будущем в зависимости от бизнес-задач;
* Изолированность инфраструктуры — частное облако использует изолированные ресурсы, доступные только владельцу облака;
* Конфигурируемость системы — в любой момент облачная инфраструктура может быть изменена по усмотрению владельца.
  
**Публичное облако**
* Быстрый выпуск продукта — инструменты и сервисы облака сокращают время выпуска продукта на рынок;
* Разгрузка внутреннего ИТ-отдела — техподдержка облачного провайдера разгружает клиентские ИТ-отделы;
* Автоматизация — инструменты и сервисы публичного облака имеют API для удалённого управления через специализированные программы, такие как Ansible, Terraform, Jenkins и другие;
* Резервирование мощностей — при пиковых нагрузках дополнительные мощности можно быстро получить из публичного облака.


#### Чтобы лучше в этом разобраться, рассмотрим несколько примеров.

Представим, что нам нужно изобрести какой-то сервис, которого нет, например, в Яндексе/Amazon, то тогда стоит использовать частное облако, так как в нем можно самому кастомизировать нужный сервис. Также у частного облака изолированные ресурсы, то есть они доступны только владельцу облака, поэтому данные компании можно защищать так, как ей нужно, и переместить их ближе к пользователю. Например, если компания находится в Хабаровске (а там нет датацентра Яндекса:)), то можно развернуть сервис в частном облаке в Хабаровске, и он будет ближе к пользователям из Хабаровска. И еще один преимуществом частного облака явлеяется конфигурируемость системы, то есть в любой момент ее можно переконфигурировать так, как нужно бизнесу.

Если компания хочет разгрузить внутренний IT-отдел, то стоит использовать публичное облака. Самостоятельно ничего не надо будет строить, контролировать ресурсы, которые конечны в частном облаке. То есть всё будет автоматизированно через консоль провайдера. Также если сервис дорого разрабатывать и долго внедрять, то удобнее запросить, например, у Yandex Cloud этот сервис в публичном облаке. Также в публичном облаке можно всё контролировать через программироваемые интерфейсы (API), управлять удаленно, заказывать ресурсов столько, сколько нужно и,соответсвенно, платить за это столько, сколько потребуется.

Однако большинство компаний стремятся построить гибридное облако.

# Рубежка 2. Вариант №
