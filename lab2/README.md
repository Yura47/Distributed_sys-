# **Лабораторна робота №2**

-----------------------------------
## Необхідні ресурси:
- Встановлений компілятор для Python.

## Інформація про програму:
- Виводить в терміналі "Hello World!".
- Виконує команди: ping, echo, login, list, msg, file, exit.

## Опис Команд:
### 1. Команда `ping <Address: String>`.
#### Ця команда перевіряє зєднання з сервером, сайтом чи будь-яким іншим пристроєм за вказаною IP або DNS адресою. Дані команді передається тільки один параметр - `<Address: String>`
#### Результатом виконання у разі успішного зєднання в першому рядку записується `Ping <Address: String> ...` і в наступному рядку `Ping <Address: String> request success.`.
#### Якщо ж кількість введених параметрів не буде рівна "1", то замість результату виводиться повідомлення з описом помилки в дужках`PING ERROR (Incorect input argument)`

### Приклад виконання команди:
```text
rybolov@rybolov-VirtualBox:~/Distributed_Sys/Distributed_sys-/lab2$ python3 lab2.py
Hello World!
========================================
Input Command: ping google.com
Entered command = "ping", parameters = ['google.com']
----------------------------------------

Results:
Ping google.com ...
Ping google.com request success.
========================================
Input Command: ping 168.190.2.1
Entered command = "ping", parameters = ['168.190.2.1']
----------------------------------------

Results:
Ping 168.190.2.1 ...
Ping 168.190.2.1 request success.
========================================
Input Command: ping
Entered command = "ping", parameters = []
----------------------------------------

Results:
PING ERROR (Incorect input argument)
========================================

```

### 2. Команда `echo <anyText: String> <anyText: String> ...`.
#### Ця команда виводить на екрані текст з вхідних параметрів - `<anyText: String>`. Ця команда може отримувати будь-яку кількість параметрів. Кожний параметр відображається в новому рядку.

### Приклад виконання команди:
```text
Input Command: echo good morning! 
Entered command = "echo", parameters = ['good', 'morning!', '']
----------------------------------------

Results:
good
morning!

========================================
Input Command: echo TESTTEST
Entered command = "echo", parameters = ['TESTTEST']
----------------------------------------

Results:
TESTTEST
========================================
Input Command: echo "good morning!"
Entered command = "echo", parameters = ['good morning!']
----------------------------------------

Results:
good morning!
========================================
```

### 3. Команда `login <login: String> <password: String>`.
#### Ця команда дозволяє користувачу залогінитися. Дані команді передається два параметри - `<login: String>` і `<password: String>`.
#### Результатом виконання команди буде:
- Якщо логін даного користувача немає в базі даних, то в консолі виводиться `LOGIN ERROR (Incorect input login or password)`.
- Якщо логін даного користувача є в базі даних, але відповідний до нього пароль введений неправильно, то в консолі виводиться `LOGIN ERROR (Incorect input login or password)`.
- Якщо логін даного користувача є в базі даних, і відповідний до нього пароль введений правильно, то в першому рядку консолі виводиться - `LOGIN SUCCESS:`, а в наступному рядку - `Hello, <nameUsers: String>`.
- Якщо кількість введених параметрів не дорівнює 2, то в консолі виводиться `LOGIN ERROR (Incorect input argument)`.

### Приклад виконання команди:
```text
========================================
Input Command: login 1std std11
Entered command = "login", parameters = ['1std', 'std11']
----------------------------------------

Results:
LOGIN SUCCESS:
 Hello, Student1
========================================
Input Command: login 2std std
Entered command = "login", parameters = ['2std', 'std']
----------------------------------------

Results:
LOGIN ERROR (Incorect input login or password)
========================================
Input Command: login 2std std22 
Entered command = "login", parameters = ['2std', 'std22']
----------------------------------------

Results:
LOGIN SUCCESS:
 Hello, Student2
========================================
Input Command: login 3std std22
Entered command = "login", parameters = ['3std', 'std22']
----------------------------------------

Results:
LOGIN ERROR (Incorect input login or password)
========================================
```

### 4. Команда `list`.
#### Ця команда виводить на екран список назв всіх зареєстрованих користувачів які знаходяться в базі даних. Для цієї команди не потрібно вводити параметри, якщо було введено параметри то вони ігноруються. Назва кожного користувача відображається в новому рядку з його поряковим номером - `<№Users: Int>. <nameUsers: String>` .
#### База даних:
- user_names = `Student1`, `Student2`, `Student3`, `Student4`
- user_logins = `1std`, `2std`, `3std`, `4std`
- user_passwords = `std11`, `std22`, `std33`, `std44`

