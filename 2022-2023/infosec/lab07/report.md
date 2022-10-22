
---
## Front matter
title: "Лабораторная работа №7"
subtitle: "Лабораторная работа № 7. Элементы криптографии. Однократное гаммирование"
author: "Болотина Александра Сергеевна"

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
lot: false # List of tables
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

Освоить на практике применение режима однократного гаммирования


# Выполнение лабораторной работы

Программа шифрует и дешифрует сообщения

Нужно подобрать ключ, чтобы получить сообщение «С Новым Годом, друзья!». Требуется разработать приложение, позволяющее шифровать и
дешифровать данные в режиме однократного гаммирования. Приложение должно:
1. Определить вид шифротекста при известном ключе и известном открытом тексте.
2. Определить ключ, с помощью которого шифротекст может быть преобразован в некоторый фрагмент текста, представляющий собой один из
возможных вариантов прочтения открытого текста.

Ключ:   
![изображение](https://user-images.githubusercontent.com/113191444/197333159-e765a64d-370c-47ee-b628-5af6a15c53ec.png)  
Текст сообщения, которое нужно зашифровать:  
![изображение](https://user-images.githubusercontent.com/113191444/197333167-c90022f0-e144-41a3-be97-69ebcc4c0183.png)  
Зашифрованное сообщение:  
![изображение](https://user-images.githubusercontent.com/113191444/197333172-a62c58c5-aa35-4fc6-ad59-6064a2f42a81.png)  
  
Ключ:   
![изображение](https://user-images.githubusercontent.com/113191444/197333159-e765a64d-370c-47ee-b628-5af6a15c53ec.png)  
Текст зашифрованного сообщения:
![изображение](https://user-images.githubusercontent.com/113191444/197333172-a62c58c5-aa35-4fc6-ad59-6064a2f42a81.png)  
Расшифрованное сообщение:  
![изображение](https://user-images.githubusercontent.com/113191444/197333167-c90022f0-e144-41a3-be97-69ebcc4c0183.png)  

# Выводы

Я освоила на практике применение режима однократного гаммирования.

# Список литературы

1. [Лабораторная работа № 7](https://esystem.rudn.ru/pluginfile.php/1652029/mod_resource/content/2/007-lab_crypto-gamma.pdf)

::: {#refs}
:::

