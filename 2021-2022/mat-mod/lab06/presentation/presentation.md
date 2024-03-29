---
## Front matter
lang: ru-RU
title: Лабораторная работа №6
subtitle: Задача об эпидемии
author:
  - Болотина А. С.
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 17 марта 2023

## i18n babel
babel-lang: russian
babel-otherlangs: english

## Formatting pdf
toc: false
toc-title: Содержание
slide_level: 2
aspectratio: 169
section-titles: true
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
 - '\makeatletter'
 - '\beamer@ignorenonframefalse'
 - '\makeatother'
---

# Информация

## Докладчик

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

  * Болотина Александра Сергеевна
  * студент группы НПИбд-02-19
  * Российский университет дружбы народов
  * [1032192943@pfur.ru](mailto:1032192943@pfur.ru)
  * <https:https://github.com/AleksandraBolotina>

:::
::: {.column width="30%"}

:::
::::::::::::::

# Вводная часть

## Актуальность

- Необходим навык математического моделирования, которое является неизбежной составляющей научно-технического прогресса

## Объект и предмет исследования

- Задача об эпидемии

## Цели и задачи

Построить график для задачи об эпидемии.

# Выполнение работы

## Изучение теории

Предположим, что некая
популяция, состоящая из N особей, (считаем, что популяция изолирована)
подразделяется на три группы. Первая группа - это восприимчивые к болезни, но
пока здоровые особи, обозначим их через S(t). Вторая группа – это число
инфицированных особей, которые также при этом являются распространителями
инфекции, обозначим их I(t). А третья группа, обозначающаяся через R(t) – это
здоровые особи с иммунитетом к болезни.  
  До того, как число заболевших не превышает критического значения
I*, считаем, что все больные изолированы и не заражают здоровых. Когда I(t) > I*,
тогда инфицирование способны заражать восприимчивых к болезни особей.  
  Таким образом, скорость изменения числа S(t) меняется по следующему
закону: $\frac{dS}{dt} = -aS, если I(t) > I*$ и $\frac{dS}{dt} = 0, если I(t) <= I*$  
  Поскольку каждая восприимчивая к болезни особь, которая, в конце концов,
заболевает, сама становится инфекционной, то скорость изменения числа
инфекционных особей представляет разность за единицу времени между
заразившимися и теми, кто уже болеет и лечится, т.е.: 
$\frac{dI}{dt} = aS - bI, если I(t) > I*$ и $\frac{dS}{dt} = -bI, если I(t) <= I*$  
  А скорость изменения выздоравливающих особей (при этом приобретающие
иммунитет к болезни): $\frac{dR}{dt} = bI$ 
  Постоянные пропорциональности a, b - это коэффициенты заболеваемости
и выздоровления соответственно.  
  Для того, чтобы решения соответствующих уравнений определялось
однозначно, необходимо задать начальные условия. Считаем, что на начало
эпидемии в момент времени t = 0 нет особей с иммунитетом к болезни R(0)=0, а
число инфицированных и восприимчивых к болезни особей I(0) и S(0) соответственно.
Для анализа картины протекания эпидемии необходимо
рассмотреть два случая: I(0)<=I* и I(0)>I*.

## Написание кода 

```
mport math
import numpy as np
from scipy.integrate import odeint
import matplotlib.pyplot as plt

a = 0.01
b = 0.02

N = 12300
I0 = 140
R0 = 54
S0 = N - I0 - R0
x0 = [S0, I0, R0]

t0 = 0
tmax = 200
dt = 0.01
t = np.arange(t0, tmax, dt)

def S1(x, t):
    dx1_0 = 0
    dx1_1 = - b*x[1]
    dx1_2 = b*x[1]
    return dx1_0, dx1_1, dx1_2

def S2(x, t):
    dx2_0 = -a*x[0]
    dx2_1 = a*x[0] - b*x[1]
    dx2_2 = b*x[1]
    return dx2_0, dx2_1, dx2_2

y1 = odeint(S1, x0, t)
y2 = odeint(S2, x0, t)

plt.plot(t, y1[:,0], label='S(t)')
plt.plot(t, y1[:,1], label='I(t)')
plt.plot(t, y1[:,2], label='R(t)')
plt.title('I(0) <= I*')
plt.legend()

plt.plot(t, y2[:,0], label='S(t)')
plt.plot(t, y2[:,1], label='I(t)')
plt.plot(t, y2[:,2], label='R(t)')
plt.title('I(0) > I*')
plt.legend()
```

# Результаты

## Результат

Для задачи об эпидемии:

Построила слудующие графики:

![Рис. 1. График для 1 случая](image/1.PNG){ #fig:001 width=70% }
![Рис. 2. График для 2 случая](image/2.PNG){ #fig:001 width=70% }

# Вывод

## Вывод

Построила график для задачи об эпидемии.
