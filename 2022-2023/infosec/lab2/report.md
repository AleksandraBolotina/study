---
## Front matter
title: "Лабораторная работа №2"
subtitle: "Дискреционное разграничение прав в Linux. Основные атрибуты"
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

Целью данной работы является получение практических навыков работы в консоли с атрибутами файлов, закрепление теоретических основ дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux.

# Выполнение лабораторной работы

1. В установленной при выполнении предыдущей лабораторной работы
операционной системе создайте учётную запись пользователя guest (использую учётную запись администратора): </br>
```useradd guest``` </br>
![изображение 1](https://user-images.githubusercontent.com/113191444/190870308-f840efa7-abb8-4309-af8c-4ce669747ca2.png)

2. Задайте пароль для пользователя guest (использую учётную запись администратора):
passwd guest </br>
![изображение 2](https://user-images.githubusercontent.com/113191444/190870382-8ea12247-55cb-4f70-94dd-e88e49dbdaac.png)

3. Войдите в систему от имени пользователя guest. (изображение 3)
4. Определите директорию, в которой вы находитесь, командой pwd. Сравните её с приглашением командной строки. Определите, является ли она
вашей домашней директорией? - Да </br> (изображение 3)
5. Уточните имя вашего пользователя командой whoami. (изображение 3)
6. Уточните имя вашего пользователя, его группу, а также группы, куда входит пользователь, командой id. Выведенные значения uid, gid и др. запомните. Сравните вывод id с выводом команды groups. - значения совпадают. (изображение 3)
7. Сравните полученную информацию об имени пользователя с данными,
выводимыми в приглашении командной строки. - значения совпадают. </br>
![изображение 3](https://user-images.githubusercontent.com/113191444/190870429-3447a542-f262-480f-98d6-f861077a784e.png)

8. Просмотрите файл /etc/passwd командой
cat /etc/passwd
Найдите в нём свою учётную запись. Определите uid пользователя. - 1009 </br>
Определите gid пользователя. - 100 </br>
Сравните найденные значения с полученными в предыдущих пунктах. - значения совпадают.  </br>
Замечание: в случае, когда вывод команды не умещается на одном
экране монитора, используйте прокрутку вверх–вниз (удерживая клавишу shift, нажимайте page up и page down) либо программу grep в качестве фильтра для вывода только строк, содержащих определённые
буквенные сочетания:
cat /etc/passwd | grep guest </br>
![изображение 4](https://user-images.githubusercontent.com/113191444/190870450-9d4dd62c-6b18-4059-bb05-58c6215032a8.png)

9. Определите существующие в системе директории командой
ls -l /home/
Удалось ли вам получить список поддиректорий директории /home? Какие права установлены на директориях? </br>
![изображение 5](https://user-images.githubusercontent.com/113191444/190870932-5f307bd5-a91f-4273-b8d5-fef97771c5cc.png)


10. Проверьте, какие расширенные атрибуты установлены на поддиректориях, находящихся в директории /home, командой:
lsattr /home
Удалось ли вам увидеть расширенные атрибуты директории? 
Удалось ли вам увидеть расширенные атрибуты директорий других
пользователей?


11. Создайте в домашней директории поддиректорию dir1 командой
mkdir dir1
Определите командами ls -l и lsattr, какие права доступа и расширенные атрибуты были выставлены на директорию dir1. </br>
![изображение 6](https://user-images.githubusercontent.com/113191444/190871015-ab2a155b-ca15-4372-ae26-db646f40d1d0.png)
![изображение 7](https://user-images.githubusercontent.com/113191444/190871035-1646039a-0fae-4942-bd4c-59cb915f4e05.png)
![изображение 8](https://user-images.githubusercontent.com/113191444/190871225-48da15b7-1a7d-4b82-952e-41a444c4d428.png)


12. Снимите с директории dir1 все атрибуты командой
chmod 000 dir1
и проверьте с её помощью правильность выполнения команды
ls -l </br>
![изображение 9](https://user-images.githubusercontent.com/113191444/190871261-de5be692-e627-42d2-a58e-36afca6d54e9.png)

13. Попытайтесь создать в директории dir1 файл file1 командой
echo "test" > /home/guest/dir1/file1
Объясните, почему вы получили отказ в выполнении операции по созданию файла?
Оцените, как сообщение об ошибке отразилось на создании файла? Проверьте командой
ls -l /home/guest/dir1
действительно ли файл file1 не находится внутри директории dir1. </br>
![изображение 10](https://user-images.githubusercontent.com/113191444/190871307-e7200483-1e47-40a3-9dae-15ae9fa01c1d.png)
![изображение 11](https://user-images.githubusercontent.com/113191444/190871332-b86112a0-c54e-4a73-a88c-b824021ad1b3.png)

14. Заполните таблицу «Установленные права и разрешённые действия»
(см. табл. 2.1), выполняя действия от имени владельца директории (файлов), определив опытным путём, какие операции разрешены, а какие нет.
Если операция разрешена, занесите в таблицу знак «+», если не разрешена, знак «-». </br>
![изображение 12](https://user-images.githubusercontent.com/113191444/190871486-325d13bf-912d-4b51-8c78-759b854d6080.png)

15. На основании заполненной таблицы определите те или иные минимально необходимые права для выполнения операций внутри директории
dir1, заполните табл. 2.2. </br>
![изображение 13](https://user-images.githubusercontent.com/113191444/190871678-be8e11ab-9887-4ac7-abef-f3d213cc7c22.png)



# Выводы

Я получила практические навыки работы в консоли с атрибутами файлов, закрепление теоретических основ дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux



# Список литературы{.unnumbered}

1. [Лабораторная работа № 2. Дискреционное разграничение прав в Linux.Основные атрибуты](https://esystem.rudn.ru/pluginfile.php/1652019/mod_resource/content/6/002-lab_discret_attr.pdf)

::: {#refs}
:::

