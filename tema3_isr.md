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
### [3.2. Создание геттеров и сеттеров для классов «запись», «комментарий» приложения «Гостевая книга». Создание функций для вывода на печать информации, хранящийся в объектах.](https://replit.com/@PolinaLazebniko/sem4-Tema3-ISR-32#main.py)
```python
"""
    Лазебникова Полина 
    ИВТ 2 курс
    группа 1.1

    Инвариантная самостоятельная работа 
    Задание 3.2: Создание геттеров и сеттеров для классов «запись», «комментарий» приложения. Создание функций для вывода 
    на печать информации, хранящийся в объектах.
"""

class Post():
    """
    Cоздание поста
    """
    def __init__(self, user_id, text):
      self.__verify_text(user_id)
      self.__verify_text(text)
      self.__user_id = user_id
      self.__user_text = text

    # id пользователя
    @property
    def id_user(self):
      return self.__user_id # getter
    
    @id_user.setter
    def id_user(self, user_id): #setter
      try:
        self.__verify_text(user_id)
      except ValueError as e:
        print(e)
      else:
        self.__user_id = user_id

    # комментарий
    @property
    def text_post(self):
      return self.__user_text
    
    @text_post.setter
    def text_post(self, text):
      try:
        self.__verify_text(text)
      except ValueError as e:
        print(e)
      else:
        self.__user_text = text 

    def __verify_text(self, text,field='text'):
      if len(text) == 0:
        raise ValueError(f'Поле {field} обязательное поле')

    def __str__(self):
      return f"Author: {self.id_user}\n Text: {self.text_post}" 

class Comment(Post): # Наследует класс Post 
    """
    Создание комментария под постом
    """
    def __init__(self, user_id, reply_to, text):
        Post.__init__(self, user_id, text)
        self.text = text
        self.reply_to = reply_to

    def __str__(self):
      return f"Author: {self.id_user}\n Reply to: {self.reply_to}\n Comment: {self.text}" 

post = Post(user_id='pau', text='Hello!')
print('Post:\n\n', post)
comment = Comment(user_id='wooya', reply_to='pau', text='Hi!')
print('\nComment:\n\n', comment)
```
