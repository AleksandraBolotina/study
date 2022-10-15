
---
## Front matter
title: "Лабораторная работа №6"
subtitle: "Лабораторная работа № 6. Мандатное разграничение прав в Linux"
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

Изучение механизмов изменения идентификаторов, применения SetUID- и Sticky-битов. Получение практических навыков работы в консоли с дополнительными атрибутами. Рассмотрение работы механизма
смены идентификатора процессов пользователей, а также влияние бита Sticky на запись и удаление файлов.

# Выполнение лабораторной работы

1. Войдите в систему с полученными учётными данными и убедитесь, что
SELinux работает в режиме enforcing политики targeted с помощью команд getenforce и sestatus.
![изображение](https://user-images.githubusercontent.com/113191444/196002071-74576ee2-cdd9-402e-9a71-94495bab6f7e.png)

2. Обратитесь с помощью браузера к веб-серверу, запущенному на вашем
компьютере, и убедитесь, что последний работает:
service httpd status
или
/etc/rc.d/init.d/httpd status
Если не работает, запустите его так же, но с параметром start.
![изображение](https://user-images.githubusercontent.com/113191444/196002112-00aaaa54-c73b-4a2d-a688-10b345039c90.png)

3. Найдите веб-сервер Apache в списке процессов, определите его контекст
безопасности и занесите эту информацию в отчёт. Например, можно использовать команду
ps auxZ | grep httpd
или
ps -eZ | grep httpd
![изображение](https://user-images.githubusercontent.com/113191444/196002151-cac92474-4947-4657-b153-75e90347986e.png)

4. Посмотрите текущее состояние переключателей SELinux для Apache с
помощью команды
sestatus -bigrep httpd
Обратите внимание, что многие из них находятся в положении «off».
5. Посмотрите статистику по политике с помощью команды seinfo, также
определите множество пользователей, ролей, типов.
![изображение](https://user-images.githubusercontent.com/113191444/196002243-4406da9b-6626-4415-9010-a8250514da98.png)

6. Определите тип файлов и поддиректорий, находящихся в директории
/var/www, с помощью команды
ls -lZ /var/www
7. Определите тип файлов, находящихся в директории /var/www/html:
ls -lZ /var/www/html
![изображение](https://user-images.githubusercontent.com/113191444/196002281-75945b40-4c9f-4375-b65a-b120f76c0b62.png)

8. Определите круг пользователей, которым разрешено создание файлов в
директории /var/www/html.
9. Создайте от имени суперпользователя (так как в дистрибутиве после установки только ему разрешена запись в директорию) html-файл
/var/www/html/test.html следующего содержания:
<html>
<body>test</body>
</html>
![изображение](https://user-images.githubusercontent.com/113191444/196002387-a76752e2-bde9-475d-a250-340e9a42a41e.png)


10. Проверьте контекст созданного вами файла. Занесите в отчёт контекст,
присваиваемый по умолчанию вновь созданным файлам в директории
/var/www/html.

11. Обратитесь к файлу через веб-сервер, введя в браузере адрес
http://127.0.0.1/test.html. Убедитесь, что файл был успешно отображён.
- файл не отображён
![изображение](https://user-images.githubusercontent.com/113191444/196002402-29b4fc6c-13af-4abc-aeb6-2c0785dcbbde.png)

12. Изучите справку man httpd_selinux и выясните, какие контексты файлов определены для httpd. Сопоставьте их с типом файла
test.html. Проверить контекст файла можно командой ls -Z.
ls -Z /var/www/html/test.html
![изображение](https://user-images.githubusercontent.com/113191444/196002446-44980cb0-0e85-4068-b2c6-dab0dbe2ac83.png)
![изображение](https://user-images.githubusercontent.com/113191444/196002453-002dcf77-05c0-4799-b39f-4df8b5dd11fe.png)

13. Измените контекст файла /var/www/html/test.html с
httpd_sys_content_t на любой другой, к которому процесс httpd не
должен иметь доступа, например, на samba_share_t:
chcon -t samba_share_t /var/www/html/test.html
ls -Z /var/www/html/test.html
После этого проверьте, что контекст поменялся.
![изображение](https://user-images.githubusercontent.com/113191444/196002525-6d5ef98c-c99e-4f42-964a-42f30e5df897.png)

14. Попробуйте ещё раз получить доступ к файлу через веб-сервер, введя в
браузере адрес http://127.0.0.1/test.html. Вы должны получить
сообщение об ошибке:
Forbidden
You don't have permission to access /test.html on this server.
![изображение](https://user-images.githubusercontent.com/113191444/196002539-16432017-c3f1-4b55-867d-1884b557a255.png)

15. Проанализируйте ситуацию. 
ls -l /var/www/html/test.html
Просмотрите log-файлы веб-сервера Apache. Также просмотрите системный лог-файл:
tail /var/log/messages
![изображение](https://user-images.githubusercontent.com/113191444/196002567-08f9ec33-a871-4a79-ab6a-ae8f125442cc.png)

16. Попробуйте запустить веб-сервер Apache на прослушивание ТСР-порта 81 (а не 80, как рекомендует IANA и прописано в /etc/services). Для
этого в файле /etc/httpd/httpd.conf найдите строчку Listen 80 и замените её на Listen 81.
- файл пуст
![изображение](https://user-images.githubusercontent.com/113191444/196002619-c23daf6d-8a0e-4e03-9ad7-ba5f9f7e0c47.png)

17. Выполните перезапуск веб-сервера Apache. 
18. Проанализируйте лог-файлы:
tail -nl /var/log/messages
![изображение](https://user-images.githubusercontent.com/113191444/196002649-3fd814db-a88d-4db0-9c6a-4d0478331f0f.png)

Просмотрите файлы /var/log/http/error_log, /var/log/http/access_log и /var/log/audit/audit.log и выясните, в каких файлах появились записи.
![изображение](https://user-images.githubusercontent.com/113191444/196002666-687be149-3eba-444e-afae-eadc093ee899.png)

19. Выполните команду
semanage port -a -t http_port_t -р tcp 81
После этого проверьте список портов командой
semanage port -l | grep http_port_t
Убедитесь, что порт 81 появился в списке.
![изображение](https://user-images.githubusercontent.com/113191444/196002723-32a59604-d196-4356-ba77-f484c2582e40.png)

20. Попробуйте запустить веб-сервер Apache ещё раз. 
21. Верните контекст httpd_sys_cоntent__t к файлу /var/www/html/ test.html:
chcon -t httpd_sys_content_t /var/www/html/test.html
После этого попробуйте получить доступ к файлу через веб-сервер, введя в браузере адрес http://127.0.0.1:81/test.html.
Вы должны увидеть содержимое файла — слово «test».
![изображение](https://user-images.githubusercontent.com/113191444/196002747-6321a1ac-f8c6-4c11-85b0-b4b067ef212e.png)
![изображение](https://user-images.githubusercontent.com/113191444/196002774-a8c408db-68eb-4904-8d32-9ad9de256c2c.png)

22. Исправьте обратно конфигурационный файл apache, вернув Listen 80.
23. Удалите привязку http_port_t к 81 порту:
semanage port -d -t http_port_t -p tcp 81
и проверьте, что порт 81 удалён.
![изображение](https://user-images.githubusercontent.com/113191444/196002809-fa8af9e9-0c73-4cf9-8573-981c9f0fa0ae.png)

24. Удалите файл /var/www/html/test.html:
rm /var/www/html/test.html
![изображение](https://user-images.githubusercontent.com/113191444/196002825-754f8b17-94ba-4355-b448-f3066d607b57.png)



# Выводы

Я изучила механизмы изменения идентификаторов, применения SetUID- и Sticky-битов. Получила практических навыков работы в консоли с дополнительными атрибутами. Рассмотрела работы механизма
смены идентификатора процессов пользователей, а также влияние бита Sticky на запись и удаление файлов.

# Список литературы

1. [Лабораторная работа № 5]([https://esystem.rudn.ru/pluginfile.php/1652025/mod_resource/content/2/005-lab_discret_sticky.pdf](https://esystem.rudn.ru/pluginfile.php/1652027/mod_resource/content/2/006-lab_selinux.pdf))

::: {#refs}
:::

