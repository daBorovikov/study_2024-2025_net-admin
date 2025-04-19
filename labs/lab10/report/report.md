---
## Front matter
title: "Отчёт по лабораторной работе №10"
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

Освоить настройку прав доступа пользователей к ресурсам сети.

#  Задание

1. Требуется настроить следующие правила доступа:

1) web-сервер: разрешить доступ всем пользователям по протоколу HTTP
через порт 80 протокола TCP, а для администратора открыть доступ
по протоколам Telnet и FTP;

2) файловый сервер: с внутренних адресов сети доступ открыт по портам
для общедоступных каталогов, с внешних — доступ по протоколу FTP;

3) почтовый сервер: разрешить пользователям работать по протоколам
SMTP и POP3 [@wiki:bash] (соответственно через порты 25 и 110 протокола TCP),
а для администратора — открыть доступ по протоколам Telnet и FTP;

4) DNS-сервер: открыть порт 53 протокола UDP для доступа из внутренней сети;

5) разрешить icmp-сообщения, направленные в сеть серверов;

6) запретить для сети Other любые запросы за пределы сети, за исключением администратора;

7) разрешить доступ в сеть управления сетевым оборудованием только
администратору сети.

2. Требуется проверить правильность действия установленных правил доступа.

3. Требуется выполнить задание для самостоятельной работы по настройке
прав доступа администратора сети на Павловской.

4. При выполнении работы необходимо учитывать соглашение об именовании

# Выполнение лабораторной работы

В рабочей области проекта подключите ноутбук администратора с именем
admin к сети к other-donskaya-1 (рис. [-@fig:001])с тем, чтобы разрешить ему потом любые
действия, связанные с управлением сетью. Для этого подсоедините ноутбук
к порту 24 коммутатора msk-donskaya-sw-4 и присвойте ему статический
адрес 10.128.6.200, указав в качестве gateway-адреса 10.128.6.1 и адреса
DNS-сервера 10.128.0.5  (рис. [-@fig:002]).

