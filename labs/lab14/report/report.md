---
## Front matter
title: "Отчёт по лабораторной работе №14"
subtitle: "Дисциплина: Администрирование сетевых подсистем"
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

Настроить взаимодействие через сеть провайдера посредством статической
маршрутизации локальной сети организации с сетью основного здания, расположенного в 42-м квартале в Москве, и сетью филиала, расположенного
в г. Сочи.

#  Задание

1. Настроить связь между территориями .

2. Настроить оборудование, расположенное в квартале 42 в Москве .

3. Настроить оборудование, расположенное в филиале в г. Сочи .

4. Настроить статическую маршрутизацию между территориями.

5. Настроить статическую маршрутизацию на территории квартала 42 в г.
Москве .

6. Настроить NAT на маршрутизаторе msk-donskaya-gw-1 .

7. При выполнении работы необходимо учитывать соглашение об именовании.


# Выполнение лабораторной работы



Первым делом нам нужно настроить линку между площадками. Для этого
настроим интерфейсы у коммутатора provider-daborovikov-sw-1, маршрутизатора
msk-donskaya-daborovikov-gw-1, маршрутизатора msk-q42-daborovikov-gw-1,
коммутатора sch-sochi-daborovikov-sw-1 и маршрутизатора sch-sochi-daborovikov-gw-1 
 (рис. [-@fig:001])

