# РОССИЙСКИЙ УНИВЕРСИТЕТ ДРУЖБЫ НАРОДОВ

### Факультет физико-математических и естественных наук 

<br/>
<br/>
<br/>
<br/>

ОТЧЕТ
ПО ЛАБОРАТОРНОЙ РАБОТЕ №3
===============
## Тема:  Дискреционное разграничение прав в Linux. Два пользователя
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
Получение практических навыков работы в консоли с атрибутами файлов для групп пользователей.

### Задачи.
1. Проведём последовательность тестов над атрибутами файлов и каталогов. 

2. Заполним таблицу «Установленные права и разрешённые действия», выполняя действия от имени пользователя guest и делая проверку от пользователя guest2.

3. На основании заполненной таблицы определим минимально необходимые права для выполнения операций внутри директории dir1 и заполним таблицу «Минимальные права для совершения операций».

## Ход работы
### 1 задание
---
Для начала в установленной ОС создадим учётные записи пользователей guest и guest2 и зададим для них пароли(рис.1 - рис.3):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab2/Screenshots/Screenshot_1.png)
<br/>*РИС.1(создание учётной записи guest)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab2/Screenshots/Screenshot_2.png)
<br/>*РИС.2(установка пароля для учётной записи guest)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab3/Screenshots/Screenshot_1.png)
<br/>*РИС.3(создание учётной записи guest и установка пароля для неё)*

Добавим пользователя guest2 в группу guest (рис.4):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab3/Screenshots/Screenshot_2.png)
<br/>*РИС.4*

Далее войдём в систему от 2-х пользователей на 2-х разных консолях и определим директорию, в которой находится каждый пользователь (рис.5 - рис.6):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab3/Screenshots/Screenshot_3.png)
<br/>*РИС.5(вход в систему для guest)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab3/Screenshots/Screenshot_4.png)
<br/>*РИС.6(вход в систему для guest2)*

Определим директорию, в которой находится каждый пользователь (рис.7, рис.8):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab3/Screenshots/Screenshot_5.png)
<br/>*РИС.7(директория guest)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab3/Screenshots/Screenshot_6.png)
<br/>*РИС.8(директория guest2)*

Уточним имя пользователя, его группу, а также группы, куда входит пользователь, с помощью команд id (с опциями -GN и -G) и groups и сравним выведенные результаты (рис.9 - рис.14):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab3/Screenshots/Screenshot_7.png)
<br/>*РИС.9(имя пользователя, его группу, а также группы, куда входит пользователь guest)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab3/Screenshots/Screenshot_8.png)
<br/>*РИС.10(имя пользователя, его группу, а также группы, куда входит пользователь guest2)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab3/Screenshots/Screenshot_9.png)
<br/>*РИС.11(группы, куда входит пользователь guest)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab3/Screenshots/Screenshot_10.png)
<br/>*РИС.12(группы, куда входит пользователь guest2)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab3/Screenshots/Screenshot_11.png)
<br/>*РИС.13(полученный результат о guest соответствует имеющимся данным)*

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab3/Screenshots/Screenshot_12.png)
<br/>*РИС.14(полученный результат о guest2 соответствует имеющимся данным)*

Сравним полученную информацию с содержимым файла `/etc/group` (рис.15):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab3/Screenshots/Screenshot_13.png)
<br/>*РИС.15(полученная информация соответствует имеющимся данным)*

От имени пользователя guest2 выполним регистрацию guest2 в группе guest (рис.16):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab3/Screenshots/Screenshot_14.png)
<br/>*РИС.16*

После чего от имени пользователя guest изменим права директории /home/guest, разрешив все действия для пользователей группы (рис.17):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab3/Screenshots/Screenshot_15.png)
<br/>*РИС.17*

Далее От имени пользователя guest снимем с директории /home/guest/dir1 все атрибуты и проверим результат операции (рис.18):

