---
## Front matter
lang: ru-RU
title: Ind Project Stage №5
author: |
	Anna D. Zaytseva\inst{1,3}
institute: |
	\inst{1}RUDN University, Moscow, Russian Federation
date: NEC--2024, 12 October, Moscow

## Formatting
toc: false
slide_level: 2
theme: metropolis
header-includes: 
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
 - '\makeatletter'
 - '\beamer@ignorenonframefalse'
 - '\makeatother'
aspectratio: 43
section-titles: true
---

# Цель работы

Цель работы --- приобретение пракктических навыков по использованию инструмента Burp Suite.

# Выполнение этапа индивидуального проекта

## Steps 1-7

Подготовка к использованию Burp Suite:

![Запуск сервисов](images/1.png){ #fig:001 width=70% }

![Запуск Burp Suite](images/2.png){ #fig:002 width=70% }

![Открытие настроек браузера](images/3.png){ #fig:003 width=70% }

![Изменение Connection settings](images/4.png){ #fig:004 width=70% }

![Изменение настроек proxy в Burp Suite](images/5.png){ #fig:005 width=70% }

![Intercept is on](images/6.png){ #fig:006 width=70% }

![network_allow_hijacking_localhost = true](images/7.png){ #fig:007 width=70% }

## Steps 8-11

Работа с Burp Suite - захват запроса:

![Forward для загрузки страницы DVWA](images/8.png){ #fig:008 width=70% }

![Страница авторизации](images/9.png){ #fig:009 width=70% }

![Вкладка Target](images/10.png){ #fig:010 width=70% }

![Неверный логин](images/11.png){ #fig:011 width=70% }

## Steps 12-17

Подготовка к атаке и сама атака (подбор логина и пароля для входа в DVWA):

![Send to Intruder](images/12.png){ #fig:012 width=70% }

![Intruder](images/13.png){ #fig:013 width=70% }

![Смена типа атаки и проставление специальных символов](images/14.png){ #fig:014 width=70% }

![Первый список подбора](images/15.png){ #fig:015 width=70% }

![Второй список подбора](images/16.png){ #fig:016 width=70% }

![Атака запущена](images/17.png){ #fig:017 width=70% }

## Steps 18-23

Анализ полученных результатов атаки:

![Смотрю ответ на пару admin-admin](images/18.png){ #fig:018 width=70% }

![Смотрю ответ на пару admin-password](images/19.png){ #fig:019 width=70% }

![Дополнительная проверка с Repeater](images/20.png){ #fig:020 width=70% }

![Результат запроса](images/21.png){ #fig:021 width=70% }

![Follow redirection result](images/22.png){ #fig:022 width=70% }

![Follow redirection visual result](images/23.png){ #fig:023 width=70% }

# Вывод

Приобрела практический навык по использованию инструмента Burp Suite.

# Библиография

* https://www.kaznu.kz/content/files/news/folder23191/%D0%9B%D0%B5%D0%BA%D1%86%D0%B8%D1%8F%2012%20rus.pdf
* https://esystem.rudn.ru/mod/page/view.php?id=1140635

## {.standout}

Спасибо за внимание!
