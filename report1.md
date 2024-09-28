---
## Front matter
: "Отчёт по лабораторной работе 1"
author: "Лобов Михаил Сергеевич"


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
  options:
  - spelling=modern
  - babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: IBM Plex Serif
romanfont: IBM Plex Serif
sansfont: IBM Plex Sans
monofont: IBM Plex Mono
mathfont: STIX Two Math
mainfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
romanfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
sansfontoptions: Ligatures=Common,Ligatures=TeX,Scale=MatchLowercase,Scale=0.94
monofontoptions: Scale=MatchLowercase,Scale=0.94,FakeStretch=0.9
mathfontoptions:
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


Изучить использование системы контроля версий git. Ознакомиться с основными настройками и протестировать их. Скачать данные из репозитория и внести изменения с помощью возможностей git.


# Задание


1) Зарегистрироваться на Github.
2) Создать базовую конфигурацию для работы с git.
3) Создать ключ SSH.
4) Создать ключ PGP.
5) Настроить подписи git.
6) Создать локальный каталог для выполнения заданий по предмету.


# Теоретическое введение


## Базовая настройка git


git config --global user.name "Name Surname" - задает имя владельца репозитория


git config --global user.email "work@mail" - задает email владельца репозитория


git config --global core.quotepath false - настройка utf-8 в выводе сообщений git


git config --global init.defaultBranch master - задает имя начальной ветки


git config --global core.autocrlf input - настройка параметра autocrlf


git config --global core.safecrlf warn - настройка параметра safecrlf


## Команды для создания ключей ssh


ssh-keygen -t rsa -b 4096 - по алгоритму rsa с ключём размером 4096 бит


ssh-keygen -t ed25519 - – по алгоритму ed25519


## Команды для работы с ключами gpg


gpg --full-generate-key - генерация gpg ключа с настройками


gpg --list-secret-keys --keyid-format LONG - вывод списка ключей


gpg --armor --export <PGP Fingerprint> | xclip -sel clip - копирование ключа в буфер обмена


## Команды для настройки автоматических подписей коммитов git


git config --global user.signingkey <PGP Fingerprint>


git config --global commit.gpgsign true


git config --global gpg.program $(which gpg2)


## Для настройки каталога курса


cd - переход в нужную папку


make - создание новой папки/файла


rm - удаление ненужной папки/файла


***Отправка файлов на сервер:***


git add .


git commit -am 'feat(main): make course structure'


git push


# Выполнение лабораторной работы


## 1) Зарегистрироваться на Github.


Регистрирую аккаунт на платформе GitHub, чтобы загрузить репозиторий и работать с файлами через локальную копию на своем компьютере. Ссылка на профиль https://github.com/SuponinaAP/ScientificProg
![Профиль на GitHub](PhotoLab1/photo1.png){#fig:002 width=50%}


## 2) Создать базовую конфигурацию для работы с git.


### ***Установка программного обеспечения***


Устанавливаю программное обеспечение при помощи Chocolate, через команду в Windows PowerShell.


![Установка при помощи пакета chocolate](PhotoLab1/config1.png){#fig:001 width=50%}


![Установка при помощи пакета chocolate2](PhotoLab1/config2.png){#fig:002 width=50%}


### ***Базовая настройка git***


Указываю имя и адрес электронной почты, а также настраиваю языковые параметры.
![Настройка git](PhotoLab1/photo2.PNG){#fig:003 width=50%}


## 3) Создать ключ SSH.


Создаю ключи SSH.
- по алгоритму rsa


![Ключ SSH](PhotoLab1/photo3.PNG){#fig:003 width=50%}


- по алгоритму ed25519


![Ключ SSH 2](PhotoLab1/photo4.PNG){#fig:003 width=50%}


## 4) Создать ключ PGP.


Генерирую gpg ключ, со следующими параметрами:


– тип RSA and RSA;


– размер 4096;


– выберите срок действия; значение по умолчанию— 0 (срок действия не истекает
никогда).
![Ключ Gpg](PhotoLab1/photo5.PNG){#fig:003 width=50%}
![Ключ Gpg 2](PhotoLab1/photo6.PNG){#fig:003 width=50%}


Добавляю ключи на аккаунт в GitHub. Для этого открываю на гитхаб Настройки/Ключи ssh и gpg и там добавляю их.


При помощи команды получаю отпечаток приватного ключа.
![Добавление ключа](PhotoLab1/photo7.PNG){#fig:003 width=50%}


Для получения gpg ключа использую команду заменяя фразу в скобках на полученный отпечаток приватного ключа.
***gpg --armor --export <PGP Fingerprint>***
которая выводит на экран сам ключ.
![Привязанные ключи](PhotoLab1/photo8.png){#fig:003 width=50%}


## 5) Настроить подписи git.


Задаю требования для подписи коммитов.
![Настройка коммитов](PhotoLab1/photo9.PNG){#fig:003 width=50%}


## 6) Создать локальный каталог для выполнения заданий по предмету.


Создаю каталог, удаляю лишние файлы, а затем загружаю репозиторий на GitHub.


![Изменение репозитория](PhotoLab1/photo11.PNG){#fig:003 width=50%}


Проверяю изменения зайдя на GitHub
![Измененный репозиторий](PhotoLab1/photo10.png){#fig:003 width=50%}
# Выводы


В ходе работы я освоил использование системы контроля версий git. Изучил и применил базовые настройки. Загрузил данные из репозитория и внес изменения с помощью функций git.


# Список литературы{.unnumbered}


::: Пособие по лабораторной работе 1 {https://esystem.rudn.ru/pluginfile.php/2372898/mod_resource/content/5/002-lab_vcs.pdf}
::: Пособие по лабораторной работе 2 {https://esystem.rudn.ru/pluginfile.php/2372900/mod_resource/content/4/003-lab_markdown.pdf}



