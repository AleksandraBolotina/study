
---
## Front matter
title: "Лабораторная работа №4"
subtitle: "Дискреционное разграничение прав в Linux. Расширенные атрибуты"
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

Получение практических навыков работы в консоли с расширенными
атрибутами файлов

# Выполнение лабораторной работы

1. От имени пользователя guest определите расширенные атрибуты файла
/home/guest/dir1/file1 командой (рис. 1)
lsattr /home/guest/dir1/file1
2. Установите командой
chmod 600 file1
на файл file1 права, разрешающие чтение и запись для владельца файла. (рис. 1)
3. Попробуйте установить на файл /home/guest/dir1/file1 расширенный атрибут a от имени пользователя guest: (рис. 1)
chattr +a /home/guest/dir1/file1
В ответ вы должны получить отказ от выполнения операции.
![изображение](https://user-images.githubusercontent.com/113191444/193420778-0c3e7c65-7ef3-46ce-8554-6938f58bccb2.png)(рис. 1)

4. Зайдите на третью консоль с правами администратора либо повысьте
свои права с помощью команды su. Попробуйте установить расширенный атрибут a на файл /home/guest/dir1/file1 от имени суперпользователя: (рис. 2)
chattr +a /home/guest/dir1/file1
![изображение](https://user-images.githubusercontent.com/113191444/193420841-6f8f8fa8-a190-48a7-b9af-cb298d1fc64d.png)(рис. 2)

5. От пользователя guest проверьте правильность установления атрибута: (рис. 3)
lsattr /home/guest/dir1/file1
6. Выполните дозапись в файл file1 слова «test» командой  
echo "test" /home/guest/dir1/file1
После этого выполните чтение файла file1 командой
cat /home/guest/dir1/file1
Убедитесь, что слово test было успешно записано в file1. (рис. 3)
![изображение](https://user-images.githubusercontent.com/113191444/193420870-16cfc2e2-20a1-4d07-95d4-b563386ac1ca.png)(рис. 3)

7. Попробуйте удалить файл file1 либо стереть имеющуюся в нём информацию командой
echo "abcd" > /home/guest/dirl/file1
Попробуйте переименовать файл. (рис. 4)
8. Попробуйте с помощью команды chmod 000 file1
установить на файл file1 права, например, запрещающие чтение и запись для владельца файла. Удалось ли вам успешно выполнить указанные команды? 
- нет (рис. 4)
![изображение](https://user-images.githubusercontent.com/113191444/193420914-062d5f9e-7021-4d7f-885b-e0fa2642246b.png)(рис. 4)

9. Снимите расширенный атрибут a с файла /home/guest/dirl/file1 от
имени суперпользователя командой
chattr -a /home/guest/dir1/file1
Повторите операции, которые вам ранее не удавалось выполнить. Ваши
наблюдения занесите в отчёт.
- не удалось выполнить операции (рис. 5, 6)
![изображение](https://user-images.githubusercontent.com/113191444/193420961-007a503f-22ad-4835-a29f-0f34f07a11cd.png)(рис. 5)
![изображение](https://user-images.githubusercontent.com/113191444/193420987-79e8aa8b-96a7-4fb7-9769-724a5e552589.png)(рис. 6)


10. Повторите ваши действия по шагам, заменив атрибут «a» атрибутом «i».
Удалось ли вам дозаписать информацию в файл? 
- нет (рис. 7, 8)
- ![изображение](https://user-images.githubusercontent.com/113191444/193421037-7d676a94-d17e-4b7f-9162-af0238c453c1.png)(рис. 7)
- ![изображение](https://user-images.githubusercontent.com/113191444/193421019-e1ed5d6d-0c86-47e9-b95f-f8c3e672be41.png)(рис. 8)



# Выводы

В результате выполнения работы мы повысили свои навыки использования интерфейса командой строки (CLI), познакомились на примерах с тем,
как используются основные и расширенные атрибуты при разграничении
доступа. Имели возможность связать теорию дискреционного разделения
доступа (дискреционная политика безопасности) с её реализацией на практике в ОС Linux. Опробовали действие на практике расширенных атрибутов «а» и «i».

# Список литературы{.unnumbered}

1. [Лабораторная работа № 4]([https://esystem.rudn.ru/pluginfile.php/1652019/mod_resource/content/6/002-lab_discret_attr.pdf](https://esystem.rudn.ru/pluginfile.php/1652023/mod_resource/content/3/004-lab_discret_extattr.pdf))

::: {#refs}
:::

