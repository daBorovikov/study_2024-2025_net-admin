---
## Front matter
lang: ru-RU
title: Лабораторная Работа №5. Конфигурирование VLAN
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

Получить основные навыки по настройке VLAN на коммутаторах сети.

## Конфигурация Trunk-порта

![Конфигурация Trunk-порта msk-donskaya-sw-1](image/1.png){#fig:001 width=70%}

## Конфигурация Trunk-порта

![Конфигурация Trunk-порта msk-donskaya-sw-2](image/2.png){#fig:002 width=60%}

## Конфигурация Trunk-порта

![Конфигурация Trunk-порта msk-donskaya-sw-3](image/3.png){#fig:003 width=70%}

## Конфигурация Trunk-порта

![Конфигурация Trunk-порта msk-donskaya-sw-4](image/4.png){#fig:004 width=60%}

## Конфигурация Trunk-порта

![Конфигурация Trunk-порта msk-pavlovskaya-sw-1](image/5.png){#fig:005 width=70%}

## msk-donskaya-sw-1 как VTP-сервер

![msk-donskaya-sw-1 как VTP-сервер](image/6.png){#fig:006 width=60%}

## VTP-клиент

![msk-donskaya-sw-2 как VTP-клиент](image/7.png){#fig:007 width=70%}

## VTP-клиент

![msk-donskaya-sw-3 как VTP-клиент](image/8.png){#fig:008 width=60%}

## VTP-клиент

![msk-donskaya-sw-4 как VTP-клиент](image/9.png){#fig:009 width=70%}

## VTP-клиент

![msk-pavlovskaya-sw-1 как VTP-клиент](image/10.png){#fig:010 width=60%}

## Статический IP-адрес

![Пример указания статического IP-адреса](image/11.png){#fig:011 width=70%}

## Статический IP-адрес

![Пример указания статического IP-адреса](image/12.png){#fig:012 width=60%}

## ping

![ping](image/13.png){#fig:013 width=70%}

## Процесс передвижения пакета ICMP

![Процесс передвижения пакета ICMP](image/14.png){#fig:014 width=60%}

## Содержимое пакета

![Содержимое пакета](image/15.png){#fig:015 width=70%}



## Вывод

В ходе выполнения лабораторной работы я получил основные навыки по настройке VLAN на коммутаторах сети

