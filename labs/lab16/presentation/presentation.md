---
## Front matter
lang: ru-RU
title: Лабораторная Работа №16.  Настройка VPN
subtitle: Администрирование локальных сетей 
author:
  - Боровиков Д.А.
institute:
  - Российский университет дружбы народов им. Патриса Лумумбы, Москва, Россия

## i18n babel
babel-lang: russian
babel-otherlangs: english

## Formatting pdf
toc: false
toc-title: Содержание
slide_level: 2
aspectratio: 169
section-titles: true
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
 - '\makeatletter'
 - '\beamer@ignorenonframefalse'
 - '\makeatother'

## Fonts
mainfont: Arial
romanfont: Arial
sansfont: Arial
monofont: Arial
---


## Докладчик


  * Боровиков Даниил Александрович
  * НПИбд-01-22
  * Российский университет дружбы народов
  * [1132222006@pfur.ru]


## Цели и задачи

Получение навыков настройки VPN-туннеля через незащищённое Интернет-соединение.

## Размещение оборудования

![Размещение оборудования в рабочей области проекта.](image/1.png){#fig:001 width=70%}

## Repeater-PT

![Замена модулей на Repeater-PT](image/2.png){#fig:002 width=60%}

## Подключение оборудования

![Подключение оборудования](image/3.png){#fig:003 width=70%}

## Создание города Пиза

![Создание города Пиза в физической рабочей области](image/4.png){#fig:004 width=60%}

## Перемещение оборудования

![Перемещение оборудования](image/5.png){#fig:005 width=70%}

## pisa-unipi-daborovikov-gw-1

![Первоначальная настройка маршрутизатора pisa-unipi-daborovikov-gw-1](image/6.png){#fig:006 width=60%}

## pisa-unipi-daborovikov-sw-1

![Первоначальная настройка коммутатора pisa-unipi-daborovikov-sw-1](image/7.png){#fig:007 width=70%}

## pisa-unipi-daborovikov-gw-1

![Настройка интерфейсов маршрутизатора pisa-unipi-daborovikov-gw-1](image/8.png){#fig:008 width=60%}

## pisa-unipi-daborovikov-sw-1

![Настройка интерфейсов коммутатора pisa-unipi-daborovikov-sw-1](image/9.png){#fig:009 width=70%}

## Присвоение адресов

![Присвоение адресов оконечному устройству](image/10.png){#fig:010 width=60%}

## Пинг

![Пинг адреса 10.131.0.1](image/11.png){#fig:011 width=70%}

## VPN

![Настройка маршрутизатора msk-donskaya-daborovikov-gw-1](image/12.png){#fig:012 width=60%}

## VPN

![Настройка маршрутизатора pisa-unipi-daborovikov-gw-1](image/13.png){#fig:013 width=70%}

## VPN

![Проверка доступности узлов сети Университета г. Пиза с ноутбука администратора сети «Донская»](image/14.png){#fig:014 width=60%}


## Вывод

В ходе выполнения лабораторной работы мы получили навыки настройки
VPN-туннеля через незащищённое Интернет-соединение.