![pic](https://raw.githubusercontent.com/KirillKoifman/study_2024-2025_infosec/master/labs/lab3/Screenshots/Screenshot_16.png)
<br/>*РИС.18(атрибуты были успешно сняты)*

### 2 задание
---
Теперь заполним таблицу «Установленные права и разрешённые действия для групп», выполняя действия от имени владельца директории (файлов), определив опытным путём, какие операции разрешены, а какие нет.
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
            <td rowspan=1 align="left">d(010)</td>
            <td rowspan=1 align="left">(000)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(010)</td>
            <td rowspan=1 align="left">(010)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(010)</td>
            <td rowspan=1 align="left">(020)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(010)</td>
            <td rowspan=1 align="left">(030)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(010)</td>
            <td rowspan=1 align="left">(040)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(010)</td>
            <td rowspan=1 align="left">(050)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(010)</td>
            <td rowspan=1 align="left">(060)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(010)</td>
            <td rowspan=1 align="left">(070)</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
            <td rowspan=1 align="left">-</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">d(020)</td>
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
            <td rowspan=1 align="left">d(020)</td>
            <td rowspan=1 align="left">(010)</td>
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
            <td rowspan=1 align="left">d(020)</td>
            <td rowspan=1 align="left">(020)</td>
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
            <td rowspan=1 align="left">d(020)</td>
            <td rowspan=1 align="left">(030)</td>
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
            <td rowspan=1 align="left">d(020)</td>
            <td rowspan=1 align="left">(040)</td>
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
            <td rowspan=1 align="left">d(020)</td>
            <td rowspan=1 align="left">(050)</td>
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
            <td rowspan=1 align="left">d(020)</td>
            <td rowspan=1 align="left">(060)</td>
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
            <td rowspan=1 align="left">d(020)</td>
            <td rowspan=1 align="left">(070)</td>
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
            <td rowspan=1 align="left">d(030)</td>
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
            <td rowspan=1 align="left">d(030)</td>
            <td rowspan=1 align="left">(010)</td>
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
            <td rowspan=1 align="left">d(030)</td>
            <td rowspan=1 align="left">(020)</td>
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
            <td rowspan=1 align="left">d(030)</td>
            <td rowspan=1 align="left">(030)</td>
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
            <td rowspan=1 align="left">d(030)</td>
            <td rowspan=1 align="left">(040)</td>
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
            <td rowspan=1 align="left">d(030)</td>
            <td rowspan=1 align="left">(050)</td>
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
            <td rowspan=1 align="left">d(030)</td>
            <td rowspan=1 align="left">(060)</td>
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
            <td rowspan=1 align="left">d(030)</td>
            <td rowspan=1 align="left">(070)</td>
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
            <td rowspan=1 align="left">d(040)</td>
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
            <td rowspan=1 align="left">d(040)</td>
            <td rowspan=1 align="left">(010)</td>
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
            <td rowspan=1 align="left">d(040)</td>
            <td rowspan=1 align="left">(020)</td>
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
            <td rowspan=1 align="left">d(040)</td>
            <td rowspan=1 align="left">(030)</td>
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
            <td rowspan=1 align="left">d(040)</td>
            <td rowspan=1 align="left">(040)</td>
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
            <td rowspan=1 align="left">d(040)</td>
            <td rowspan=1 align="left">(050)</td>
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
            <td rowspan=1 align="left">d(040)</td>
            <td rowspan=1 align="left">(060)</td>
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
            <td rowspan=1 align="left">d(040)</td>
            <td rowspan=1 align="left">(070)</td>
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
            <td rowspan=1 align="left">d(050)</td>
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
            <td rowspan=1 align="left">d(050)</td>
            <td rowspan=1 align="left">(010)</td>
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
            <td rowspan=1 align="left">d(050)</td>
            <td rowspan=1 align="left">(020)</td>
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
            <td rowspan=1 align="left">d(050)</td>
            <td rowspan=1 align="left">(030)</td>
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
            <td rowspan=1 align="left">d(050)</td>
            <td rowspan=1 align="left">(040)</td>
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
            <td rowspan=1 align="left">d(050)</td>
            <td rowspan=1 align="left">(050)</td>
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
            <td rowspan=1 align="left">d(050)</td>
            <td rowspan=1 align="left">(060)</td>
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
            <td rowspan=1 align="left">d(050)</td>
            <td rowspan=1 align="left">(070)</td>
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
            <td rowspan=1 align="left">d(060)</td>
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
            <td rowspan=1 align="left">d(060)</td>
            <td rowspan=1 align="left">(010)</td>
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
            <td rowspan=1 align="left">d(060)</td>
            <td rowspan=1 align="left">(020)</td>
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
            <td rowspan=1 align="left">d(060)</td>
            <td rowspan=1 align="left">(030)</td>
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
            <td rowspan=1 align="left">d(060)</td>
            <td rowspan=1 align="left">(040)</td>
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
            <td rowspan=1 align="left">d(060)</td>
            <td rowspan=1 align="left">(050)</td>
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
            <td rowspan=1 align="left">d(060)</td>
            <td rowspan=1 align="left">(060)</td>
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
            <td rowspan=1 align="left">d(060)</td>
            <td rowspan=1 align="left">(070)</td>
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
            <td rowspan=1 align="left">d(070)</td>
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
            <td rowspan=1 align="left">d(070)</td>
            <td rowspan=1 align="left">(010)</td>
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
            <td rowspan=1 align="left">d(070)</td>
            <td rowspan=1 align="left">(020)</td>
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
            <td rowspan=1 align="left">d(070)</td>
            <td rowspan=1 align="left">(030)</td>
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
            <td rowspan=1 align="left">d(070)</td>
            <td rowspan=1 align="left">(040)</td>
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
            <td rowspan=1 align="left">d(070)</td>
            <td rowspan=1 align="left">(050)</td>
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
            <td rowspan=1 align="left">d(070)</td>
            <td rowspan=1 align="left">(060)</td>
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
            <td rowspan=1 align="left">d(070)</td>
            <td rowspan=1 align="left">(070)</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">+</td>
            <td rowspan=1 align="left">-</td>
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
            <td rowspan=1 align="left">d(030)</td>
            <td rowspan=1 align="left">(000)</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">Удаление файла</td>
            <td rowspan=1 align="left">d(030)</td>
            <td rowspan=1 align="left">(000)</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">Чтение файла</td>
            <td rowspan=1 align="left">d(010)</td>
            <td rowspan=1 align="left">(040)</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">Запись в файл</td>
            <td rowspan=1 align="left">d(010)</td>
            <td rowspan=1 align="left">(020)</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">Переименование файла</td>
            <td rowspan=1 align="left">d(030)</td>
            <td rowspan=1 align="left">(000)</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">Создание поддиректорииы</td>
            <td rowspan=1 align="left">d(030)</td>
            <td rowspan=1 align="left">(000)</td>
        </tr>
        <tr>
            <td rowspan=1 align="left">Удаление поддиректории</td>
            <td rowspan=1 align="left">d(030)</td>
            <td rowspan=1 align="left">(000)</td>
        </tr>
    </tbody>
</table>

## Заключение
В ходе проделанной лабораторной работы мной были усвоены навыки работы в консоли с атрибутами файлов для групп пользователей.