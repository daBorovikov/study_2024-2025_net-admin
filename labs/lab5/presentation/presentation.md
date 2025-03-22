---
## Front matter
lang: ru-RU
title: Лабораторная Работа №6. Статическая маршрутизация VLAN
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

Настроить статическую маршрутизацию VLAN в сети.

## Размещение маршрутизатора 

![Размещение маршрутизатора Cisco 2811](image/1.png){#fig:001 width=70%}

## Конфигурирование маршрутизатора

![Конфигурирование маршрутизатора, удаленной подключение ssh](image/2.png){#fig:002 width=60%}

##  trunk-порт 24

![Порт 24 как trunk-порт](image/3.png){#fig:003 width=70%}

## Переименование маршрутизатора

![Переименование маршрутизатора](image/4.png){#fig:004 width=60%}

## Настройка виртуальных интерфейсов

![Настроим виртуальные интерфейсы, соответствующие номерам VLAN](image/5.png){#fig:005 width=50%}

## ping

![ping](image/6.png){#fig:006 width=50%}

## Процесс передвижения пакета ICMP по сети.

![Процесс передвижения пакета ICMP по сети.](image/7.png){#fig:007 width=70%}

## Содержимое передаваемого пакета

![Содержимое передаваемого пакета](image/8.png){#fig:008 width=60%}



## Вывод

В ходе выполнения лабораторной работы я приобрел практические навыки по настройке статической маршрутизации VLAN в сети.

