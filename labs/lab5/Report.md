# РОССИЙСКИЙ УНИВЕРСИТЕТ ДРУЖБЫ НАРОДОВ

### Факультет физико-математических и естественных наук 

<br/>
<br/>
<br/>
<br/>

ОТЧЕТ
ПО ЛАБОРАТОРНОЙ РАБОТЕ №5
===============
## Тема:  Дискреционное разграничение прав в Linux. Исследование влияния дополнительных атрибутов
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
Изучение механизмов изменения идентификаторов, применения SetUID- и Sticky-битов. Получение практических навыков работы в консоли с дополнительными атрибутами. Рассмотрение работы механизма смены идентификатора процессов пользователей, а также влияние бита Sticky на запись и удаление файлов.

### Задачи.
1. Создать несколько программ для проверки прав доступа к файлам с использованием SetUID-бита и SetGID-бита. 

2. Провести последовательность тестов над файлами, использующих Sticky-бит. 

## Ход работы
### 1 задание
---
Для начала от имени пользователя guest создадим программу simpleid.c, скомпилируем и выполним её, после чего сравним вывод программы с результатом команды `id`:

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab5/Screenshots/Screenshot_1.png)
<br/>*РИС.1(программа успешно скомпилировалась и сохранилась)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab5/Screenshots/Screenshot_2.png)
<br/>*РИС.2(вывод программы соответствует результату команды id)*

Напишем другую программу, в которой будет производится вывод действительных идентификаторов, скомпилируем и запустим её (рис.3 - рис.4):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab5/Screenshots/Screenshot_3.png)
<br/>*РИС.3(программа успешно скомпилировалась)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab5/Screenshots/Screenshot_4.png)
<br/>*РИС.4(вывод программы)*

Далее от имени суперпользователя изменим владельца файла программы simpleid2 и установим SetUID-бит, потом выполним проверку правильности установки новых атрибутов и смены владельца файла, а также запустим simpleid2 и id (рис.5 - рис.8):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab5/Screenshots/Screenshot_5.png)
<br/>*РИС.5(изменение владельца файла программы simpleid2 и установка SetUID-бита)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab5/Screenshots/Screenshot_6.png)
<br/>*РИС.6(изменение владельца файла программы simpleid2 и установка SetUID-бита прошли успешно)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab5/Screenshots/Screenshot_7.png)
<br/>*РИС.7(результаты программы)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab5/Screenshots/Screenshot_7.1.png)
<br/>*РИС.8(результаты команды)*

Проделаем ту же последовательность действий, но относительно SetGID-бита (рис.9):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab5/Screenshots/Screenshot_8.png)
<br/>*РИС.9*

А сейчас создадим программу readfile.c, скомпилируем её, сменим владельца файла readfile.c и изменим права так, чтобы только суперпользователь (root) мог прочитать его, a guest не мог (рис.10 - рис.11):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab5/Screenshots/Screenshot_9.png)
<br/>*РИС.10(программа успешно скомпилировалась)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab5/Screenshots/Screenshot_10.png)
<br/>*РИС.11(смена владельца и установка прав)*

И попробуем считать файл от имени guest (рис.12):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab5/Screenshots/Screenshot_11.png)
<br/>*РИС.12(в доступе отказано)*

Сменим у программы readfile владельца и установим SetU’D-бит, после чего проверим может ли программа readfile прочитать файл readfile.c и файл /etc/shadow (рис.12 - рис.13):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab5/Screenshots/Screenshot_12.png)
<br/>*РИС.12(смена владельца и установка прав)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab5/Screenshots/Screenshot_13.png)
<br/>*РИС.13(файлы не считываются)*

### 2 задание
---
Теперь проверим, установлен ли атрибут Sticky на директории /tmp, после чего от имени guest создадим файл file01.txt в этой директории со словом "test" и просмотрим атрибуты у только что созданного файла и разрешим чтение и запись для категории пользователей «все остальные» (рис.14 - рис.15):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab5/Screenshots/Screenshot_14.png)
<br/>*РИС.14(атрибут Sticky на директории /tmp установлен)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab5/Screenshots/Screenshot_15.png)
<br/>*РИС.15(атрибут Sticky на директории /tmp установлен)*

А сейчас от имени пользователя guest2 попробуем прочитать файл file01.txt (рис.16):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab5/Screenshots/Screenshot_16.png)
<br/>*РИС.16*

Попробуем дозаписать в этот файл (рис.17), стереть всё его содержимое (рис.18) и удалить его (рис.19):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab5/Screenshots/Screenshot_17.png)
<br/>*РИС.17(отредактировать файл нельзя)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab5/Screenshots/Screenshot_18.png)
<br/>*РИС.18(стереть всё его содержимое нельзя)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab5/Screenshots/Screenshot_19.png)
<br/>*РИС.19(удалить файл нельзя)*

Повысим права до суперпользователя, после этого снимим атрибут t (Sticky-бит) с директории /tmp и покинем режим суперпользователя (рис.20):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab5/Screenshots/Screenshot_20.png)
<br/>*РИС.20*

Повторим предыдущие шаги (рис.21):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab5/Screenshots/Screenshot_21.png)
<br/>*РИС.21(удалось удалить файл)*

Вновь повысим права до суперпользователя, после этого востановим атрибут t (Sticky-бит) в директории /tmp (рис.22):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab5/Screenshots/Screenshot_22.png)
<br/>*РИС.22*

## Заключение
В ходе проделанной лабораторной работы мной были усвоены навыки работы в консоли с дополнительными атрибутами, а также изучены механизмы изменения идентификаторов с применением SetUID- и Sticky-битов.