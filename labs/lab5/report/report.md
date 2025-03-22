---
## Front matter
title: "Отчёт по лабораторной работе №6"
subtitle: "Дисциплина: Администрирование локальных сетей"
author: "Боровиков Даниил Александрович НПИбд-01-22"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: Arial
romanfont: Arial
sansfont: Arial
monofont: Arial
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Настроить статическую маршрутизацию VLAN в сети.

#  Задание

1. Добавить в локальную сеть маршрутизатор, провести его первоначальную
настройку.

2. Настроить статическую маршрутизацию VLAN[@wiki:bash].

3. При выполнении работы необходимо учитывать соглашение об именовании

# Выполнение лабораторной работы

 В логической области проекта разместим маршрутизатор Cisco 2811, подключим его к порту 24 коммутатора msk-donskaya-sw-1 (рис. [-@fig:001])

![Размещение маршрутизатора Cisco 2811](image/1.png){ #fig:001 width=70% }

Используя приведённую ниже последовательность команд по первоначальной настройке маршрутизатора, сконфигурируем маршрутизатор, задав на
нём имя, пароль для доступа к консоли, настроим удалённое подключение
к нему по ssh(рис. [-@fig:002]). 

![Конфигурирование маршрутизатора, удаленной подключение ssh](image/2.png){ #fig:002 width=70% }

Настроим порт 24 коммутатора msk-donskaya-sw-1 как trunk-порт.(рис. [-@fig:003]). 

![Порт 24 как trunk-порт](image/3.png){ #fig:003 width=70% }

Переименуем маршрутизатор(рис. [-@fig:004]). 

![Переименование маршрутизатора](image/4.png){ #fig:004 width=70% }

На интерфейсе f0/0 маршрутизатора msk-donskaya-gw-1 настроим виртуальные интерфейсы, соответствующие номерам VLAN. Зададим соответствующие IP-адреса
на виртуальных интерфейсах. Для этого используем приведённую ниже
последовательность команд по конфигурации VLAN-интерфейсов маршрутизатора.(рис. [-@fig:005]). 

![Настроим виртуальные интерфейсы, соответствующие номерам VLAN](image/5.png){ #fig:005 width=70% }

Проверим доступность оконечных устройств из разных VLAN.(рис. [-@fig:006]). 

![ping](image/6.png){ #fig:006 width=70% }

Используя режим симуляции в Packet Tracer, изучиv процесс передвижения пакета ICMP по сети.  (рис. [-@fig:007]).

![Процесс передвижения пакета ICMP по сети.](image/7.png){ #fig:007 width=70% }

Изучим содержимое передаваемого пакета
и заголовки задействованных протоколов.(рис. [-@fig:008])

![Содержимое передаваемого пакета](image/8.png){ #fig:008 width=70% }

##  Контрольные вопросы

**1. Охарактеризуйте стандарт IEEE 802.1Q.**
  
Стандарт IEEE 802.1Q — это сетевой стандарт, разработанный для реализации технологии VLAN (Virtual Local Area Network) в Ethernet-сетях. Он позволяет разделять физическую сеть на несколько логических сетей, обеспечивая изоляцию трафика и повышая эффективность использования ресурсов. Основная идея заключается во внедрении тега VLAN в кадр Ethernet, что позволяет коммутаторам идентифицировать, к какой VLAN относится конкретный кадр. IEEE 802.1Q поддерживает до 4096 виртуальных сетей (идентификаторы VLAN от 0 до 4095), хотя 0 и 4095 обычно зарезервированы. Этот стандарт широко используется в корпоративных сетях для сегментации трафика, повышения безопасности и управления пропускной способностью.

**2. Опишите формат кадра IEEE 802.1Q.** 
 
Кадр IEEE 802.1Q представляет собой модифицированный кадр Ethernet, в который добавлен тег VLAN длиной 4 байта. Формат кадра выглядит следующим образом:  

- **Преамбула (7 байт)** и **SFD (Start Frame Delimiter, 1 байт)** — стандартные поля Ethernet для синхронизации. 
 
- **MAC-адрес получателя (6 байт)** — адрес устройства-получателя. 
 
- **MAC-адрес отправителя (6 байт)** — адрес устройства-отправителя.  

- **Тег 802.1Q (4 байта)**:  

  - **TPID (Tag Protocol Identifier, 2 байта)** — идентификатор протокола тега, обычно равен 0x8100, указывает на использование 802.1Q.  

  - **TCI (Tag Control Information, 2 байта)**: 
 
    - **PCP (Priority Code Point, 3 бита)** — приоритет кадра (0–7) для QoS.  

    - **DEI (Drop Eligible Indicator, 1 бит)** — индикатор возможности отбрасывания кадра при перегрузке.  

    - **VID (VLAN Identifier, 12 бит)** — идентификатор VLAN (0–4095).  

- **Тип/длина (2 байта)** — указывает тип данных или длину полезной нагрузки.  

- **Данные (46–1500 байт)** — полезная нагрузка кадра.  

- **FCS (Frame Check Sequence, 4 байта)** — контрольная сумма для проверки целостности кадра.  

Тег 802.1Q вставляется между полями MAC-адреса отправителя и Тип/длина, увеличивая максимальную длину кадра с 1518 до 1522 байт.

# Выводы

В ходе выполнения лабораторной работы я приобрел практические навыки по настройке статической маршрутизации VLAN в сети.


# Список литературы{.unnumbered}

::: {#refs}
:::
