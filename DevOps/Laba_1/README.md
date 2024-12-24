# Лабораторная работа №1 (обычная)

## Задание
Настроить nginx по заданному тз:
1. Должен работать по https c сертификатом
2. Настроить принудительное перенаправление HTTP-запросов (порт 80) на HTTPS (порт 443) для обеспечения безопасного соединения.
3. Использовать alias для создания псевдонимов путей к файлам или каталогам на сервере.
4. Настроить виртуальные хосты для обслуживания нескольких доменных имен на одном сервере.
5. Что угодно еще под требования проекта

## Решение

С помощью следующих команд обновим пакеты и установим nginx:
```bash
sudo apt-get update
```
![Обновление пакетов](https://github.com/lisalaktionova/itmo_devops-clouds/blob/main/DevOps/Laba_1/update.png)

```bash
sudo apt install nginx
```
![Установка nginx](https://github.com/lisalaktionova/itmo_devops-clouds/blob/main/DevOps/Laba_1/install_nginx.png)

Запустим nginx и проверим его статус:
```bash
sudo systemctl start nginx
```
```bash
sudo systemctl status nginx
```
![](https://github.com/lisalaktionova/itmo_devops-clouds/blob/main/DevOps/Laba_1/start_nginx.png)


Затем создадим каталоги для проектов и настроим права доступа с помощью ```sudo chown``` и других команд, изображенных на скриншоте:

![]([img/img_1.png](https://github.com/lisalaktionova/itmo_devops-clouds/blob/main/DevOps/Laba_1/1.png))

Следующим шагом будет установка ssl и генерация самоподписанного сертификата. SSL устанавливается командой ```sudo apt install openssl```, 
а сертификат генерируется с помощью ```sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/nginx/ssl/nginx.key -out /etc/nginx/ssl/nginx.crt```.
Процесс его настройки изображен на скриншоте:

![](https://github.com/lisalaktionova/itmo_devops-clouds/blob/main/DevOps/Laba_1/1.png)

Когда мы приготовили все инструменты, настало время приступать к самой лабораторной. Будем настраивать виртуальные хосты,
для этого пропишем ```sudo nano /etc/nginx/sites-available/proj1```, у нас откроется конфигурация виртуального хоста первого проекта,
в ней мы должны написать следующее:

![](https://github.com/lisalaktionova/itmo_devops-clouds/blob/main/DevOps/Laba_1/1.png)

В ней мы указали доменное имя (server_name), перенаправление с http на https, путь к ssl сертификату, который мы подписали
заранее, указали, где искать файлы проекта (root /var/www/proj1) и установили index.html в качестве главной страницы сайта.
Со вторым проектом все аналогично, поэтому просто оставим его конфиг здесь:

![](https://github.com/lisalaktionova/itmo_devops-clouds/blob/main/DevOps/Laba_1/1.png)

После внесения этих изменений файлы нужно активировать, создав символические ссылки в директории /etc/nginx/sites-enabled/
с помощью следующих команд:

```bash
sudo ln -s /etc/nginx/sites-available/proj1 /etc/nginx/sites-enabled/
sudo ln -s /etc/nginx/sites-available/proj2 /etc/nginx/sites-enabled/
```

Далее перезагрузим nginx командой ```sudo systemctl restart nginx``` для того, чтобы все изменения вступили в силу. Теперь
нам надо узнать IP-адрес нашей машины, на которой установлен nginx. Делается это с помощью команды ```hostname -I```. Этот
IP-адрес будет использоваться для связи между нашим компьютером и виртуальными хостами Nginx.

Следующим шагом нам надо будет отредактировать /etc/hosts, который используется для сопоставления доменных имен и IP-адресов
на локальном уровне, минуя DNS-серверы. Открываем его с помощью ```sudo nano /etc/hosts``` и добавляем в него следующие строки:

```
your_server_ip  proj1.example.com
your_server_ip  proj2.example.com
```
На месте ```your_server_ip``` должен быть адрес нашей виртуальной машины, а proj1.example.com и proj2.example.com будут 
доменными именами наших проектов. Ниже прикреплен скриншот того, как выглядит наш hosts:

![](https://github.com/lisalaktionova/itmo_devops-clouds/blob/main/DevOps/Laba_1/1.png)

Далее переходим в браузере по адресам и , и, как видим, все работает +
реализовано автоматическое перенаправление на https.

![](https://github.com/lisalaktionova/itmo_devops-clouds/blob/main/DevOps/Laba_1/1.png)

![](https://github.com/lisalaktionova/itmo_devops-clouds/blob/main/DevOps/Laba_1/1.png)

![]()
