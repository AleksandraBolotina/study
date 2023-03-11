---
## Front matter
title: "Отчет по лабораторной работе №5"
subtitle: "Дисциплина: Математическое моделирование"
author: "Выполнила: Болотина Александра Сергеевна"

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

Рассмотреть простейшую модель взаимодействия двух видов типа «хищник — жертва» -
модель Лотки-Вольтерры. Выполнить задание согласно варианту: построить график зависимости численности хищников от численности жертв, а также графики изменения численности хищников и численности жертв при заданных начальных условиях, найти стационарное сосотояние системы.

# Задание

**Вариант № 35**:

Задача: Для модели «хищник-жертва»:  
  $\frac{\partial x}{\partial t} = -0,29x(t)+0,031x(t)y(t)$  
  $\frac{\partial y}{\partial t} = 0,33y(t)-0,024x(t)y(t)$

Постройте график зависимости численности хищников от численности жертв,
а также графики изменения численности хищников и численности жертв при
следующих начальных условиях: $x_{0} = 7$, $y_{0} = 14$.
Найдите стационарное состояние системы.


# Теоретическое введение

Простейшая модель взаимодействия двух видов типа «хищник — жертва» -
модель Лотки-Вольтерры. Данная двувидовая модель основывается на
следующих предположениях:  
  1. Численность популяции жертв x и хищников y зависят только от времени
(модель не учитывает пространственное распределение популяции на
занимаемой территории)  
  2. В отсутствии взаимодействия численность видов изменяется по модели
Мальтуса, при этом число жертв увеличивается, а число хищников падает  
  3. Естественная смертность жертвы и естественная рождаемость хищника
считаются несущественными  
  4. Эффект насыщения численности обеих популяций не учитывается  
  5. Скорость роста численности жертв уменьшается пропорционально
численности хищников:
 
  $\frac{\partial x}{\partial t} = ax(t)-bx(t)y(t)$  
  $\frac{\partial y}{\partial t} = -cy(t)+dx(t)y(t)$

В этой модели x – число жертв, y - число хищников. Коэффициент a
описывает скорость естественного прироста числа жертв в отсутствие хищников, с
- естественное вымирание хищников, лишенных пищи в виде жертв. Вероятность
взаимодействия жертвы и хищника считается пропорциональной как количеству
жертв, так и числу самих хищников (xy). Каждый акт взаимодействия уменьшает
популяцию жертв, но способствует увеличению популяции хищников (члены -bxy
и dxy в правой части уравнения).  
  Стационарное состояние системы (1) (положение равновесия, не зависящее
от времени решение) будет в точке:
 
  $x_{0} = \frac{c}{d}$  
  $y_{0} = \frac{a}{b}$ 

# Выполнение лабораторной работы

Написала программу на Modelica:
```
model lab05
  parameter Real a=-0.29;
  parameter Real b=-0.031;
  parameter Real c=-0.33;
  parameter Real d=-0.024;
  parameter Real x0=7;
  parameter Real y0=14;
  Real x(start=x0);
  Real y(start=y0);
equation
  der(x)=a*x-b*x*y;
  der(y)=-c*y+d*x*y;
end lab05;
```
Получила следующиq график (см. рис. -@fig:001).

![Рис. 1. График](https://user-images.githubusercontent.com/113191444/224508023-704819a3-d98d-4993-9820-3dbb5a33e848.png)){ #fig:001 width=70% }


**3. Стационарное состояние**

Стационарная точка будет иметь коориднаты 
$x_{0} = \frac{c}{d} = \frac{-0,33}{-0,024} = 13,75$ и 
$y_{0} = \frac{a}{b} = \frac{-0,29}{-0,031} = 9,35$

# Выводы

Я рассмотрела простейшую модель взаимодействия двух видов типа «хищник — жертва» -
модель Лотки-Вольтерры. Выполнила задание согласно варианту: построила график зависимости численности хищников от численности жертв, а также графики изменения численности хищников и численности жертв при заданных начальных условиях, нашла стационарное сосотояние системы.

# Список литературы{.unnumbered}

::: {#refs}
:::