### Приклад виконання команди:
```text
========================================
Input Command: list
Entered command = "list", parameters = []
----------------------------------------

Results:
1. Student1
2. Student2
3. Student3
4. Student4
========================================

```

### 5. Команда `msg <destinationUser: String> <text: String>`.
#### Ця команда надсилає текстове повідомлення іншому користувачу. Дані команді передається два параметри - `<destinationUser: String>` і ` <text: String>`.
#### Результатом виконання команди буде:
- Якщо назви даного користувача немає в базі даних, то в консолі виводиться `MESSAGE SENDING ERROR (This user not found)`.
- Якщо назва даного користувача є в базі даних, то в консолі виводиться `MESSAGE SENDING SUCCESS`.
- Якщо кількість введених параметрів не дорівнює 2, то в консолі виводиться `MESSAGE SENDING ERROR (Incorect input argument)`.

### Приклад виконання команди:
```text
rybolov@rybolov-VirtualBox:~/Distributed_Sys/Distributed_sys-/lab2$ python3 lab2.py
Hello World!
========================================
Input Command: msg Srudent3 'Zdorov'
Entered command = "msg", parameters = ['Srudent3', 'Zdorov']
----------------------------------------

Results:
MESSAGE SENDING ERROR (This user not found)
========================================
Input Command: msg Student3 'Correct std'
Entered command = "msg", parameters = ['Student3', 'Correct std']
----------------------------------------

Results:
MESSAGE SENDING SUCCESS
========================================
```

### 6. Команда `file <destinationUser: String> <filename: String>`.
#### Ця команда надсилає файлове повідомлення іншому користувачу. Дані команді передається два параметри - `<destinationUser: String>` і ` <filename: String>`.
#### Результатом виконання команди буде:
- Якщо назви даного користувача немає в базі даних, то в консолі виводиться `FILE SENDING ERROR (User not found)`.
- Якщо назва даного користувача є в базі даних, але даного файлу немає, то в консолі виводиться `FILE SENDING ERROR (File not found)`.
- Якщо назва даного користувача є в базі даних, і цей файл існує, то в консолі виводиться `FILE SENDING SUCCESS`.
- Якщо кількість введених параметрів не дорівнює 2, то в консолі виводиться `FILE SENDING ERROR (Incorect input argument)`.

### Приклад виконання команди:
```text
rybolov@rybolov-VirtualBox:~/Distributed_Sys/Distributed_sys-/lab2$ python3 lab2.py
Hello World!
========================================
Input Command: file Student1 Lab
Entered command = "file", parameters = ['Student1', 'Lab']
----------------------------------------

Results:
FILE SENDING ERROR (File not found)
========================================
Input Command: file wrongperson lab2.py
Entered command = "file", parameters = ['wrongperson', 'lab2.py']
----------------------------------------

Results:
FILE SENDING ERROR (User not found)
========================================
Input Command: file Sudent2 lab2.py
Entered command = "file", parameters = ['Sudent2', 'lab2.py']
----------------------------------------

Results:
FILE SENDING ERROR (User not found)
========================================
Input Command: file Student2 lab2.py
Entered command = "file", parameters = ['Student2', 'lab2.py']
----------------------------------------

Results:
FILE SENDING SUCCESS
========================================
```

### 7. Команда `exit`.
#### Ця команда виходить з циклу для опитування введення команд. Для цієї команди не потрібно вводити параметри, якщо було введено параметри то вони ігноруються.
- Результатом виконання команди буде - `Exit from cycle`

### Приклад виконання команди:
```text
rybolov@rybolov-VirtualBox:~/Distributed_Sys/Distributed_sys-/lab2$ python3 lab2.py
Hello World!
========================================
Input Command: list
Entered command = "list", parameters = []
----------------------------------------

Results:
1. Student1
2. Student2
3. Student3
4. Student4
========================================
Input Command: exit
Entered command = "exit", parameters = []
----------------------------------------

Results:
Exit from cycle
```

### Примітка: щоб ввести текст в якому містяться символ " " потрібно використовувати oдинарні або подвійні дужки в кінці і на початку тексту.
### Примітка: Якщо було некоректно введено команду або її не існує, то в консолі виводиться `No Command = "<comand>"`.

```text
rybolov@rybolov-VirtualBox:~/Distributed_Sys/Distributed_sys-/lab2$ python3 lab2.py
Hello World!
========================================
Input Command: comand
Entered command = "comand", parameters = []
----------------------------------------

Results:
No Command = "comand"
========================================
```
