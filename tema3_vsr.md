# Вариативная самостоятельная работа

### [3.1 Разработка прототипа приложения “Регистрация на конференцию” на основе фрагмента технического задания с использованием ООП.](https://replit.com/@PolinaLazebniko/sem4-Tema3-VSR-31#main.py)
```python
"""
    Лазебникова Полина 
    ИВТ 2 курс
    группа 1.1

    Вариативная самостоятельная работа 
    Задание 3.1: Разработка прототипа приложения “Регистрация на конференцию” на основе фрагмента 
    технического задания с использованием ООП.
"""
class New_client:
    country = "Russia"
    def __init__(self, fname, sname, email, date_of_birth, postalcode, city, sourceinfo):
        
        if (fname != "") and (sname != ""):
            self.__fname = fname
            self.__sname = sname
        else:
            raise ValueError('Поля "Имя" и "Фамилия" должны быть заполнены')

        if self.__check_email(email):
            self.__email = email

        if self.__check_date_of_birth(date_of_birth):
            self.__date_of_birth = date_of_birth

        if len(postalcode) > 3:
            self.__postalcode = postalcode
        
        if city != "":
            self.__city = city

        if sourceinfo != "":
            self.__sourceinfo = sourceinfo

    def __check_email(self, mail):
        if mail.find('@') == -1:
            raise ValueError('Поле "Почта" заполнено некорректно')

        mail_1 = mail.split('@')

        if mail_1[0] == '' or mail_1[1] == '':
            raise ValueError('Поле "Почта" заполнено некорректно')

        if mail_1[1].find('.') == -1:
            raise ValueError('Поле "Почта" заполнено некорректно')
        
        mail_2 = mail_1[1].split('.')
        
        if mail_2[0] == '' or mail_2[1] == '':
            raise ValueError('Поле "Почта" заполнено некорректно')
        else:
            return True

    def __check_date_of_birth(self, date_birth):
        if date_birth.find('.') == -1:
            raise ValueError('Поле "Дата рождения" заполнено некорректно')

        date_birth_1 = date_birth.split('.')

        if date_birth_1[0] == '' or len(date_birth_1[0]) != 2 or date_birth_1[1] == '' or len(date_birth_1[1]) != 2 or date_birth_1[2] == '' or len(date_birth_1[2]) != 2:
            raise ValueError('Поле "Дата рождения" заполнено некорректно')
        else:
            return True

    def getfname(self):
        return self.__fname

    def getsname(self):
        return self.__sname

    def getemail(self):
        return self.__email
    
    def getdate_of_birth(self):
        return self.__date_of_birth

    def getpostalcode(self):
        return self.__postalcode
    
    def getcity(self):
        return self.__city

    def getsourceinfo(self):
        return self.__sourceinfo

def new_client(new_reg):
    print("Имя: ", new_reg.getsname())
    print("Email: ", new_reg.getemail())
    print("Дата рождения: ", new_reg.getdate_of_birth())
    print("Индекс: ", new_reg.getpostalcode())
    print("Город: ", new_reg.getcity())
    print("Откуда узнали: ", new_reg.getsourceinfo())

new_client_reg = New_client('Nick', 'Zhukov', 'zh@mail.ru', '11.02.99', '660012', 'Moskow', 'Из рекламы в вк')
new_client(new_client_reg)
```
### [3.4 Разработка скрипта для получения и сохранения данных социальных сетей Twitter или Instagram.](https://replit.com/@PolinaLazebniko/sem4-Tema3-VSR-34-1#main.py)
```python

```
