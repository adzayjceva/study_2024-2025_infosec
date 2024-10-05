---
## Front matter
lang: ru-RU
title: Ind Project Stage №4
author: |
	Anna D. Zaytseva\inst{1,3}
institute: |
	\inst{1}RUDN University, Moscow, Russian Federation
date: NEC--2024, 5 October, Moscow

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

Цель работы --- приобретение пракктических навыков по использованию инструмента nikto — базового сканера безопасности веб-сервера. Он сканирует и обнаруживает уязвимости в веб-приложениях, обычно вызванные неправильной конфигурацией на самом сервере, файлами, установленными по умолчанию, и небезопасными файлами, а также устаревшими серверными приложениями.

# Выполнение этапа индивидуального проекта

## Steps 1-2

Подготовка к использованию утилиты nikto:

![Запуск сервисов MySQL и Apache2](images/1.png){ #fig:001 width=70% }

![В приложении DVWA захожу в раздел ```DVWA Security``` и выбираю функцию "Low"](images/2.png){ #fig:002 width=70% }

## Steps 3-5

Работа с nikto:

![Воспользовалась утилитой nikto](images/3.png){ #fig:003 width=70% }

![DVWA "Impossible"](images/4.png){ #fig:004 width=70% }

![Повторный запуск nikto](images/5.png){ #fig:005 width=70% }

## Step 6

Настроила сервер apache2:

Ввела данные в соответствующее поле. Операция прошла успешно:

![Успешная авторизация](images/6.png){ #fig:006 width=70% }

# Вывод

Вывод утилиты не изменился. Далее привожу анализ вывода:

* Server: Apache/2.4.62 (Debian)

* /DVWA/: The anti-clickjacking X-Frame-Options header is not present. See: https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options

Отсутствие заголовка X-Frame-Options сигнализирует о том, что сайт может быть подвержен атаке clickjacking. Кликджекинг — это атака на основе интерфейса, при которой пользователя обманным путем заставляют щелкнуть активный контент на скрытом веб-сайте, щелкнув другой контент на ложном веб-сайте.

* /DVWA/: The X-Content-Type-Options header is not set. This could allow the user agent to render the content of the site in a different fashion to the MIME type. See: https://www.netsparker.com/web-vulnerability-scanner/vulnerabilities/missing-content-type-header/

Если заголовок X-Frame-Options не установлен, это может привести к тому, что старые версии Chrome и Internet Explorer будут выполнять MIME-анализ тела ответа. И это может закончиться тем, что тело ответа будет интерпретировано и отображено как тип контента, отличный от объявленного.

* Root page /DVWA redirects to: login.php

Иллюстрация имени скрипта авторизации.

* OPTIONS: Allowed HTTP Methods: HEAD, GET, POST, OPTIONS .

У эндпоинта есть несколько методов.

* /DVWA/config/: Directory indexing found.

Обнаружена индексация каталогов.

* /DVWA/config/: Configuration information may be available remotely.

Найден эндпоинт, по которому может содержаться информация по конфигурации.

* /DVWA/tests/: Directory indexing found.

Обнаружена индексация каталогов.

* /DVWA/tests/: This might be interesting.

Найдена папка с тестами: это может быть полезно.

* /DVWA/database/: Directory indexing found.

Обнаружена индексация каталогов.

* /DVWA/database/: Database directory found.

Обнаружена директория, содержащая информацию о базе данных.

* /DVWA/docs/: Directory indexing found.

Обнаружена индексация каталогов.

* /DVWA/login.php: Admin login page/section found.

Найден эндпоинт для входа в панель админа.

* /DVWA/.git/index: Git Index file may contain directory listing information.

* /DVWA/.git/HEAD: Git HEAD file found. Full repo details may be present.

* /DVWA/.git/config: Git config file found. Infos about repo details may be present.

* /DVWA/.gitignore: .gitignore file found. It is possible to grasp the directory structure.

Найдена информация о системе контроля версий.

* /DVWA/.dockerignore: .dockerignore file found. It may be possible to grasp the directory structure and learn more about the site.

Файл .dockerignore содержит список файлов и папок, которые могут быть исключены при сборке образов Docker для развертывания в контейнерах.

* 7850 requests: 0 error(s) and 16 item(s) reported on remote host

* End Time:           2024-10-05 14:45:39 (GMT-4) (29 seconds)

# Вывод

Приобрела практический навык по использованию инструмента nikto - базового сканера безопасности веб-сервера.

# Библиография

* https://github.com/digininja/DVWA?tab=readme-ov-file
* https://www.kali.org/
* https://www.kali.org/tools/nikto/
* https://habr.com/ru/companies/otus/articles/492546/

## {.standout}

Спасибо за внимание!
