---
## Front matter
lang: ru-RU
title: "Лабораторная работа №12"
subtitle: "Дисциплина: Имитационное моделирование"
author:
  - Шошина Е.А.
institute:
  - Группа НФИбд-01-22
  - Российский университет дружбы народов, Москва, Россия
date: 26 апреля 2025

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

  * Шошина Евгения Александровна
  * Студентка 3го курса, группа НФИбд-01-22
  * Фундаментальная информатика и информационные технологии
  * Российский университет дружбы народов
  * [Ссылка на репозиторий гитхаба eashoshina](https://github.com/eashoshina/study_2024-2025_simmod)

:::
::: {.column width="30%"}

:::
::::::::::::::

# Вводная часть

## Цели и задачи

Реализовать простой протокол передачи данных в CPN Tools.

## Задание

1. Реализовать простой протокол передачи данных в CPN Tools.
2. Вычислить пространство состояний, сформировать отчет о нем и построить граф.

## Задание деклараций системы

![Задание деклараций](image/1.jpeg){#fig:001 width=40%}

## Построим начальный граф

![Начальный граф](image/2.jpeg){#fig:002 width=60%}

## Добавление промежуточных состояний

![Добавление промежуточных состояний](image/3.jpeg){#fig:003 width=60%}

## Задание деклараций

![Задание деклараций](image/11.jpeg){#fig:004 width=60%}

## Модель простого протокола передачи данных

![Модель простого протокола передачи данных](image/4.jpeg){#fig:005 width=70%}

## Запуск модели простого протокола передачи данных

![Запуск модели простого протокола передачи данных](image/5.jpeg){#fig:006 width=70%}

## Упражнение (отчёт о пространстве состояний)

```
Statistics
------------------------------------------------------------------------
  State Space
     Nodes:  26881
     Arcs:   442501
     Secs:   300
     Status: Partial
  Scc Graph
     Nodes:  14135
     Arcs:   371353
     Secs:   15
```

## Упражнение (отчёт о пространстве состояний)

```
Home Properties
------------------------------------------------------------------------
  Home Markings
     None
 Liveness Properties
------------------------------------------------------------------------
  Dead Markings
     9476 [26881,26880,26879,26878,26877,...]
  Dead Transition Instances
     None
  Live Transition Instances
     None
```

## Пространство состояний

![Пространство состояний для модели простого протокола передачи данных](image/7.jpeg){#fig:008 width=30%}

## Пространство состояний

![Пространство состояний для модели простого протокола передачи данных](image/8.jpeg){#fig:009 width=60%}

## Пространство состояний

![Пространство состояний для модели простого протокола передачи данных](image/9.jpeg){#fig:009 width=60%}

# Результаты

В ходе выполнения данной лабораторной работы я реализовала простой протокол передачи данных в CPN Tools.

# Список литературы{.unnumbered}
- https://cpntools.org/wp-content/uploads/2018/01/simpleprotocol.pdf
- http://simulation.su/uploads/files/default/2015-maksimov-chaliy.pdf
- https://vestnik.rsreu.ru/images/archive/2023/86/2.3-.pdf