![Подсоединение ноутбука к порту 24 коммутатора sw-4 ](image/1.png){ #fig:001 width=70% }

 

![Присвоение оконечному устройству статического адреса 10.128.6.200, gateway-адреса 10.128.6.1 и адреса DNS-сервера 10.128.0.5](image/2.png){ #fig:002 width=70% }

Следует помнить, что на оборудовании Cisco правила в списке доступа
проверяются по порядку сверху вниз до первого совпадения — как только
одно из правил сработало, проверка списка правил прекращается и обработка
трафика происходит на основе сработавшего правила. Поэтому рекомендуется
сначала дать разрешение (permit) на какое-то действие, а уже потом накладывать ограничения (deny). Кроме того, после всех правил в конце дописывается
неявное запрещение на всё, что не разрешено: deny ip any any (implicit deny).

1. Настройка доступа к web-серверу по порту tcp 80: (рис. [-@fig:003]). 
```
msk−donskaya −gw −1#configure terminal

msk−donskaya −gw −1(config)#ip access −list extended servers −out

msk−donskaya −gw −1(config −ext−nacl)#remark web

msk−donskaya −gw −1(config −ext−nacl)#permit tcp any host 10.128.0.2 eq 80 
```
Здесь: создан список контроля доступа с названием servers-out (так как
предполагается ограничить доступ в конкретные подсети и по отношению к маршрутизатору это будет исходящий трафик); указано (в качестве
комментария-напоминания remark web), что ограничения предназначены
для работы с web-сервером; дано разрешение доступа (permit) по протоколу TCP всем (any) пользователям сети (host) на доступ к web-серверу,
имеющему адрес 10.128.0.2, через порт 80.

2. Добавление списка управления доступом к интерфейсу: (рис. [-@fig:004]). 
```
msk−donskaya −gw −1#configure terminal

msk−donskaya −gw −1(config)#interface f0/0.3

msk−donskaya −gw −1(config −subif)#ip access −group servers −out out
```
Здесь: к интерфейсу f0/0.3 подключается список прав доступа serversout и применяется к исходящему трафику (out).
Можно проверить, что доступ к web-серверу есть через протокол HTTP
(введя в строке браузера хоста ip-адрес web-сервера). (рис. [-@fig:006]).  При этом команда
ping будет демонстрировать недоступность web-сервера как по имени, так
и по ip-адресу web-сервера (рис. [-@fig:005]). 

![Настройка доступа к web-серверу по порту tcp 80 (создан список контроля доступа с названием servers-out; указано, что ограничения предназначены для работы с web-сервером; дано разрешение доступа по протоколу TCP всем пользователям сети на доступ к web-серверу, имеющему адрес 10.128.0.2, через порт 80)](image/3.png){ #fig:003 width=70% }



![Добавление списка управления доступом к интерфейсу (к интерфейсу f0/0.3 подключается список прав доступа serversout и применяется к исходящему трафику)](image/4.png){ #fig:004 width=70% }



![ping](image/5.png){ #fig:005 width=70% }



![Проверка доступа к web-серверу через протокол HTTP](image/6.png){ #fig:006 width=70% }

 3. Дополнительный доступ для администратора по протоколам Telnet и FTP: (рис. [-@fig:007]).
```
msk−donskaya −gw −1#configure terminal

msk−donskaya −gw −1(config)#ip access −list extended servers −out

msk−donskaya −gw −1(config −ext−nacl)#permit tcp host 10.128.6.200 host
 10.128.0.2 range 20 ftp

msk−donskaya −gw −1(config −ext−nacl)#permit tcp host 10.128.6.200 host
 10.128.0.2 eq telnet
```
Здесь: в список контроля доступа servers-out добавлено правило, разрешающее устройству администратора с ip-адресом 10.128.6.200 доступ на
web-сервер (10.128.0.2) по протоколам FTP и telnet.
Убедитесь, что с узла с ip-адресом 10.128.6.200 есть доступ по протоколу
FTP. Для этого в командной строке устройства администратора введите
ftp 10.128.0.2, (рис. [-@fig:008]) а затем по запросу имя пользователя cisco и пароль cisco
Попробуйте провести аналогичную процедуру с другого устройства сети.
Убедитесь, что доступ будет запрещён. (рис. [-@fig:009])

![Настройка дополнительного доступа для администратора по протоколам Telnet и FTP (в список контроля доступа servers-out добавлено правило, разрешающее устройству администратора с ip-адресом 10.128.6.200 доступ на web-сервер (10.128.0.2) по протоколам FTP и telnet)](image/7.png){ #fig:007 width=70% }



![Проверка доступа по протоколу FTP](image/8.png){ #fig:008 width=70% }



![Проверка доступа по протоколу FTP](image/9.png){ #fig:009 width=70% }

4. Настройка доступа к файловому серверу: (рис. [-@fig:010])
```
msk−donskaya −gw −1#configure terminal

msk−donskaya −gw −1(config)#ip access −list extended servers −out

msk−donskaya −gw −1(config −ext−nacl)#remark file

msk−donskaya −gw −1(config −ext−nacl)#permit tcp 10.128.0.0 0.0.255.255
host 10.128.0.3 eq 445

msk−donskaya −gw −1(config −ext−nacl)#permit tcp any host 10.128.0.3 range 20 ftp 
```
Здесь: в списке контроля доступа servers-out указано (в качестве
комментария-напоминания remark file), что следующие ограничения
предназначены для работы с file-сервером; всем узлам внутренней сети
(10.128.0.0) разрешён доступ по протоколу SMB (работает через порт 445
протокола TCP) к каталогам общего пользования; любым узлам разрешён
доступ к file-серверу по протоколу FTP. Запись 0.0.255.255 — обратная
маска (wildcard mask).

![Настройка доступа к файловому серверу (всем узлам внутренней сети (10.128.0.0) разрешён
доступ по протоколу SMB к каталогам общего пользования; любым узлам разрешён доступ к file-серверу по протоколу FTP ](image/10.png){ #fig:010 width=70% }

Настройка доступа к почтовому серверу:  (рис. [-@fig:011])
```
msk−donskaya −gw −1#configure terminal

msk−donskaya −gw −1(config)#ip access −list extended servers −out

msk−donskaya −gw −1(config −ext−nacl)#remark mail

msk−donskaya −gw −1(config −ext−nacl)#permit tcp any host 10.128.0.4 eq smtp

msk−donskaya −gw −1(config −ext−nacl)#permit tcp any host 10.128.0.4 eq pop3
```
Здесь: в списке контроля доступа servers-out указано (всем разрешён доступ
к почтовому серверу по протоколам POP3 и SMTP.

6. Настройка доступа к DNS-серверу: (рис. [-@fig:012])
```
msk−donskaya −gw −1#configure terminal


msk−donskaya −gw −1(config)#ip access −list extended servers −out

msk−donskaya −gw −1(config −ext−nacl)#remark dns

msk−donskaya −gw −1(config −ext−nacl)#permit udp 10.128.0.0 0.0.255.255

host 10.128.0.5 eq 53
```
Здесь: в списке контроля доступа servers-out указано (в качестве
комментария-напоминания remark dns), что следующие ограничения предназначены для работы с DNS-сервером; всем узлам внутренней сети
разрешён доступ к DNS-серверу через UDP-порт 53.
Проверьте доступность web-сервера (через браузер) не только по ip-адресу,
но и по имени. (рис. [-@fig:013])


![Настройка доступа к почтовому серверу (всем разрешён доступ к почтовому серверу по протоколам POP3 и SMTP)](image/11.png){ #fig:011 width=70% }



![Настройка доступа к DNS-серверу (всем узлам внутренней сети разрешён доступ к DNS-серверу
через UDP-порт 53)](image/12.png){ #fig:012 width=70% }



![Проверка доступности web-сервера (через браузер) по имени.](image/13.png){ #fig:013 width=70% }

7. Разрешение icmp-запросов: (рис. [-@fig:014])
```
msk−donskaya −gw −1#configure terminal

msk−donskaya −gw −1(config)#ip access −list extended servers −out

msk−donskaya −gw −1(config −ext−nacl)#1 permit icmp any any
```
Здесь демонстрируется явное управление порядком размещения правил
— правило разрешения для icmp-запросов добавляется в начало списка
контроля доступа. Номера строк правил в списке контроля доступа можно
посмотреть с помощью команды м
msk−donskaya −gw −1#show access −lists
8. Настройка доступа для сети Other (требуется наложить ограничение на
исходящий из сети Other трафик, который по отношению к маршрутизатору
msk-donskaya-gw-1 является входящим трафиком): 
```
msk−donskaya −gw −1#configure terminal

msk−donskaya −gw −1(config)ip access −list extended other −in

msk−donskaya −gw −1(config −ext−nacl)remark admin

msk−donskaya −gw −1(config −ext−nacl)permit ip host 10.128.6.200 any

msk−donskaya −gw −1(config −ext−nacl)exit

msk−donskaya −gw −1(config −subif)interface f0/0.104

msk−donskaya −gw −1(config −subif)ip access −group other −in in
```
Здесь: в списке контроля доступа other-in указано, что следующие правила
относятся к администратору сети; даётся разрешение устройству с адресом

10.128.6.200 на любые действия (any); к интерфейсу f0/0.104 подключается
список прав доступа other-in и применяется к входящему трафику (in).

9. Настройка доступа администратора к сети сетевого оборудования: (рис. [-@fig:016])

```
msk−donskaya −gw −1#configure terminal
msk−donskaya −gw −1(config)#ip access −list extended management −out
msk−donskaya −gw −1(config −ext−nacl)#remark admin
msk−donskaya −gw −1(config −ext−nacl)#permit ip host 10.128.6.200
 10.128.1.0 0.0.0.255
msk−donskaya −gw −1(config −ext−nacl)#exit
msk−donskaya −gw −1(config)#interface f0/0.2
msk−donskaya −gw −1(config −subif)#ip access −group management −out out
```

Здесь: в списке контроля доступа management-out указано (в качестве
комментария-напоминания remark admin), что устройству администратора с адресом 10.128.6.200 разрешён доступ к сети сетевого оборудования
(10.128.1.0); к интерфейсу f0/0.2 подключается список прав доступа
management-out и применяется к исходящему трафику (out).

![ Разрешение icmp-запросов ( icmp-запрос добавляется в начало списка контроля доступ) ](image/14.png){ #fig:014 width=70% }



![Настройка доступа для сети Other (разрешение устройству с адресом 10.128.6.200 на любые действия; подключение к интерфейсу f0/0.104 списка прав доступа other-in и применение к входящему трафику)](image/15.png){ #fig:015 width=70% }



![Настройка доступа администратора к сети сетевого оборудования ( 10.128.6.200 разрешён доступ к сети сетевого оборудования (10.128.1.0); к интерфейсу f0/0.2 подключён список прав доступа management-out и применено к исходящему трафику)](image/16.png){ #fig:016 width=70% }


# Самостоятельная работа

1. Проверьте корректность установленных правил доступа, попытавшись получить доступ по различным протоколам с разных устройств сети к подсети
серверов и подсети сетевого оборудования. (рис. [-@fig:017])

2. Разрешите администратору из сети Other на Павловской действия, аналогичные действиям администратора сети Other на Донской. (рис. [-@fig:018]) (рис. [-@fig:019]) (рис. [-@fig:020])

![ping ftp](image/17.png){ #fig:017 width=70% }



![Разрешение администратору из сети Other на Павловской действия, аналогичные действиям администратора сети Other на Донской.](image/18.png){ #fig:018 width=70% }



![Разрешение администратору из сети Other на Павловской действия, аналогичные действиям администратора сети Other на Донской.](image/19.png){ #fig:019 width=70% }



![ Проверка разрешений администратора из сети Other на
Павловской.](image/20.png){ #fig:020 width=70% }





##  Контрольные вопросы

1. Как задать действие правила для конкретного протокола? permit…

2. Как задать действие правила сразу для нескольких портов? - …range…

3. Как узнать номер правила в списке прав доступа? – show access-lists

4. Каким образом можно изменить порядок применения правил в списке
контроля доступа? ip access-list resequence…


# Выводы

В ходе выполнения лабораторной работы я освоил настройку прав доступа пользователей к ресурсам сети.


# Список литературы{.unnumbered}

::: {#refs}
:::

