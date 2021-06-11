# Инвариантная самостоятельная работа

### [3.1 Разработка классов и объектов «запись», «комментарий» для приложения «Блог» (использование наследования).](https://replit.com/@PolinaLazebniko/sem4-Tema3-ISR-31#main.py)
```python
"""
    Лазебникова Полина 
    ИВТ 2 курс
    группа 1.1

    Инвариантная самостоятельная работа 
    Задание 3.1: Разработка классов и объектов «запись», «комментарий» для приложения «Блог» (использование наследования).
"""

class Post():
    """
    Cоздание поста
    """
    def __init__(self, user_id, text):
        self.id = user_id
        self.text = text

    def __str__(self):
      return f"Author: {self.id}\n Text: {self.text}" 

class Comment(Post): # Наследует класс Post 
    """
    Создание комментария под постом
    """
    def __init__(self, user_id, reply_to, text):
        Post.__init__(self, user_id, text)
        self.text = text
        self.reply_to = reply_to

    def __str__(self):
      return f"Author: {self.id}\n Reply to: {self.reply_to}\n Comment: {self.text}" 

post = Post(user_id='pau', text='Hello!')
print('Post:\n\n', post)
comment = Comment(user_id='wooya', reply_to='pau', text='Hi!')
print('\nComment:\n\n', comment)
```
### [3.2. Создание геттеров и сеттеров для классов «запись», «комментарий» приложения «Гостевая книга». Создание функций для вывода на печать информации, хранящийся в объектах.](https://replit.com/@PolinaLazebniko/sem4-Tema1-ISR-12#main.py)
```python

```
