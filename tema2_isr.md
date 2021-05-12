# Инвариантная самостоятельная работа

### [2.1 Разработать прототип программы «Калькулятор», позволяющую выполнять базовые арифметические действия и функцию обертку, сохраняющую название выполняемой операции, аргументы и результат в файл](https://replit.com/@PolinaLazebniko/sem4-Tema2-ISR-21#main.py)
```python
"""
    Лазебникова Полина 
    ИВТ 2 курс
    группа 1.1

    Инвариантная самостоятельная работа 
    Задание 2.1: Разработать прототип программы «Калькулятор», позволяющую выполнять 
    базовые арифметические действия и функцию обертку, сохраняющую название выполняемой операции, аргументы и результат в файл.
"""

def is_digit(string):
    if string.isdigit():
       return int(string)
    else:
        try:
            float(string)
            return float(string)
        except ValueError:
            return False

def culc(strForCulc):
    outp = strForCulc
    str2 = list(strForCulc)
    operators ={
        '+': (lambda x, y: x + y),
        '-': (lambda x, y: x - y),
        '*': (lambda x, y: x * y),
        '/': (lambda x, y: x / y),
        '^': (lambda x, y: x ** y)
    }
    operators2 = {
        '+': 'addition',
        '-': 'subtraction',
        '*': 'multiplication',
        '/': 'division',
        '^': 'exponentiation'
    }
    operator = ''
    num = ''
    for i in str2:
        if i in '0123456789.' and operator == '':
            num += i
        elif operator == '':
            x = int(num)
            if i in operators:
                operator = i
            num = ''
        else:
            num += i
    y = int(num)
    outp += ' = '
    lr = (operators.get(operator)(x, y))
    outp += str(lr)
    res2 = operators2.get(operator)
    return [res2, outp]

def decor(f):
    journal = open("journal.txt", "a")
    res = f(str(input()))
    operator, result = res
    journal.write("Операция: ")
    journal.write(operator)
    journal.write(", результат: ")
    journal.write(result)
    journal.write("\n")

decor(culc)
```
### [2.2 Дополнение программы «Калькулятор» декоратором, сохраняющий действия, которые выполняются в файл-журнал.](https://replit.com/@PolinaLazebniko/sem4-Tema2-ISR-22#main.py)
```python
"""
    Лазебникова Полина 
    ИВТ 2 курс
    группа 1.1

    Инвариантная самостоятельная работа 
    Задание 2.2: Дополнение программы «Калькулятор» декоратором, сохраняющий действия, которые выполняются в файл-журнал.
"""

def decor(f):
    def second(*args, **kwargs):
        journal = open("journal.txt", "a")
        operator, result = f(*args)
        journal.write("Операция: ")
        journal.write(operator)
        journal.write(", результат: ")
        journal.write(result)
        journal.write("\n")
    return second

def is_digit(string):
    if string.isdigit():
       return int(string)
    else:
        try:
            float(string)
            return float(string)
        except ValueError:
            return False

@decor
def culc(strForCulc):
    outp = strForCulc
    str2 = list(strForCulc)
    operators ={
        '+': (lambda x, y: x + y),
        '-': (lambda x, y: x - y),
        '*': (lambda x, y: x * y),
        '/': (lambda x, y: x / y),
        '^': (lambda x, y: x ** y)
    }
    operators2 = {
        '+': 'addition',
        '-': 'subtraction',
        '*': 'multiplication',
        '/': 'division',
        '^': 'exponentiation'
    }
    operator = ''
    num = ''
    for i in str2:
        if i in '0123456789.' and operator == '':
            num += i
        elif operator == '':
            x = int(num)
            if i in operators:
                operator = i
            num = ''
        else:
            num += i
    y = int(num)
    outp += ' = '
    lr = (operators.get(operator)(x, y))
    outp += str(lr)
    res2 = operators2.get(operator)
    return [res2, outp]

culc('765*100')
```
### [2.3 Рефакторинг (модификация) программы с декоратором модулем functools и использование его функционала](https://replit.com/@PolinaLazebniko/sem4-Tema2-ISR-23#main.py)
```python
"""
    Лазебникова Полина 
    ИВТ 2 курс
    группа 1.1

    Инвариантная самостоятельная работа 
    Задание 2.3: Рефакторинг (модификация) программы с декоратором модулем functools и использование его функционала.
"""
import functools

def decor(f):
    @functools.wraps(f)
    def second(*args, **kwargs):
        journal = open("journal.txt", "a")
        operator, result = f(*args)
        journal.write("Операция: ")
        journal.write(operator)
        journal.write(", результат: ")
        journal.write(result)
        journal.write("\n")
    return second

def is_digit(string):
    if string.isdigit():
       return int(string)
    else:
        try:
            float(string)
            return float(string)
        except ValueError:
            return False

@decor
def culc(strForCulc):
    outp = strForCulc
    str2 = list(strForCulc)
    operators ={
        '+': (lambda x, y: x + y),
        '-': (lambda x, y: x - y),
        '*': (lambda x, y: x * y),
        '/': (lambda x, y: x / y),
        '^': (lambda x, y: x ** y)
    }
    operators2 = {
        '+': 'addition',
        '-': 'subtraction',
        '*': 'multiplication',
        '/': 'division',
        '^': 'exponentiation'
    }
    operator = ''
    num = ''
    for i in str2:
        if i in '0123456789.' and operator == '':
            num += i
        elif operator == '':
            x = int(num)
            if i in operators:
                operator = i
            num = ''
        else:
            num += i
    y = int(num)
    outp += ' = '
    lr = (operators.get(operator)(x, y))
    outp += str(lr)
    res2 = operators2.get(operator)
    return [res2, outp]

culc('123*505')
```
