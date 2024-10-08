---
## Front matter
title: "Лабораторная работа №2"
subtitle: "Отчёт к лабораторной работе"
author: "Зайцева Анна Дмитриевна"

## Generic options
lang: ru-RU

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
## Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
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

Цель работы --- Получение практических навыков работы в консоли с атрибутами файлов, закрепление теоретических основ дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux.

# Задание

- Последовательно выполнить все пункты (указанные в файле с заданием к лабораторной работе №2), занося ответы на поставленные вопросы и замечания в отчёт.

# Выполнение лабораторной работы

1) В установленной при выполнении предыдущей лабораторной работы операционной системе создала учётную запись пользователя guest (используя учётную запись администратора) с помощью команды *sudo useradd guest* (Рис. [-@fig:001]):

![Рис. 1](lab02_pictures/1.png){ #fig:001 width=70% }

2) Задала пароль для пользователя guest (использую учётную запись администратора): *sudo passwd guest* (Рис. [-@fig:002]):

![Рис. 2](lab02_pictures/2.png){ #fig:002 width=70% }

3) Вошла в систему от имени пользователя guest.

4) Определила директорию, в которой нахожусь, командой *pwd* (Рис. [-@fig:003]). Сравнила её с приглашением командной строки.

![Рис. 3](lab02_pictures/3.png){ #fig:003 width=70% }

5) Уточнила имя пользователя командой *whoami* (Рис. [-@fig:004]):

![Рис. 4](lab02_pictures/4.png){ #fig:004 width=70% }

6) Уточнила имя пользователя, его группу, а также группы, куда входит пользователь, командой id. Выведенные значения uid, gid и др. запомнила. Сравнила вывод id с выводом команды groups (Рис. [-@fig:005]):

![Рис. 5](lab02_pictures/5.png){ #fig:005 width=70% }

7) Сравнила полученную информацию об имени пользователя с данными, выводимыми в приглашении командной строки.

8) Просмотрела файл /etc/passwd командой *cat /etc/passwd* Нашла в нём свою учётную запись. Определила uid пользователя. Определила gid пользователя. И всё это нашла командой *cat /etc/passwd | grep gues* Сравнила найденные значения с полученными в предыдущих пунктах (Рис. [-@fig:006]):

![Рис. 6](lab02_pictures/6.png){ #fig:006 width=70% }

9) Определила существующие в системе директории командой *ls -l /home/*. Удалось получить список поддиректорий директории /home. Права, установленные на директориях изображены на (Рис. [-@fig:007]):

![Рис. 7](lab02_pictures/7.png){ #fig:007 width=70% }

10) Проверила, какие расширенные атрибуты установлены на поддиректориях, находящихся в директории /home, командой: *lsattr /home*
Увидеть расширенные атрибуты директории удалось.
Увидеть расширенные атрибуты директорий других пользователей не удалось. (Рис. [-@fig:008]):

![Рис. 8](lab02_pictures/8.png){ #fig:008 width=70% }

11) Создала в домашней директории поддиректорию dir1 командой *mkdir dir1*
Определила командами *ls -l* и *lsattr*, какие права доступа и расширенные атрибуты были выставлены на директорию dir1. (Рис. [-@fig:009]):

![Рис. 9](lab02_pictures/9.png){ #fig:009 width=70% }

12) Сняла с директории dir1 все атрибуты командой *chmod 000 dir1* и проверила с её помощью правильности выполнения команды *ls -l*  (Рис. [-@fig:010]):

![Рис. 10](lab02_pictures/10.png){ #fig:010 width=70% }

13) Попыталась создать в директории dir1 файл file1 командой *echo "test" > /home/guest/dir1/file1*
Доступ был заблокирован, поскольку мы его ограничили, выполняя условия пункта 12.
Оценила, как сообщение об ошибке отразилось на создании файла. Проверила командой *ls -l /home/guest/dir1* действительно ли файл file1 не находится внутри директории dir1.  (Рис. [-@fig:011]):

![Рис. 11](lab02_pictures/11.png){ #fig:011 width=70% }

14) Заполнила таблицу **«Установленные права и разрешённые действия»** (см. табл. 2.1 в указаниях к лабораторной), выполняя действия от имени владельца директории (файлов), определив опытным путём, какие операции разрешены, а какие нет.
Если операция разрешена, занесла в таблицу знак «+», если не разрешена, знак «-».

| **Права  директории** | **Права  файла** | **Создание  файла** | **Удаление  файла** | **Запись  в файл** | **Чтение  файла** | **Смена  директории** | **Просмотр файлов  в директории** | **Переименование  файла** | **Смена  атрибутов файла** |
|:---------------------:|:----------------:|:-------------------:|:-------------------:|:------------------:|:-----------------:|:---------------------:|:---------------------------------:|:-------------------------:|:--------------------------:|
| d(000)                |       (000)      |          -          |          -          |          -         |         -         |           -           |                 -                 |             -             |              -             |
| d--x------            |       (100)      |          -          |          -          |          -         |         -         |           +           |                 -                 |             -             |              +             |
| d-w-------            |       (200)      |          +          |          +          |          +         |         -         |           -           |                 -                 |             +             |              -             |
| d-wx------            |       (300)      |          +          |          +          |          +         |         -         |           +           |                 -                 |             +             |              +             |
| dr--------            |       (400)      |          -          |          -          |          -         |         +         |           -           |                 +                 |             -             |              -             |
| dr-x------            |       (500)      |          -          |          -          |          -         |         +         |           +           |                 +                 |             -             |              +             |
| drw-------            |       (600)      |          +          |          +          |          +         |         +         |           -           |                 +                 |             +             |              -             |
| drwx------            |       (700)      |          +          |          +          |          +         |         +         |           +           |                 +                 |             +             |              +             |

15) На основании заполненной таблицы определила минимально необходимые права для выполнения операций внутри директории dir1, заполните табл. 2.2 (см. табл. 2.2 в указаниях к лабораторной):

|      **Операция**      | **Минимальные права на директорию** | **Минимальные права на файл** |
|:----------------------:|:-----------------------------------:|:-----------------------------:|
| Создание файла         |              d-w-------             |             (200)             |
| Удаление файла         |              d-w-------             |             (200)             |
| Чтение файла           |              dr--------             |             (400)             |
| Запись в файл          |              d-w-------             |             (200)             |
| Переименование файла   |              d-w-------             |             (200)             |
| Создание поддиректории |              d--x------             |             (100)             |
| Удаление поддиректории |              d--x------             |             (100)             |

16) Сохранила отчёт в 3 форматах: docx, pdf, md.

17) Обновила данные на GitHub.


# Вывод

Получены пракические навыки работы в консоли с атрибутами файлов, закреплены теоретические основы дискреционного разграничения доступа в современных системах на базе ОС Linux.

# Библиография

1. Методические материалы курса
