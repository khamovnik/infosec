---
## Front matter
title: "Отчёт по лабораторной работе №4


Информационная безопасность"
subtitle: "Дискреционное разграничение прав в Linux. Расширенные атрибуты"
author: "Выполнил: Маляров Семён Сергеевич, 


НПИбд-01-21, 1032209505"

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
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Получить практические навыки работы в консоли с расширенными атрибутами файлов.

# Теоретическое введение

**Права доступа** определяют, какие действия конкретный пользователь может или не может совершать с определенным файлами 
и каталогами. С помощью разрешений можно создать надежную среду — такую, в которой никто не может поменять содержимое 
ваших документов или повредить системные файлы [1].

**Расширенные атрибуты файлов Linux** представляют собой пары имя: значение, которые постоянно связаны с файлами и 
каталогами, подобно тому как строки окружения связаны с процессом. Атрибут может быть определён или не определён. 
Если он определён, то его значение может быть или пустым, или не пустым [2].

Расширенные атрибуты дополняют обычные атрибуты, которые связаны со всеми inode в файловой системе 
(т. е., данные stat(2)). Часто они используются для предоставления дополнительных возможностей файловой системы, 
например, дополнительные возможности безопасности, такие как списки контроля доступа (ACL), могут быть реализованы 
через расширенные атрибуты [3].

*Установить атрибуты:*

- chattr filename

*Значения:*

- chattr +a # только добавление. Удаление и переименование запрещено;

- chattr +A # не фиксировать данные об обращении к файлу

- chattr +c # сжатый файл

- chattr +d # неархивируемый файл

- chattr +i # неизменяемый файл

- chattr +S # синхронное обновление

- chattr +s # безопасное удаление, (после удаления место на диске переписывается нулями)

- chattr +u # неудаляемый файл

- chattr -R # рекурсия

*Просмотреть атрибуты:*

- lsattr filename

*Опции:*

- lsattr -R # рекурсия

- lsattr -a # вывести все файлы (включая скрытые)

- lsattr -d # не выводить содержимое директории

# Выполнение лабораторной работы

1. От имени пользователя guest определим расширенные атрибуты файла /home/guest/dir1/file1


2. Следующим шагом установим на файл file1 права, разрешающие чтение и запись для владельца файла


3. Попробуем установить на файл /home/guest/dir1/file1 расширенный атрибут «a» от имени пользователя guest


4. Повысим свои права с помощью команды su и попробуем установить расширенный атрибут «a» на файл /home/guest/dir1/file1 
от имени суперпользователя


5. От пользователя guest проверим правильность установления атрибута


6. Затем выполним дозапись в файл file1 слова «test»


7. Выполним чтение файла file1


8. Попробуем стереть имеющуюся в нём информацию


9. Далее попробуем установить на файл file1 права запрещающие чтение и запись для владельца файла


10. Снимем расширенный атрибут «a» с файла /home/guest/dirl/file1 от имени суперпользователя и повторим операции, 
которые нам ранее не удавалось выполнить
    

11. В конце повторим наши действия по шагам, заменив атрибут «a» атрибутом «i»


# Вывод

В ходе выполнения лабораторной работы были получены практические навыки работы в консоли с расширенными атрибутами файлов.

# Список литературы. Библиография

[1] Права доступа: https://codechick.io/tutorials/unix-linux/unix-linux-permissions

[2] Расширенные атрибуты: https://ru.manpages.org/xattr/7

[3] Операции с расширенными атрибутами: https://p-n-z-8-8.livejournal.com/64493.html
