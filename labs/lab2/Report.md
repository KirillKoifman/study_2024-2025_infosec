# РОССИЙСКИЙ УНИВЕРСИТЕТ ДРУЖБЫ НАРОДОВ

### Факультет физико-математических и естественных наук 

<br/>
<br/>
<br/>
<br/>

ОТЧЕТ
ПО ЛАБОРАТОРНОЙ РАБОТЕ №2
===============
## Тема: Дискреционное разграничение прав в Linux. Основные атрибуты

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
Получение практических навыков работы в консоли с атрибутами файлов, закрепление теоретических основ дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux.

### Задачи.
1. Проведём последовательность тестов над атрибутами файлов и каталогов. 

2. Заполним таблицу «Установленные права и разрешённые действия», выполняя действия от имени владельца директории (файлов), определив опытным путём, какие операции разрешены, а какие нет.

3. На основании заполненной таблицы определим минимально необходимые права для выполнения операций внутри директории dir1 и заполним таблицу «Минимальные права для совершения операций».

## Ход работы
### 1 задание
---
Для начала в установленной ОС создадим учётную запись пользователя guest, зададим для неё пароль, после чего войдём в систему от имени этого пользователя (рис.1 - рис.3):
![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab2/Screenshots/Screenshot_1.png)
<br/>*РИС.1(создание учётной записи)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab2/Screenshots/Screenshot_2.png)
<br/>*РИС.2(установка пароля для учётной записи)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab2/Screenshots/Screenshot_3.png)
<br/>*РИС.3(вход в систему через новую учётную запись)*

Далее определим директорию, в которой находимся (рис.4):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab2/Screenshots/Screenshot_4.png)
<br/>*РИС.4(это не домашняя директория guest, поэтому переходим в другую)*

Уточним имя пользователя, его группу, а также группы, куда входит пользователь, с помощью команд id и groups и сравним выведенные результаты (рис.5 - рис.7):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab2/Screenshots/Screenshot_5.png)
<br/>*РИС.5(было установлено, что это пользователь guest)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab2/Screenshots/Screenshot_6.png)
<br/>*РИС.6(вывод имени пользователя, его группы, а также групп, куда он входит, с помощью id)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab2/Screenshots/Screenshot_7.png)
<br/>*РИС.7(вывод группы пользователя, а также групп, куда он входит, с помощью groups)*

Исходя из полученных данных (рис.6, рис.7), можно утверждать, что пользователь guest состоит только в своей группе 1001(guest) и эта информация подтверждатся результатом команды groups.

Также сравним полученную информацию об имени пользователя с данными, выводимыми в приглашении командной строки (рис.8):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab2/Screenshots/Screenshot_8.png)
<br/>*РИС.8(разницы в получаемых данных нет)*

Просмотрим файл /etc/passwd командой `cat`, найдём данные о нашей учётной записи и сравним с теми данными, что получили ранее (рис.9):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab2/Screenshots/Screenshot_9.png)
<br/>*РИС.9(данные uid и gid совпадают)*

Определим существующие в системе директории (рис.10):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab2/Screenshots/Screenshot_10.png)
<br/>*РИС.10(получили информацию о директориях guest и kdkoyjfman с правами на чтение, редактирование и выполнение для владельцев этих директорий)*

А сейчас проверим, какие расширенные атрибуты установлены на поддиректориях, находящихся в директории /home (рис.11):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab2/Screenshots/Screenshot_11.png)
<br/>*РИС.11(удалось получить информацию о расширенных атрибутах домашней директории guest, однако не удалось получить информацию о расширенных атрибутах других директорий)*

Теперь попробуем создать в домашней директории поддиректорию dir1 и определим командами `ls -l` и `lsattr`, какие права доступа и расширенные атрибуты были выставлены на эту директорию (рис.12):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab2/Screenshots/Screenshot_12.png)
<br/>*РИС.12(владелец может считывать, редактировать и выполнять содержимое директории, пока члены группы и остальные только считывать и выполнятью. Расширенные атрибуты не установлены)*

Снимем с директории dir1 все атрибуты (рис.13):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab2/Screenshots/Screenshot_13.png)
<br/>*РИС.13(все атрибуты директории были успешно сняты)*

Наконец, попытаемся создать в директории файл file1 (рис.14):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab2/Screenshots/Screenshot_14.png)
<br/>*РИС.14(создать файл не удалось, потому что ранее мы ограничили права доступа к директории)*

### 2 задание
---
Заполним таблицу «Установленные права и разрешённые действия», выполняя действия от имени владельца директории (файлов), определив опытным путём, какие операции разрешены, а какие нет.
Если операция разрешена, занесём в таблицу знак «+», если не разрешена, знак «-» (таблица 1):

