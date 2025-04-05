---
## Front matter
lang: ru-RU
title: Лабораторная Работа №8. Настройка сетевых сервисов. DHCP
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

Приобретение практических навыков по настройке динамического распределения IP-адресов посредством протокола DHCP (Dynamic Host Configuration
Protocol) в локальной сети

## Добавление сервера dns

![Добавление сервера dns](image/1.png){#fig:001 width=70%}

## Активация порта на коммутаторе

![Активация порта на коммутаторе](image/2.png){#fig:002 width=60%}

## Настройка конфигурации сервера

![Настройка конфигурации сервера](image/3.png){#fig:003 width=70%}

## Окно настройки сервиса DNS

![Окно настройки сервиса DNS](image/4.png){#fig:004 width=60%}

## Настройка DHCP-сервиса на маршрутизаторе

![Настройка DHCP-сервиса на маршрутизаторе,  указание IP-адрес DNS-сервера; настройка DHCP;  название конфигурируемому диапазону адресов (пулу адресов), указание адрес сети,  шлюза и DNS-сервера; задание пулов адресов, исключаемых из динамического распределения ](image/5.png){#fig:005 width=40%}

## Динамическое распределения адресов

![Замена статического распределения адресов на динамическое](image/6.png){#fig:006 width=60%}

## Адреса оконечных устройств

![Адреса оконечных устройств](image/7.png){#fig:007 width=70%}

## Доступность устройств из разных подсетей

![Доступность устройств из разных подсетей](image/8.png){#fig:008 width=60%}

## Запрос адреса по DHCP

![Запрос адреса по DHCP](image/9.png){#fig:009 width=70%}


## Вывод


В ходе выполнения лабораторной работы я приобрел практические навыки по настройке динамического распределения IP-адресов посредством протокола DHCP (Dynamic Host Configuration
Protocol) в локальной сети

