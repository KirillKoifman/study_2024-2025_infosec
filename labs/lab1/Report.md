# РОССИЙСКИЙ УНИВЕРСИТЕТ ДРУЖБЫ НАРОДОВ

### Факультет физико-математических и естественных наук 

<br/>
<br/>
<br/>
<br/>

ОТЧЕТ
ПО ЛАБОРАТОРНОЙ РАБОТЕ №1
===============
## Тема: Установка и конфигурация операционной системы на виртуальную машину

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
Целью данной работы является приобретение практических навыков установки операционной системы на виртуальную машину, настройки минимально необходимых для дальнейшей работы сервисов.

### Задачи.
1. Установить и настроить виртуальную машину Rocky Linux. 
2. Установить имя пользователя и название хоста и проверить корректность проведённой установки.
3. Получить следующую информацию с помощью команды `dmesg`:
    1. Версия ядра Linux (Linux version).
    2. Частота процессора (Detected Mhz processor).
    3. Модель процессора (CPU0).
    4. Объем доступной оперативной памяти (Memory available).
    5. Тип обнаруженного гипервизора (Hypervisor detected).
    6. Тип файловой системы корневого раздела.
    7. Последовательность монтирования файловых систем.

## Ход работы
### 1 задание
---
Для начала установим образ операционной системы Linux(дистрибутив Rocky) и виртуальную машину VirtualBox, которую запустим (рис.1):
![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab1/Screenshots/1/Screenshot_1.png)
<br/>*РИС.1(окно VirtualBox)*

Теперь создадим новую виртуальную машину и настроим её (рис.2 - рис.7):
![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab1/Screenshots/1/Screenshot_2.png)
<br/>*РИС.2(окно создания новой виртуальной машины. Ввод названия виртуальной машины, типа ОС и пути к ней)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab1/Screenshots/1/Screenshot_3.png)
<br/>*РИС.3(определение объёма выделяемой оперативной памяти и кол-ва процессоров)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab1/Screenshots/1/Screenshot_4.png)
<br/>*РИС.4(определение размера (виртуального) диска)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab1/Screenshots/1/Screenshot_5.png)
<br/>*РИС.5(сформированное описание параметров виртуальной машины)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab1/Screenshots/1/Screenshot_7.png)
<br/>*РИС.6(добавляем новый привод оптических дисков и выбираем установленный ранее образ ОС Rocky Linux)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab1/Screenshots/1/Screenshot_8.png)
<br/>*РИС.7(конечный вариант параметров виртуальной машины)*

Теперь запустим виртуальную машину и произведём её основную настройку перед установкой (рис.8 - рис.17):
![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab1/Screenshots/1/Screenshot_9.png)
<br/>*РИС.8(выбор языка, используемого в процессе установки)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab1/Screenshots/1/Screenshot_10.png)
<br/>*РИС.9(добавляем 2-й язык (русский) и задаём комбинацию клавиш для переключения раскладки)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab1/Screenshots/1/Screenshot_11.png)
<br/>*РИС.10(определение базового окружения и дополнительного программного обеспечения)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab1/Screenshots/1/Screenshot_12.png)
<br/>*РИС.11(отключение KDUMP)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab1/Screenshots/1/Screenshot_13.png)
<br/>*РИС.12(включение сетевого соединения и определение в качестве узла `kdkoyjfman.localdomain`)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab1/Screenshots/1/Screenshot_14.png)
<br/>*РИС.13(установка пароля для root)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab1/Screenshots/1/Screenshot_15.png)
<br/>*РИС.14(установка пароля и прав администратора для пользователя kdkoyjfman)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab1/Screenshots/1/Screenshot_16.png)
<br/>*РИС.15(процесс установки ОС)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab1/Screenshots/1/Screenshot_17.png)
<br/>*РИС.16(завершение процесса установки ОС)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab1/Screenshots/1/Screenshot_18.png)
<br/>*РИС.17(окно виртуальной машины после перезапуска)*

Далее войдём в ОС под заданной нами ранее учётной записью и подключим образ диска дополнений гостевой ОС (рис.18, рис.19):
![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab1/Screenshots/1/Screenshot_19.png)
<br/>*РИС.18*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab1/Screenshots/1/Screenshot_20.png)
<br/>*РИС.19(после загрузки дополнений вновь перезагузим виртуальную машину)*

### 2 задание
---
После этого проверим корректность проведённой установки имён пользователя и хоста (рис.20):
![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab1/Screenshots/2/Screenshot_1.png)
<br/>*РИС.20(имена пользователя и хоста были указаны верно)*

### 3 задание
---
Наконец, воспользуемся командой dmesg, чтобы получить следующую информаицю (рис.21 - рис.27):
![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab1/Screenshots/3/Screenshot_1.png)
<br/>*РИС.21(вывод части последовательности загрузки системы)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab1/Screenshots/3/Screenshot_2.png)
<br/>*РИС.22(вывод информации о версии ядра Linux)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab1/Screenshots/3/Screenshot_3.png)
<br/>*РИС.23(вывод информации о частоте процессора)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab1/Screenshots/3/Screenshot_4.png)
<br/>*РИС.24(вывод информации о модели процессора)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab1/Screenshots/3/Screenshot_5.png)
<br/>*РИС.25(вывод информации об объёме оперативной памяти)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab1/Screenshots/3/Screenshot_6.png)
<br/>*РИС.26(вывод информации о типе обнаруженного гипервизора)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab1/Screenshots/3/Screenshot_7.png)
<br/>*РИС.27(вывод информации о типе файловой системы корневого раздела)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab1/Screenshots/3/Screenshot_8.png)
<br/>*РИС.28(вывод информации о последовательности монтирования файловых систем)*

## Заключение
В ходе продеданной лабораторной работы мной были усвоены навыки установки операционной системы на виртуальную машину, настройки минимально необходимых для дальнейшей работы сервисов.

## Контрольные вопросы
1. Какую информацию содержит учётная запись пользователя? Учётная запись пользователя содержит информацию о логине, пароле пользователя, о его UID и GID.
2. Укажите команды терминала и приведите примеры:
    - для получения справки по команде; команда `man`, `man cd`
    - для перемещения по файловой системе; `cd`, `cd filesdir/`
    - для просмотра содержимого каталога; `ls`, `ls filesdir/`
    - для определения объёма каталога; `du -sh`, `du -sh filesdir/`
    - для создания / удаления каталогов / файлов; `mkdir` и `touch`, `mkdir filesdir/` и `touch file`; `rm -r` и `rm`, `rm -r filesdir` и `rm file`
    - для задания определённых прав на файл / каталог; `chmod`, `chmod +rwx file` и `chmod +w filesdir`
    - для просмотра истории команд. `history`
3. Что такое файловая система? Приведите примеры с краткой характеристикой. Файловая система - способ организации файлов и каталогов на некотором носителе или диске. ext4 - файловая система, которая поддерживает разделение дискового пространства на разные группы для повышения надежности и производительности. NTFS - файловая система, которая поддерживает большие файлы, защиту и сжатие данных.
4. Как посмотреть, какие файловые системы подмонтированы в ОС? Использовать команду `df -h`
5. Как удалить зависший процесс? Использовать команду `kill`