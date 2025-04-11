---
## Front matter
lang: ru-RU
title: Лабораторная Работа №9. Использование протокола STP. Агрегирование каналов
subtitle: Сетевой администрирование
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

Изучение возможностей протокола STP и его модификаций по обеспечению
отказоустойчивости сети, агрегированию интерфейсов и перераспределению
нагрузки между ними.

## Логическая схема локальной сети с резервным соединением

![Логическая схема локальной сети с резервным соединением](image/1.png){#fig:001 width=70%}

## g0/2 mode trunk

![g0/2 mode trunk](image/2.png){#fig:002 width=60%}

## sw-1 и sw-4 через интерфейсы Fa0/23

![sw-1 и sw-4 через интерфейсы Fa0/23](image/3.png){#fig:003 width=70%}

## sw-1 mode trunk

![sw-1 mode trunk](image/4.png){#fig:004 width=60%}

## sw-4 mode trunk

![sw-4 mode trunk](image/5.png){#fig:005 width=70%}

## ping

![ping](image/6.png){#fig:006 width=60%}

## движение пакетов через sw-2

![движение пакетов через sw-2](image/7.png){#fig:007 width=70%}

## Состояние протокола STP

![Состояние протокола STP](image/8.png){#fig:008 width=60%}

## sw-1 в качестве корневого коммутатора STP

![sw-1 в качестве корневого коммутатора STP](image/9.png){#fig:009 width=70%}

## mail через sw-3

![mail через sw-3](image/10.png){#fig:010 width=60%}

## web через sw-2

![web через sw-2](image/11.png){#fig:011 width=70%}

## Настройка режима Portfast sw-2

![Настройка режима Portfast sw-2](image/12.png){#fig:012 width=60%}

## Настройка режима Portfast sw-3

![Настройка режима Portfast sw-3](image/13.png){#fig:013 width=70%}

## Отказоустойчивость протокола STP

![Отказоустойчивость протокола STP](image/14.png){#fig:014 width=60%}

## Режим работы по протоколу Rapid PVST+

![Режим работы по протоколу Rapid PVST+](image/15.png){#fig:015 width=70%}

## Отказоустойчивость протокола Rapid PVST+

![Отказоустойчивость протокола Rapid PVST+](image/16.png){#fig:016 width=60%}

## Логическая схема локальной сети с агрегированным соединением

![Логическая схема локальной сети с агрегированным соединением](image/17.png){#fig:017 width=70%}

## sw-1 агрегирование каналов (режим EtherChannel)

![sw-1 агрегирование каналов (режим EtherChannel)](image/18.png){#fig:018 width=60%}

## sw-4 агрегирование каналов (режим EtherChannel)

![sw-4 агрегирование каналов (режим EtherChannel)](image/19.png){#fig:019 width=70%}



## Вывод

В ходе выполнения лабораторной работы я изучил возможности протокола STP и его модификаций по обеспечению
отказоустойчивости сети, агрегированию интерфейсов и перераспределению
нагрузки между ними.