#### ТАБЛИЦА 1
<table>
    <thead>
        <tr>
            <th>Права директории</th>
            <th>Права файла</th>
            <th>Создание файла</th>
            <th>Удаление файла</th>
            <th>Запись в файл</th>
            <th>Чтение файла</th>
            <th>Смена директории</th>
            <th>Просмотр файлов в директории</th>
            <th>Переименование файла</th>
            <th>Смена атрибутов файла</th>
        </tr>
    </thead>
    <tbody>
    <tr>
            <td rowspan=1 align="left">d(000)</td>
            <td rowspan=1 align="left">(000)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(100)</td>
            <td rowspan=1 align="left">(000)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(100)</td>
            <td rowspan=1 align="left">(100)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(100)</td>
            <td rowspan=1 align="left">(200)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(100)</td>
            <td rowspan=1 align="left">(300)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(100)</td>
            <td rowspan=1 align="left">(400)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(100)</td>
            <td rowspan=1 align="left">(500)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(100)</td>
            <td rowspan=1 align="left">(600)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(100)</td>
            <td rowspan=1 align="left">(700)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(200)</td>
            <td rowspan=1 align="left">(000)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(200)</td>
            <td rowspan=1 align="left">(100)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(200)</td>
            <td rowspan=1 align="left">(200)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(200)</td>
            <td rowspan=1 align="left">(300)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(200)</td>
            <td rowspan=1 align="left">(400)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(200)</td>
            <td rowspan=1 align="left">(500)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(200)</td>
            <td rowspan=1 align="left">(600)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(200)</td>
            <td rowspan=1 align="left">(700)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(300)</td>
            <td rowspan=1 align="left">(000)</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(300)</td>
            <td rowspan=1 align="left">(100)</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(300)</td>
            <td rowspan=1 align="left">(200)</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(300)</td>
            <td rowspan=1 align="left">(300)</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(300)</td>
            <td rowspan=1 align="left">(400)</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(300)</td>
            <td rowspan=1 align="left">(500)</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(300)</td>
            <td rowspan=1 align="left">(600)</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(300)</td>
            <td rowspan=1 align="left">(700)</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(400)</td>
            <td rowspan=1 align="left">(000)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(400)</td>
            <td rowspan=1 align="left">(100)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(400)</td>
            <td rowspan=1 align="left">(200)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(400)</td>
            <td rowspan=1 align="left">(300)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(400)</td>
            <td rowspan=1 align="left">(400)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(400)</td>
            <td rowspan=1 align="left">(500)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(400)</td>
            <td rowspan=1 align="left">(600)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(400)</td>
            <td rowspan=1 align="left">(700)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(500)</td>
            <td rowspan=1 align="left">(000)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(500)</td>
            <td rowspan=1 align="left">(100)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(500)</td>
            <td rowspan=1 align="left">(200)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(500)</td>
            <td rowspan=1 align="left">(300)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(500)</td>
            <td rowspan=1 align="left">(400)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(500)</td>
            <td rowspan=1 align="left">(500)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(500)</td>
            <td rowspan=1 align="left">(600)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(500)</td>
            <td rowspan=1 align="left">(700)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(600)</td>
            <td rowspan=1 align="left">(000)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(600)</td>
            <td rowspan=1 align="left">(100)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(600)</td>
            <td rowspan=1 align="left">(200)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(600)</td>
            <td rowspan=1 align="left">(300)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(600)</td>
            <td rowspan=1 align="left">(400)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(600)</td>
            <td rowspan=1 align="left">(500)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(600)</td>
            <td rowspan=1 align="left">(600)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(600)</td>
            <td rowspan=1 align="left">(700)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(700)</td>
            <td rowspan=1 align="left">(000)</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(700)</td>
            <td rowspan=1 align="left">(100)</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(700)</td>
            <td rowspan=1 align="left">(200)</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(700)</td>
            <td rowspan=1 align="left">(300)</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(700)</td>
            <td rowspan=1 align="left">(400)</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(700)</td>
            <td rowspan=1 align="left">(500)</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(700)</td>
            <td rowspan=1 align="left">(600)</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(700)</td>
            <td rowspan=1 align="left">(700)</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
        </tr>
    </tbody>
</table>

### 3 задание
---
На основании заполненной таблицы 1 определим минимально необходимые права для выполнения операций внутри директории dir1 и заполним таблицу 2 (таблица 2):

#### ТАБЛИЦА 2
<table>
    <thead>
        <tr>
            <th>Операция</th>
            <th>Минимальные права на директорию</th>
            <th>Минимальные права на файл</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=1 align="left">Создание файла</td>
            <td rowspan=1 align="left">d(300)</td>
            <td rowspan=1 align="left">(000)</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">Удаление файла</td>
            <td rowspan=1 align="left">d(300)</td>
            <td rowspan=1 align="left">(000)</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">Чтение файла</td>
            <td rowspan=1 align="left">d(100)</td>
            <td rowspan=1 align="left">(400)</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">Запись в файл</td>
            <td rowspan=1 align="left">d(100)</td>
            <td rowspan=1 align="left">(200)</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">Переименование файла</td>
            <td rowspan=1 align="left">d(300)</td>
            <td rowspan=1 align="left">(000)</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">Создание поддиректорииы</td>
            <td rowspan=1 align="left">d(300)</td>
            <td rowspan=1 align="left">(000)</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">Удаление поддиректории</td>
            <td rowspan=1 align="left">d(300)</td>
            <td rowspan=1 align="left">(000)</td>
        </tr>
    </tbody>
</table>

## Заключение
В ходе проделанной лабораторной работы мной были усвоены навыки работы в консоли с атрибутами файлов, закреплены теоретические основы дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux. 