![Настройка интерфейсов коммутатора provider-daborovikov-sw-1.](image/1.png){ #fig:001 width=70% }

(рис. [-@fig:002]). 

![Настройка интерфейсов маршрутизатора msk-donskaya-daborovikovgw-1.](image/2.png){ #fig:002 width=70% }

(рис. [-@fig:003]). 

![Настройка интерфейсов маршрутизатора msk-q42-daborovikov-gw-1.](image/3.png){ #fig:003 width=70% }

(рис. [-@fig:004]). 

![Выполнение проверки.](image/4.png){ #fig:004 width=70% }

(рис. [-@fig:005]). 

![Настройка интерфейсов коммутатора sch-sochi-daborovikov-sw-1.](image/5.png){ #fig:005 width=70% }

(рис. [-@fig:006]). 

![Настройка интерфейсов маршрутизатора sch-sochi-daborovikov-gw-1.](image/6.png){ #fig:006 width=70% }

 (рис. [-@fig:007]).

![Выполнение проверки.](image/7.png){ #fig:007 width=70% }



Следующим шагом настроим площадку 42-го квартала. Для этого настроим
интерфейсы у маршрутизатора msk-q42-daborovikov-gw-1, коммутатора msk-q42-
daborovikov-sw-1, маршрутизирующего коммутатора msk-hostel-daborovikov-gw-1 и
коммутатора msk-hostel-sw-1 
(рис. [-@fig:008])

![Настройка интерфейсов маршрутизатора msk-q42-daborovikov-gw-1.](image/8.png){ #fig:008 width=70% }

(рис. [-@fig:009])

![Настройка интерфейсов коммутатора msk-q42-daborovikov-sw-1.](image/9.png){ #fig:009 width=70% }

(рис. [-@fig:010])

![Присвоение адресов оконечному устройству pc-q42-1.](image/10.png){ #fig:010 width=70% }

 (рис. [-@fig:011])

![Выполнение проверки.](image/11.png){ #fig:011 width=70% }

(рис. [-@fig:012])

![Настройка интерфейсов маршрутизирующего коммутатора mskhostel-daborovikov-gw-1.](image/12.png){ #fig:012 width=70% }

(рис. [-@fig:013])

![Выполнение проверки.](image/13.png){ #fig:013 width=70% }

(рис. [-@fig:014])

![Настройка интерфейсов коммутатора msk-hostel-sw-1.](image/14.png){ #fig:014 width=70% }

(рис. [-@fig:015])

![Присвоение адресов оконечному устройству pc-hostel-1.](image/15.png){ #fig:015 width=70% }

(рис. [-@fig:016])

![Выполнение проверки.](image/16.png){ #fig:016 width=70% }


 
Далее настроим площадку в Сочи. Настроим интерфейсы у маршрутизатора
sch-sochi-daborovikov-gw-1 и у коммутатора sch-sochi-daborovikov-sw-1 

(рис. [-@fig:017])

![Первоначальная настройка маршрутизатора sch-sochi-daborovikov-gw-1.](image/17.png){ #fig:017 width=70% }

(рис. [-@fig:018])

![Первоначальная настройка коммутатора sch-sochi-daborovikov-sw-1.](image/18.png){ #fig:018 width=70% }

(рис. [-@fig:019])

![Присвоение адресов оконечному устройству pc-sochi-1.](image/19.png){ #fig:019 width=70% }


Затем настроим маршрутизацию между площадками. Настроим
маршрутизатор msk-donskaya-daborovikov-gw-1, маршрутизатор msk-q42-daborovikovgw-1 и маршрутизатор sch-sochi-daborovikov-gw-1 

(рис. [-@fig:020])

![Настройка маршрутизатора msk-donskaya-daborovikov-gw-1.](image/20.png){ #fig:020 width=70% }

(рис. [-@fig:021])

![Выполнение проверки.](image/21.png){ #fig:021 width=70% }

(рис. [-@fig:022])

![Настройка маршрутизатора msk-q42-daborovikov-gw-1.](image/22.png){ #fig:022 width=70% }

(рис. [-@fig:023])

![Выполнение проверки.](image/23.png){ #fig:023 width=70% }

(рис. [-@fig:024])

![Настройка маршрутизатора sch-sochi-daborovikov-gw-1.](image/24.png){ #fig:024 width=70% }


Предпоследним шагом настроим маршрутизацию на 42 квартале. Для этого
настроим маршрутизатор msk-q42-daborovikov-gw-1 (Рис. 1.26) и маршрутизирующий
коммутатор msk-hostel-daborovikov-gw-1 (Рис. 1.27):

(рис. [-@fig:025])

![Настройка маршрутизатора msk-q42-daborovikov-gw-1.](image/25.png){ #fig:025 width=70% }

(рис. [-@fig:026])

![Настройка интерфейсов маршрутизирующего коммутатора mskhostel-daborovikov-gw-1.](image/26.png){ #fig:026 width=70% }



И наконец последним шагом настроим NAT [@wiki:bash] на маршрутизаторе mskdonskaya-daborovikov-gw-1  и выполним контрольную проверку 
(рис. [-@fig:027])

![Настройка NAT на маршрутизаторе msk-donskaya-daborovikov-gw1. ](image/27.png){ #fig:027 width=70% }

(рис. [-@fig:028])

![Контрольная проверка.](image/28.png){ #fig:028 width=70% }


##  Контрольные вопросы


1. Приведите пример настройки статической маршрутизации между
двумя подсетями организации. - Необходимо задать IP шлюзов на
интерфейсах, настроить sub-интерфейсы с тегированием кадром
VLAN'нами и своими IP, затем настроить статические маршруты
между сетями.

2. Опишите процесс обращения устройства из одного VLAN к устройству
из другого VLAN. - 1 устройство посылает фрейм на
маршрутизатор, тот меняет MAC исходника на свой и
перенаправляет фрейм 2 устройству.

3. Как проверить работоспособность маршрута? - ping на диаметрально
противоположных устройствах друг к другу.

4. Как посмотреть таблицу маршрутизации? - show ip route


# Выводы

В ходе выполнения лабораторной работы я настроил взаимодействие через сеть провайдера посредством статической
маршрутизации локальной сети организации с сетью основного здания, расположенного в 42-м квартале в Москве, и сетью филиала, расположенного
в г. Сочи.


# Список литературы{.unnumbered}

::: {#refs}
:::


