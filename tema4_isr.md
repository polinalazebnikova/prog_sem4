# Инвариантная самостоятельная работа

### [4.1 Создание программы по заполнению массивов случайными значениями. Сортировка значений в списке методом вставки, плавной сортировки, с помощью встроенных функций языка.](https://replit.com/@PolinaLazebniko/sem4-Tema4-ISR-41#main.py)
```python
"""
    Лазебникова Полина 
    ИВТ 2 курс
    группа 1.1

    Инвариантная самостоятельная работа 
    Задание 4.1: Создание программы по заполнению массивов случайными значениями. Сортировка 
    значений в списке методом вставки, плавной сортировки, с помощью встроенных функций языка.
"""
import random 

massiv=[] 
for i in range(10): 
    massiv.append(random.randint(-100, 100)) 
print("Массив\n", massiv)

def insertionSort(mas = []):
    """
    Метод вставки
    """
    n = len(mas)
    for i in range(1, n):
        elChange = mas[i]
        k = i - 1
        while ((k >= 0)&(mas[k] > elChange)):
            mas[k + 1] = mas[k]
            k -= 1
        mas[k + 1] = elChange
    return mas

print("Сортировка методом вставки\n", insertionSort(massiv))

mas_sort = sorted(massiv)
print("Сортировка с помощью встроенных функций языка\n", mas_sort)
```
### [4.2 Создание программы по распределению списка с случайными значениями на два списка по определенному критерию (четность/нечетность, положительные/отрицательные числа).](https://replit.com/@PolinaLazebniko/sem4-Tema4-ISR-42#main.py)
```python
"""
    Лазебникова Полина 
    ИВТ 2 курс
    группа 1.1

    Инвариантная самостоятельная работа 
    Задание 4.2: Создание программы по заполнению массивов случайными значениями. Сортировка 
    значений в списке методом вставки, плавной сортировки, с помощью встроенных функций языка.
"""

def separateList(mas = []):
    """
    Разделение списка на два списка по признаку "положительные/отрицательные числа"
    """
    mas1 = []
    mas2 = []
    for i in mas:
        if (i >= 0):
            mas1 += [i]
        else:
            mas2 += [i]
    return mas1, mas2

a = [4, 5, 56, 1, 43, 909, 12, -13, -5, 3, -17, 2647893, -92826]
print(separateList(a))
```
