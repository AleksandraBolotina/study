---
## Front matter
title: "Лабораторная 1"
subtitle: "Работа с git"
author: "Александра Болотина"

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
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
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

Научиться работать с git.  


# Выполнение лабораторной работы

Выполните следующие команды, чтобы git узнал ваше имя и
электронную почту.  

```
git config --global user.name "Your Name"
git config --global user.email "your_email@whatever.com"
```
![изображение](https://user-images.githubusercontent.com/113191444/213754674-b45897f6-4185-4c01-9ba2-9b10344a2f19.png)

Параметры установки окончаний строк
![изображение](https://user-images.githubusercontent.com/113191444/213754735-c20af54d-351f-46dc-a73e-8136a86e9f3b.png)

Установка отображения unicode
![изображение](https://user-images.githubusercontent.com/113191444/213755190-8e32854f-275c-4322-8af9-1fb8842f9e9b.png)

Создание проекта.  
Создайте страницу «Hello, World»

![изображение](https://user-images.githubusercontent.com/113191444/213755370-169e2f24-bc41-429e-9930-e4290a7a684d.png)

Создание репозитория

Добавление файла в репозиторий


Проверка состояние репозитория






# Выводы

Я научилась работать с git.

# Список литературы{.unnumbered}

::: {#refs}
:::
