# РОССИЙСКИЙ УНИВЕРСИТЕТ ДРУЖБЫ НАРОДОВ

### Факультет физико-математических и естественных наук 

<br/>
<br/>
<br/>
<br/>

ОТЧЕТ
Этап проекта №1
===============
## Тема: Установка Kali Linux

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

## Ход работы
Запустим среду виртуализации VirtualBox и создадим новую виртуальную машину, взяв за основу дистрибутив Kali Linux (рис.1 - рис.4):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/personal-project/stage1/Screenshots/Screenshot_1.png)
<br/>*РИС.1(окно создания новой виртуальной машины. Ввод названия виртуальной машины, типа ОС и пути к ней)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/personal-project/stage1/Screenshots/Screenshot_2.png)
<br/>*РИС.2(сформированное описание базовых параметров системы перед началом установки)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/personal-project/stage1/Screenshots/Screenshot_3.png)
<br/>*РИС.3(выбираем установленный ранее образ ОС Kali Linux)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/personal-project/stage1/Screenshots/Screenshot_4.png)
<br/>*РИС.4(итоговое описание базовых параметров системы перед началом установки)*

Теперь запустим виртуальную машину и произведём её основную настройку перед установкой (рис.5 - рис. 16):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/personal-project/stage1/Screenshots/Screenshot_5.png)
<br/>*РИС.5(окно меню установки)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/personal-project/stage1/Screenshots/Screenshot_6.png)
<br/>*РИС.6(основное меню настройки)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/personal-project/stage1/Screenshots/Screenshot_7.png)
<br/>*РИС.7(включение сетевого соединения и определение в качестве узла `kdkoyjfman.localdomain`)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/personal-project/stage1/Screenshots/Screenshot_8.png)
<br/>*РИС.8(определение имени пользователя)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/personal-project/stage1/Screenshots/Screenshot_9.png)
<br/>*РИС.9(определение пароля пользователя)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/personal-project/stage1/Screenshots/Screenshot_10.png)
<br/>*РИС.10(конфигурация параметров разметки диска)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/personal-project/stage1/Screenshots/Screenshot_11.png)
<br/>*РИС.11(выбор ранее зарезервированного дискогового пространства)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/personal-project/stage1/Screenshots/Screenshot_12.png)
<br/>*РИС.12(выбор размещения всех файлов в общем разделе)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/personal-project/stage1/Screenshots/Screenshot_13.png)
<br/>*РИС.13(подтверждение выбранной конфигурацииы)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/personal-project/stage1/Screenshots/Screenshot_14.png)
<br/>*РИС.14(определение дополнительного программного обеспечения к установке)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/personal-project/stage1/Screenshots/Screenshot_15.png)
<br/>*РИС.15(выбор установки системного загрузчика GRUB)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/personal-project/stage1/Screenshots/Screenshot_16.png)
<br/>*РИС.16(выбор устройства для установки системного загрузчика GRUB)*

После заверешения настройки и установки виртуальной машины, перезапустим её и авторизуемся под созданной ранее учётной записью (рис.17 - рис.18):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/personal-project/stage1/Screenshots/Screenshot_17.png)
<br/>*РИС.17(окно виртуальной машины после перезапуска)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/personal-project/stage1/Screenshots/Screenshot_18.png)
<br/>*РИС.18(открытие терминала под учётной записью созданного пользователя и получение им прав root-пользователя)*

## Заключение
В ходе продеданной лабораторной работы мной были усвоены навыки установки операционной системы на виртуальную машину, настройки минимально необходимых для дальнейшей работы сервисов.