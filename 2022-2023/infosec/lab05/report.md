
---
## Front matter
title: "Лабораторная работа №5"
subtitle: "Дискреционное разграничение прав в Linux. Исследование влияния дополнительных атрибутов"
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

Изучение механизмов изменения идентификаторов, применения
SetUID- и Sticky-битов. Получение практических навыков работы в консоли с дополнительными атрибутами. Рассмотрение работы механизма
смены идентификатора процессов пользователей, а также влияние бита
Sticky на запись и удаление файлов.

# Выполнение лабораторной работы

1. Войдите в систему от имени пользователя guest.
2. Создайте программу simpleid.c:
Получившуюся программу назовите simpleid2.c.
3. Скомплилируйте программу и убедитесь, что файл программы создан:
gcc simpleid.c -o simpleid
![изображение](https://user-images.githubusercontent.com/113191444/194703062-609eadfe-0d39-4a66-85aa-c7f24c893ae4.png)

4. Выполните программу simpleid:
./simpleid
5. Выполните системную программу id:
id
и сравните полученный вами результат с данными предыдущего пункта
задания.
![изображение](https://user-images.githubusercontent.com/113191444/194703076-f462ba18-113d-491d-b226-54457c4ceaaf.png)
Данные совпадают

6. Усложните программу, добавив вывод действительных идентификаторов
Получившуюся программу назовите simpleid2.c
8. Скомпилируйте и запустите simpleid2.c:
gcc simpleid2.c -o simpleid2
./simpleid2
![изображение](https://user-images.githubusercontent.com/113191444/194703105-bc9347e2-c076-498b-965a-a12b2cf9343a.png)

8. От имени суперпользователя выполните команды:
chown root:guest /home/guest/simpleid2
chmod u+s /home/guest/simpleid2
![изображение](https://user-images.githubusercontent.com/113191444/194703118-ff7cad62-e6e2-4420-86e8-6cc8ed38fac0.png)
![изображение](https://user-images.githubusercontent.com/113191444/194703127-bbc2de9a-29fc-4920-a35c-aae0383d03ce.png)

9. Используйте sudo или повысьте временно свои права с помощью su.
Поясните, что делают эти команды.
- Крманда sudo позволяет выполнять команды от имени админимтратора. <\br>
- Команда su позволяет выполнять команды от имени другого пользователя
10. Выполните проверку правильности установки новых атрибутов и смены
владельца файла simpleid2:
ls -l simpleid2
11. Запустите simpleid2 и id:
./simpleid2
id
Сравните результаты.
- данные совпадают 
12. Проделайте тоже самое относительно SetGID-бита.
13. Создайте программу readfile.c
14. Откомпилируйте её.
gcc readfile.c -o readfile
15. Смените владельца у файла readfile.c (или любого другого текстового
файла в системе) и измените права так, чтобы только суперпользователь
(root) мог прочитать его, a guest не мог.
16. Проверьте, что пользователь guest не может прочитать файл readfile.c.
17. Смените у программы readfile владельца и установите SetU’D-бит.
18. Проверьте, может ли программа readfile прочитать файл readfile.c?
19. Проверьте, может ли программа readfile прочитать файл /etc/shadow?
![изображение](https://user-images.githubusercontent.com/113191444/194703170-1a2013a6-2f43-4782-b1ac-93f34d508663.png)


 Исследование Sticky-бита
1. Выясните, установлен ли атрибут Sticky на директории /tmp, для чего
выполните команду
ls -l / | grep tmp
![изображение](https://user-images.githubusercontent.com/113191444/194703192-ea9f52e7-1441-4ef7-a591-b4ce40c57170.png)

2. От имени пользователя guest создайте файл file01.txt в директории /tmp
со словом test:
echo "test" > /tmp/file01.txt
3. Просмотрите атрибуты у только что созданного файла и разрешите чтение и запись для категории пользователей «все остальные»:
ls -l /tmp/file01.txt
chmod o+rw /tmp/file01.txt
ls -l /tmp/file01.txt
![изображение](https://user-images.githubusercontent.com/113191444/194703221-f513cbf0-107b-4bd4-b855-d6e14dd511d7.png)

4. От пользователя guest2 (не являющегося владельцем) попробуйте прочитать файл /tmp/file01.txt:
cat /tmp/file01.txt
5. От пользователя guest2 попробуйте дозаписать в файл
/tmp/file01.txt слово test2 командой
echo "test2" > /tmp/file01.txt
Удалось ли вам выполнить операцию?
- да, так как в предыдущем шаге были даны права для этого
6. Проверьте содержимое файла командой
cat /tmp/file01.txt
7. От пользователя guest2 попробуйте записать в файл /tmp/file01.txt
слово test3, стерев при этом всю имеющуюся в файле информацию командой
echo "test3" > /tmp/file01.txt
Удалось ли вам выполнить операцию?
- да, так как в предыдущем шаге были даны права для этого
8. Проверьте содержимое файла командой
cat /tmp/file01.txt
9. От пользователя guest2 попробуйте удалить файл /tmp/file01.txt командой
rm /tmp/fileOl.txt
Удалось ли вам удалить файл?

![изображение](https://user-images.githubusercontent.com/113191444/194703244-ffea15b4-7615-4db7-81d7-9dcb7ed8dc0b.png)

10. Повысьте свои права до суперпользователя следующей командой
su -
и выполните после этого команду, снимающую атрибут t (Sticky-бит) с
директории /tmp:
chmod -t /tmp
![изображение](https://user-images.githubusercontent.com/113191444/194703262-62cb9d46-6557-4b6b-a079-8a9f206c666e.png)

11. Покиньте режим суперпользователя командой
exit
12. От пользователя guest2 проверьте, что атрибута t у директории /tmp
нет:
ls -l / | grep tmp
![изображение](https://user-images.githubusercontent.com/113191444/194703269-949cf3e4-70c3-47e1-8325-c21580ac0f85.png)

15. Повысьте свои права до суперпользователя и верните атрибут t на директорию /tmp:
su -
chmod +t /tmp
exit
![изображение](https://user-images.githubusercontent.com/113191444/194703277-4c369cb2-6772-49e2-92c0-7a582caf1dd8.png)


# Выводы

Я изучила механизмы изменения идентификаторов, применения
SetUID- и Sticky-битов. Получила практические навыки работы в консоли с дополнительными атрибутами. Рассмотрела работу механизма
смены идентификатора процессов пользователей, а также влияние бита
Sticky на запись и удаление файлов.

# Список литературы

1. [Лабораторная работа № 5](https://esystem.rudn.ru/pluginfile.php/1652025/mod_resource/content/2/005-lab_discret_sticky.pdf)

::: {#refs}
:::

