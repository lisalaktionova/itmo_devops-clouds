# Лабораторная работа №1 (обычная)

## Задание
Настроить nginx по заданному тз:
1. Должен работать по https c сертификатом
2. Настроить принудительное перенаправление HTTP-запросов (порт 80) на HTTPS (порт 443) для обеспечения безопасного соединения.
3. Использовать alias для создания псевдонимов путей к файлам или каталогам на сервере.
4. Настроить виртуальные хосты для обслуживания нескольких доменных имен на одном сервере.
5. Что угодно еще под требования проекта

## Установка nginx

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
