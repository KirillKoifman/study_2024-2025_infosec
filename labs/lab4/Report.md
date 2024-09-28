# РОССИЙСКИЙ УНИВЕРСИТЕТ ДРУЖБЫ НАРОДОВ

### Факультет физико-математических и естественных наук 

<br/>
<br/>
<br/>
<br/>

ОТЧЕТ
ПО ЛАБОРАТОРНОЙ РАБОТЕ №4
===============
## Тема:  Дискреционное разграничение прав в Linux. Расширенные атрибуты
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
дисциплина:  Информационная безопасность

Студент: Койфман Кирилл Дмитриевич

Группа: НПИбд-01-21

<br/>
<br/>
<br/>
<br/>

## Введение.
### Цель работы.
Получение практических навыков работы в консоли с расширенными атрибутами файлов.

### Задачи.
1. Проведём последовательность тестов над файлами с применением расширенного атрибута -a. 

2. Проведём последовательность тестов над файлами с применением расширенного атрибута -i. 

## Ход работы
### 1 задание
---
Для начала от имени пользователя guest определите расширенные атрибуты файла /home/guest/dir1/file1, установим на file1 права, разрешающие чтение и запись для владельца файла, после чего попробуем установить на файл /home/guest/dir1/file1 расширенный атрибут -a от имени пользователя guest (рис.1 - рис.3):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab4/Screenshots/Screenshot_1.png)
<br/>*РИС.1(никакие атрибуты не установлены)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab4/Screenshots/Screenshot_2.png)
<br/>*РИС.2*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab4/Screenshots/Screenshot_3.png)
<br/>*РИС.3(был получен отказ при выполнении операции)*

Откроем третью консоль с правами администратора либо повысьте
свои права с помощью команды su. Попробуйте установить расширенный атрибут a на файл /home/guest/dir1/file1 от имени суперпользователя и проверим результат (рис.4, рис.5):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab4/Screenshots/Screenshot_4.png)
<br/>*РИС.4*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab4/Screenshots/Screenshot_5.png)
<br/>*РИС.5(атрибут был успешно установлен)*

Далее выполним запись в файл file1 слова «test», выполним чтение из файла, после чего попробуем стереть из него информацию и переименовать его (рис.6, рис.7):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab4/Screenshots/Screenshot_6.png)
<br/>*РИС.6(файл был успешно отредактирован)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab4/Screenshots/Screenshot_7.png)
<br/>*РИС.7(операции выполнить не удалось)*

Теперь попробуем установить на файл права, запрещающие чтение и запись для владельца файла (рис.8):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab4/Screenshots/Screenshot_8.png)
<br/>*РИС.8(операцию выполнить не удалось)*

Снимем расширенный атрибут -a с файла и повторим операции, которые не удалось выполнить ранее (рис.9 - 10):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab4/Screenshots/Screenshot_9.png)
<br/>*РИС.9(успешно сняли атрибут)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab4/Screenshots/Screenshot_10.png)
<br/>*РИС.10(успешно выполнили все операции)*

### 2 задание
---
А сейчас повтории все операции по шагам, заменив атрибут «a» атрибутом «i» (рис.11, рис.12):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab4/Screenshots/Screenshot_11.png)
<br/>*РИС.11(успешно установили атрибут)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab4/Screenshots/Screenshot_12.png)
<br/>*РИС.12(операции выполнить после установки атрибута не удалось)*

## Заключение
В ходе проделанной лабораторной работы мной были усвоены навыки работы в консоли с расширенными атрибутами файлов.