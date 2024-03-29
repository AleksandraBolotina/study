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
### Установка имени и электронной почты
Выполните следующие команды, чтобы git узнал ваше имя и
электронную почту.  

```
git config --global user.name "Your Name"
git config --global user.email "your_email@whatever.com"
```
![изображение](https://user-images.githubusercontent.com/113191444/213754674-b45897f6-4185-4c01-9ba2-9b10344a2f19.png)

### Параметры установки окончаний строк
![изображение](https://user-images.githubusercontent.com/113191444/213754735-c20af54d-351f-46dc-a73e-8136a86e9f3b.png)

### Установка отображения unicode
![изображение](https://user-images.githubusercontent.com/113191444/213755190-8e32854f-275c-4322-8af9-1fb8842f9e9b.png)

## Создание проекта.  
### Создайте страницу «Hello, World»

![изображение](https://user-images.githubusercontent.com/113191444/213755370-169e2f24-bc41-429e-9930-e4290a7a684d.png)

### Создание репозитория

![изображение](https://user-images.githubusercontent.com/113191444/213755793-f12ce202-dd62-41a6-85cb-05dcd0940cc8.png)

### Добавление файла в репозиторий

![изображение](https://user-images.githubusercontent.com/113191444/213755980-e11694cf-09d7-4916-b314-e5fcf2046771.png)

### Проверка состояние репозитория
![изображение](https://user-images.githubusercontent.com/113191444/213756017-ca2dd624-490b-48a2-8077-91cde7096f7c.png)

### Измените страницу «Hello, World»
![изображение](https://user-images.githubusercontent.com/113191444/213756185-91890984-d5b3-4e73-8a5d-043b7ac3010c.png)

### Индексация изменений

![изображение](https://user-images.githubusercontent.com/113191444/213756506-d898f8ee-ddf1-4bae-9a87-e6be0a9e816d.png)

### Коммит изменений

![изображение](https://user-images.githubusercontent.com/113191444/213756652-28272b5f-be2c-400b-a933-8e8e958ed086.png)

Добавьте стандартные теги страницы
![изображение](https://user-images.githubusercontent.com/113191444/213756926-6ba5b002-e337-4f73-9c14-38e549239e5c.png)

![изображение](https://user-images.githubusercontent.com/113191444/213757184-c0ff922e-c707-42d5-82ed-8e6fd87d7e82.png)

### История
Получим список произведенных изменений:
![изображение](https://user-images.githubusercontent.com/113191444/213757541-3c9768be-2ae7-490b-bfae-03c11eadf575.png)

### Получение старых версий
![изображение](https://user-images.githubusercontent.com/113191444/213757918-25f9d65c-e3ab-4870-96f8-bf9884479f94.png)

### Создание тегов версий
![изображение](https://user-images.githubusercontent.com/113191444/213758380-f9c9f4e4-7db8-44c5-bf26-9dd65f548671.png)

### Переключение по имени тега
![изображение](https://user-images.githubusercontent.com/113191444/213758887-29b6c766-875f-4841-8ebf-a4415ecf236e.png)

###  Просмотр тегов с помощью команды tag
![изображение](https://user-images.githubusercontent.com/113191444/213759081-368dd81f-de99-458a-9d51-03be5d45444e.png)

## Отмена локальных изменений (до индексации)
### Переключитесь на ветку master
Убедитесь, что вы находитесь на последнем коммите ветки master, прежде чем
продолжить работу.

![изображение](https://user-images.githubusercontent.com/113191444/213759357-21a96c6a-08dc-430a-bab4-63fff8712c12.png)

### Измените hello.html
Иногда случается, что вы изменили файл в рабочем каталоге, и хотите отменить
последние коммиты. С этим справится команда git checkout.
Внесите изменение в файл hello.html в виде нежелательного комментария.
![изображение](https://user-images.githubusercontent.com/113191444/213759895-20bdedbe-801b-4f8f-b8fa-3f427b25ece5.png)

### Проверьте состояние
Сначала проверьте состояние рабочего каталога.
![изображение](https://user-images.githubusercontent.com/113191444/213760020-a5cf5ff1-966c-4513-86c6-4dc9c548ec29.png)


### Отмена изменений в рабочем каталоге
Используйте команду git checkout для переключения версии файла
hello.html в репозитории.
![изображение](https://user-images.githubusercontent.com/113191444/213760213-ee380817-0082-4053-ac60-6e23fe44b563.png)

##  Отмена проиндексированных изменений (перед коммитом)
### Измените файл и проиндексируйте изменения
Внесите изменение в файл hello.html в виде нежелательного комментария

### Проверьте состояние
Проверьте состояние нежелательного изменения. Состояние показывает, что изменение было проиндексировано и готово к коммиту.

###  Выполните сброс буферной зоны
Команда git reset сбрасывает буферную зону к HEAD. Это очищает буферную
зону от изменений, которые мы только что проиндексировали.
Команда git reset (по умолчанию) не изменяет рабочий каталог. Поэтому
рабочий каталог все еще содержит нежелательный комментарий. Мы можем использовать команду git checkout, чтобы удалить нежелательные изменения в
рабочем каталоге.

### Переключитесь на версию коммита
Наш рабочий каталог опять чист

![изображение](https://user-images.githubusercontent.com/113191444/213760839-164eb71c-bb20-4e1f-b00c-fec08a6d5119.png)

##  Отмена коммитов
### Измените файл и сделайте коммит
Измените файл hello.html
Выполните:
```
git add hello.html
git commit -m "Oops, we didn't want this commit" 
```
### Сделайте коммит с новыми изменениями, отменяющими предыдущие
Чтобы отменить коммит, нам необходимо сделать коммит, который удаляет изменения, сохраненные нежелательным коммитом.

### Проверьте лог
Проверка лога показывает нежелательные и отмененные коммиты в наш репозиторий.

![изображение](https://user-images.githubusercontent.com/113191444/213761595-e01f8d5e-2a58-4e58-a263-2b1f7f420ee7.png)
![изображение](https://user-images.githubusercontent.com/113191444/213761693-68ac8578-3092-478d-a667-e8228cd8047d.png)

## Удаление коммиттов из ветки
### Проверьте нашу историю
сделаем быструю проверку нашей истории коммитов
### Для начала отметьте эту ветку
Но прежде чем удалить коммиты, давайте отметим последний коммит тегом, чтобы
потом можно было его найти.
### Сброс коммитов к предшествующим коммиту Oops
Глядя на историю лога, мы видим, что коммит с тегом «v1» является коммитом,
предшествующим ошибочному коммиту. Давайте сбросим ветку до этой точки.
Поскольку ветка имеет тег, мы можем использовать имя тега в команде сброса
(если она не имеет тега, мы можем использовать хэш-значение).

![изображение](https://user-images.githubusercontent.com/113191444/213762448-5f775603-d341-4b47-883e-3c90df2a4c72.png)

### Ничего никогда не теряется
Мы видим, что ошибочные коммиты не исчезли. Они все еще находятся в репозитории

![изображение](https://user-images.githubusercontent.com/113191444/213762512-22381766-f09f-4680-a682-753988a96073.png)

## Удаление тега oops
### Удаление тега oops
Тег oops свою функцию выполнил. Давайте удалим его и коммиты, на которые он
ссылался, сборщиком мусора. Тег «oops» больше не будет отображаться в репозитории.
![изображение](https://user-images.githubusercontent.com/113191444/213762654-472b47cb-a30b-4c8c-8f21-f41749fe994a.png)

## Внесение изменений в коммиты
###  Измените страницу, а затем сделайте коммит
Добавьте в страницу комментарий автора
### Необходим email
Обновите страницу hello, включив в
нее email.
### Измените предыдущий коммит
Мы действительно не хотим создавать отдельный коммит только ради электронной
почты. Давайте изменим предыдущий коммит, включив в него адрес электронной
почты.
###  Просмотр истории
Мы можем увидеть, что оригинальный коммит «автор» заменен коммитом «автор/email»

![изображение](https://user-images.githubusercontent.com/113191444/213763028-11aefebb-04e2-4bd1-bc4d-1b1766556525.png)

### Перемещение файлов
Сейчас мы собираемся создать структуру нашего репозитория. Давайте перенесем
страницу в каталог lib.
![изображение](https://user-images.githubusercontent.com/113191444/213763185-9c751391-424f-4107-81e1-7c99c7c26fc6.png)


### Коммит в новый каталог
Давайте сделаем коммит этого перемещения:
![изображение](https://user-images.githubusercontent.com/113191444/213763758-b5ebbb01-a49e-4563-a235-5b13591a8651.png)

## Подробнее о структуре
###  Добавление index.html
![изображение](https://user-images.githubusercontent.com/113191444/213763934-d8bf66e1-ecf7-48da-a200-5e6585ae9223.png)

##  Git внутри: Каталог .git
### Каталог .git
Это каталог, в котором хранится вся информация git.
### База данных объектов
Имена каталогов являются первыми двумя буквами хэша sha1 объекта, хранящегося в
git.
### Углубляемся в базу данных объектов
Смотрим в один из каталогов с именем из 2 букв. Вы увидите файлы с именами
из 38 символов. Это файлы, содержащие объекты, хранящиеся в git. Они сжаты и
закодированы, поэтому просмотр их содержимого нам мало чем поможет.
###  Config File
Это файл конфигурации, создающийся для каждого конкретного проекта. Записи
в этом файле будут перезаписывать записи в файле .gitconfig вашего главного
каталога, по крайней мере в рамках этого проекта.
### Ветки и теги
Вы должны узнавать файлы в подкаталоге тегов. Каждый файл соответствует
тегу, ранее созданному с помощью команды git tag. Его содержание — это всего
лишь хэш коммита, привязанный к тегу.
Каталог heads практически аналогичен, но используется для веток, а не тегов.
На данный момент у нас есть только одна ветка, так что все, что вы увидите в этом
каталоге – это ветка master.
### Файл HEAD
Файл HEAD содержит ссылку на текущую ветку, в данный момент это должна
быть ветка master.
![изображение](https://user-images.githubusercontent.com/113191444/213764423-a01d4686-0100-4d70-9c6f-e455f75ee641.png)

## Работа непосредственно с объектами git
### Поиск последнего коммита
![изображение](https://user-images.githubusercontent.com/113191444/213764654-47f361eb-1658-483a-95c5-96a54cd869e3.png)

### Вывод последнего коммита с помощью SHA1 хэша
![изображение](https://user-images.githubusercontent.com/113191444/213764789-ed1f6dbe-28ca-42c3-bfe2-4336ba3f2ca1.png)

### Поиск дерева
Мы можем вывести дерево каталогов, ссылка на который идет в коммите. Это должно быть описание файлов (верхнего уровня) в нашем проекте (для конкретного
коммита)
### Вывод каталога lib
Выполните:
`git cat-file -p <libhash>`

### Вывод файла hello.html
Выполните:
`git cat-file -p <hellohash>`
![изображение](https://user-images.githubusercontent.com/113191444/213765309-d6e8d061-eaee-45ea-ada9-9f01076ae6df.png)

## Создание ветки
###  Создайте ветку
Назовем нашу новую ветку «style».
###  Добавьте файл стилей style.css
Выполните:
```
touch lib/style.css
Файл lib/style.css:
h1 {
color: red;
}
```
Выполните:
```
git add lib/style.css
git commit -m "Added css stylesheet"
```
### Измените основную страницу
Измените основную страницу
###  Измените index.html
Обновите файл index.html, чтобы он тоже использовал style.css
![изображение](https://user-images.githubusercontent.com/113191444/213765933-4a381678-a7e9-46ff-9f16-f0bae51cb741.png)

## Навигация по веткам
Теперь в проекте есть две ветки
![изображение](https://user-images.githubusercontent.com/113191444/213766240-44b4ec76-3140-406c-891f-402ab9c81367.png)

## Переключение на ветку master
Используйте команду git checkout для переключения между ветками
## Вернемся к ветке style
Содержимое lib/hello.html подтверждает, что мы вернулись на ветку style
![изображение](https://user-images.githubusercontent.com/113191444/213766376-0b543bb1-2f99-4ab3-9d89-02732692307f.png)

### Изменения в ветке master
## Создайте файл README в ветке master
Выполните:
git checkout master
Создайте файл README.md
echo "This is the Hello World example from the git tutorial." > README.md
![изображение](https://user-images.githubusercontent.com/113191444/213766584-d6c8fcaf-06af-428a-9c20-76d8832c71c8.png)

## Сделайте коммит изменений README.md в ветку master

Выполните:
```
git add README.md
git commit -m "Added README"
```
##  Просмотрите текущие ветки
Добавление опции --graph в git log вызывает построение дерева коммитов
с помощью простых ASCII символов. Мы видим обе ветки (style и master), и то,
что ветка master является текущей HEAD. Общим предшественником обеих веток
является коммит «Added index.html».
Опция --all гарантированно означает, что мы видим все ветки. По умолчанию
показывается только текущая ветка.
![изображение](https://user-images.githubusercontent.com/113191444/213766843-268c4955-1012-414d-8a4b-3dc8c79f358d.png)

## Слияние
Слияние переносит изменения из двух веток в одну. Давайте вернемся к ветке
style и сольем master с style.
![изображение](https://user-images.githubusercontent.com/113191444/213778916-4741e42d-0db4-46b2-9be7-8db13e366f36.png)

## Создание конфликта
###  Вернитесь в master и создайте конфликт
![изображение](https://user-images.githubusercontent.com/113191444/213779134-d2761d88-45e9-4d0f-93f9-6865cf499236.png)

###  Просмотр веток
![изображение](https://user-images.githubusercontent.com/113191444/213779253-9e665c80-c00a-4a64-b602-5c96cd66c7c3.png)

## Разрешение конфликтов
### Слияние master с веткой style
![изображение](https://user-images.githubusercontent.com/113191444/213779443-8f783a3b-6e13-4e50-bc9c-909ef65bcf14.png)

## Решение конфликта
необходимо вручную разрешить конфликт

## Сделайте коммит решения конфликта

Выполните:
```
git add lib/hello.html
git commit -m "Merged master fixed conflict."
```
![изображение](https://user-images.githubusercontent.com/113191444/213779631-9647ca99-0e53-4874-951a-51df759a798a.png)

## Сброс ветки style
### Сброс ветки style
Вернемся на ветке style к точке перед тем, как мы слили ее с веткой master. Мы
можем сбросить ветку к любому коммиту. По сути, это изменение указателя ветки
на любую точку дерева коммитов.
В этом случае мы хотим вернуться в ветке style в точку перед слиянием с master.
Нам необходимо найти последний коммит перед слиянием.
![изображение](https://user-images.githubusercontent.com/113191444/213779826-f2120188-3015-4a40-b47f-7f4ec6733150.png)

### Проверьте ветку
Поищите лог ветки style. У нас в истории больше нет коммитов слияний.
Выполните:
![изображение](https://user-images.githubusercontent.com/113191444/213779898-e50662a5-5441-4f56-8020-55007178a5b4.png)

##  Сброс ветки master
![изображение](https://user-images.githubusercontent.com/113191444/213779976-45f64044-5c00-495a-be5e-6ee03badd653.png)
![изображение](https://user-images.githubusercontent.com/113191444/213780033-15c4b0ac-85df-4e8a-9566-5a0e6f8a5046.png)

## Перебазирование
![изображение](https://user-images.githubusercontent.com/113191444/213780147-dc6f90fa-cc71-4921-8f21-e9af12c71c6f.png)

##  Слияние в ветку master
### Слияние style в master
Поскольку последний коммит ветки master прямо предшествует последнему
коммиту ветки style, git может выполнить ускоренное слияние-перемотку. При
быстрой перемотке вперед git просто передвигает указатель вперед, таким образом указывая на тот же коммит, что и ветка style.
При быстрой перемотке конфликтов быть не может.
### Просмотрите логи
![изображение](https://user-images.githubusercontent.com/113191444/213780414-c127fae7-cc52-445b-8877-b994a0f1da48.png)

## Клонирование репозиториев
### Перейдите в рабочий каталог
![изображение](https://user-images.githubusercontent.com/113191444/213780628-163a9164-3cf9-4655-b105-b1e0e7f50aff.png)

###  Создайте клон репозитория hello
![изображение](https://user-images.githubusercontent.com/113191444/213780697-ef4d255b-5940-45bf-8256-41c7dc2cb22a.png)

## Просмотр клонированного репозитория
### Давайте взглянем на клонированный репозиторий.
Cписок всех файлов на верхнем уровне оригинального репозитория
README.md, index.html и lib.
### Просмотрите историю репозитория
![изображение](https://user-images.githubusercontent.com/113191444/213781040-0c500711-eab3-4bee-8692-186b0c1ee9d8.png)

##  Что такое origin?
![изображение](https://user-images.githubusercontent.com/113191444/213781145-c53c7558-d6d4-450c-8390-efb4c017a553.png)

## Удаленные ветки
Как мы видим, в списке только ветка master.

###  Список удаленных веток
Git выводит все коммиты в оригинальный репозиторий, но ветки в удаленном
репозитории не рассматриваются как локальные
![изображение](https://user-images.githubusercontent.com/113191444/213781283-72e65139-06e6-4ed0-8030-a8f4f05ad75a.png)

## Изменение оригинального репозитория
### Внесите изменения в оригинальный репозиторий hello
Теперь в оригинальном репозитории есть более поздние изменения, которых
нет в клонированной версии.
### Извлечение изменений
Сейчас мы находимся в репозитории cloned_hello.
На данный момент в репозитории есть все коммиты из оригинального репозитория, но они не интегрированы в локальные ветки клонированного репозитория.
В истории выше найдите коммит «Changed README in original repo». Обратите
внимание, что коммит включает в себя коммиты «origin/master» и «origin/HEAD».
Теперь давайте посмотрим на коммит «Updated index.html». Вы увидите, что
локальная ветка master указывает на этот коммит, а не на новый коммит, который
мы только что извлекли.
Выводом является то, что команда git fetch будет извлекать новые коммиты из удаленного репозитория, но не будет сливать их с вашими наработками в
локальных ветках.
![изображение](https://user-images.githubusercontent.com/113191444/213782261-de04c8c7-739a-4a33-8bc9-cccca560d024.png)

### Проверьте README.md
Мы можем продемонстрировать, что клонированный файл README.md не изменился.
![изображение](https://user-images.githubusercontent.com/113191444/213782333-2d96cf4b-4c84-47a6-a68c-230e78dc3a7d.png)

## Слияние извлеченных изменений
### Слейте извлеченные изменения в локальную ветку master
Выполните:
```
git merge origin/master
```
##  Еще раз проверьте файл README.md
![изображение](https://user-images.githubusercontent.com/113191444/213782622-e25a1432-fc5c-4ab9-8b6c-7e07096e3b7f.png)

## Добавление ветки наблюдения

![изображение](https://user-images.githubusercontent.com/113191444/213782786-7271d374-9e8a-4d3c-951d-fe448c57b1bb.png)

## Создайте чистый репозиторий
Как правило, репозитории, оканчивающиеся на .git являются чистыми репозиториями. Мы видим, что в репозитории hello.git нет рабочего каталога. По сути,
это есть не что иное, как каталог .git нечистого репозитория.
![изображение](https://user-images.githubusercontent.com/113191444/213782922-a459ff80-3b93-42c6-afe9-9f92e61c463b.png)

##  Добавление удаленного репозитория
![изображение](https://user-images.githubusercontent.com/113191444/213783149-152e7c65-ccac-4b62-b447-f05bb7552065.png)


## Отправка изменений
![изображение](https://user-images.githubusercontent.com/113191444/213783849-ae7b37fc-30e6-45fb-8216-46345eb14061.png)

## Извлечение общих изменений
![изображение](https://user-images.githubusercontent.com/113191444/213784027-94eb148d-010c-47a5-8151-2a61ddc1b87e.png)

# Выводы

Я научилась работать с git.

# Список литературы{.unnumbered}

::: {#refs}
:::
