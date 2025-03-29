---
## Front matter
title: "Отчет по лабораторной работе №8"
subtitle: "Дисциплина: Имитационное моделирование"
author: "Шошина Евгения Александровна"

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

Реализовать модель TCP/AQM в xcos и OpenModelica.

# Задание

1. Построить модель TCP/AQM в xcos;
2. Построить графики динамики изменения размера TCP окна $W(t)$ и размера очереди $Q(t)$;
3. Построить модель TCP/AQM в OpenModelica;

# Теоретическое введение

Протокол TCP использует механизм динамической регулировки размера окна для предотвращения перегрузок. Уравнение $W(t) = 1/R(t) − (W(t)W(t−R(t)))/(2R(t−R(t)))·p(t−R(t))$ отражает два ключевых режима:  

- **Фаза медленного старта** (первое слагаемое) — линейный рост окна до достижения порога ssthresh;  
- **Фаза избежания перегрузок** (второе слагаемое) — мультипликативное уменьшение окна при детектировании потерь пакетов через функцию p(t).  

Функция p(t) реализует алгоритм AQM (Active Queue Management), который proactively управляет очередью маршрутизатора для минимизации задержек и потерь.

1. **Постоянные N и R** — позволяют анализировать устойчивость системы методами теории управления.  
2. **Линейная зависимость p(t) от Q(t)** — упрощает анализ влияния длины очереди на динамику окна.  

Модель позволяет:  
- Исследовать баланс между скоростью обработки пакетов (C) и интенсивностью трафика (NW/R);  
- Анализировать стабильность системы при различных значениях K;  
- Оптимизировать параметры AQM для соблюдения QoS-требований ($IPTD ≤ 150 мс, IPLR ≤ 10^{-3}$).  

Для учебных целей упрощения оправданы, так как фокусируют внимание на ключевых аспектах взаимодействия TCP и AQM, игнорируя второстепенные факторы (например, вариативность RTT)
[@first; @second].

# Выполнение лабораторной работы

Зададим переменные окружения $N = 1, R = 1, K = 5.3, C = 1, W(0) = 0.1, Q(0) = 1$.(рис. @fig:001).

![Зададим переменные окружения](image/1.jpg){#fig:001 width=70%}

Построим модель TCP/AQM в xcos.

![Схема xcos, моделирующая систему](image/2.jpg){#fig:002 width=70%}

Построим график динамики изменения размера TCP окна W(t) и размера очереди Q(t). При C=1:

![динамики изменения размера TCP окна W(t) и размера очереди Q(t)](image/3.jpg){#fig:003 width=70%}

Построим фазовый портрет (W,Q).

![Фазовый портрет (W,Q)](image/4.jpg){#fig:004 width=70%}

Построим график динамики изменения размера TCP окна W(t) и размера очереди Q(t). При C=0.9:

![динамики изменения размера TCP окна W(t) и размера очереди Q(t)](image/5.jpg){#fig:005 width=70%}

Построим фазовый портрет (W,Q).

![Фазовый портрет (W,Q)](image/6.jpg){#fig:006 width=70%}

Реализуем модель с помощью языка Modelica в среде OpenModelica. Для реализации используем оператор delay().

![Программа на языке Modelica](image/7.jpg){#fig:007 width=70%}

Построим график динамики изменения размера TCP окна W(t) и размера очереди Q(t) в среде OpenModelica.

![динамики изменения размера TCP окна W(t) и размера очереди Q(t)](image/8.jpg){#fig:008 width=70%}

Построим фазовый портрет (W,Q) в среде OpenModelica.

![Фазовый портрет (W,Q)](image/9.jpg){#fig:009 width=70%}

# Выводы

Реализовали модель TCP/AQM в xcos и OpenModelica.

# Список литературы{.unnumbered}

- https://spot.colorado.edu/~lich1539/fn/UtilityMaximization2016.pdf
- https://arxiv.org/pdf/1307.1204
- https://scispace.com/papers/a-two-dimensional-fluid-model-for-tcp-aqm-analysis-1kfrgt1y
