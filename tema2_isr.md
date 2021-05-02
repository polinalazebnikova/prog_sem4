# Инвариантная самостоятельная работа

### [2.1 Разработать прототип программы «Калькулятор», позволяющую выполнять базовые арифметические действия и функцию обертку, сохраняющую название выполняемой операции, аргументы и результат в файл]()
```python

```
### [2.2 Дополнение программы «Калькулятор» декоратором, сохраняющий действия, которые выполняются в файл-журнал.](https://repl.it/@PolinaLazebniko/Tema6-ISR-Zad32)
```python
"""
    Лазебникова Полина 
    ИВТ 2 курс
    группа 1.1

    Инвариантная самостоятельная работа 
    Задание 3.2: Разработка сценария с реализацией операции поиска подстроки в тексте.
"""

def search_all_str(input_str_f, searchable_str_f): 
    """
    Функция для поиска подстроки 

    Входные данные - строка для поиска, строка, по которой идет поиск

    Сначала ищет первое вхождение подстроки, и далее последующие, если вхождений нет,
    то выводит сообщение об этом
    """
    rec = searchable_str_f.find(input_str_f)
    if rec != -1:
        print('Первое вхождение подстроки: ', rec)
    else:
        print('Нет вхождений подстроки')
    while rec != -1:
        rec = searchable_str_f.find(input_str_f, rec + len(input_str_f), len(searchable_str_f))
        if rec != -1:
            print('Вхождение подстроки: ', rec)
        else:
            print('Больше нет вхождений')

def main():
    """
    Функция, которая принимает от пользователя строку для поиска и строку, по которой идет поиск и 
    вызывает функцию search_all_str  
    """
    input_str = input("Введите строку для поиска: ")
    searchable_str = input("Введите строку, по которой идет поиск: ")    
    search_all_str(input_str, searchable_str)

main()
```
### [2.3 Рефакторинг (модификация) программы с декоратором модулем functools и использование его функционала](https://repl.it/@PolinaLazebniko/Tema6-ISR-Zad33)
```python
"""
    Лазебникова Полина 
    ИВТ 2 курс
    группа 1.1

    Инвариантная самостоятельная работа 
    Задание 3.3: Создание скрипта для считывания данных справочных логов из текстового 
    файла и преобразования их в CSV-формат с последующей записью в новый файл.
"""

import json
import csv

def json_f():
    """
    Функция для работы с json
    """
    handle = open('MOCK_DATA.json')
    lines = json.load(handle)
    return lines

def csv_f(lines):
    """
    Функция для работы с csv
    """
    with open('eggs.csv', 'w', newline='') as csvfile:
        csv_writer = csv.writer(
            csvfile, delimiter=';', quotechar='"',
            quoting=csv.QUOTE_MINIMAL)
        csv_writer.writerow(list(lines[0].keys()))
        for line in lines:
            csv_writer.writerow(list(line.values()))

csv_f(json_f())
```
