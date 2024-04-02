# Тема 8. Введение в ООП
Отчет по Теме #8 выполнил(а):
- Катаев Виктор Алексеевич
- ИНО ЗБ ПОАС-22-1

| Задание | Сам_раб |
| ------ | ------ |
| Задание 1 | + |
| Задание 2 | + |
| Задание 3 | + |
| Задание 4 | + |
| Задание 5 | + |

знак "+" - задание выполнено; знак "-" - задание не выполнено;

Работу проверили:
- к.э.н., доцент Панов М.А.

## Самостоятельная работа №1
### Самостоятельно создать класс и его объект.
Создадим класс Person, представляющий человека. Этот класс будет иметь атрибуты для хранения имени, возраста и профессии человека.
```python
class Person:
    def __init__(self, name, age, profession):
        self.name = name
        self.age = age
        self.profession = profession

# Создаем объект класса Person
person1 = Person("Виктор", 23, "Системный администратор")
```
### Результат.
![image](https://github.com/lowfl3xx3r/main/blob/Tema8/pics/lab8_1.png)

## Самостоятельная работа №2
### Самостоятельно создать атрибуты и методы для ранее созданного класса.
Для класса Person добавим метод, который будет выводить информацию о человеке, а также атрибут, который будет хранить информацию о месте проживания.
```python
class Person:
    def __init__(self, name, age, profession, residence):
        self.name = name
        self.age = age
        self.profession = profession
        self.residence = residence
    def introduce(self):
        print(f"Привет! Меня зовут {self.name}. Мне {self.age}. Моя профессия - {self.profession}. Я живу в городе {self.residence}")
person1 = Person("Виктор", 23, "Системный администратор", "Екатеринбург")
person1.introduce()
```
### Результат.
![image](https://github.com/lowfl3xx3r/main/blob/Tema8/pics/lab8_2.png)

## Самостоятельная работа №3
### Самостоятельно реализуйте наследование, продолжая работать с ранее созданным классом
Создадим подкласс Employee, который будет наследовать функциональность класса Person и добавит дополнительный атрибут и метод для работы с зарплатой.
```python
class Person:
    def __init__(self, name, age, profession, residence):
        self.name = name
        self.age = age
        self.profession = profession
        self.residence = residence
    def introduce(self):
        print(f"Привет! Меня зовут {self.name}. Мне {self.age}. Моя профессия - {self.profession}. Я живу в городе {self.residence}")
class Employee(Person):
    def __init__(self, name, age, profession, residence, salary):
        super().__init__(name, age, profession, residence)
        self.salary = salary
person1 = Person("Виктор", 23, "Системный администратор", "Екатеринбург")
person1.introduce()
employee1 = Employee("Алиса", 25, "Разработчик", "Екатеринбург", 75000)
employee1.introduce()
```
### Результат.
![image](https://github.com/lowfl3xx3r/main/blob/Tema8/pics/lab8_3.png)

## Самостоятельная работа №4
### Самостоятельно реализуйте инкапсуляцию, продолжая работать с ранее созданным классом

```python
class Person:
    def __init__(self, name, age, profession, residence):
        self._name = name
        self._age = age
        self._profession = profession
        self._residence = residence
    def get_name(self):
        return self._name
    def get_age(self):
        return self._age
    def get_profession(self):
        return self._profession
    def get_residence(self):
        return self._residence
    def introduce(self):
        print(f"Привет! Меня зовут {self._name}. Мне {self._age}. Моя профессия - {self._profession}. Я живу в городе {self._residence}")
person1 = Person("Виктор", 23, "Системный администратор", "Екатеринбург")
person1.introduce()
class Employee(Person):
    def __init__(self, name, age, profession, residence, salary):
        super().__init__(name, age, profession, residence)
        self._salary = salary
    def get_salary(self):
        return self._salary
    def increase_salary(self, increase_amount):
        self._salary += increase_amount
    def introduce(self):
        super().introduce()
        print(f"Я зарабатываю {self._salary} рублей в месяц.")

employee1 = Employee("Алиса", 25, "Разработчик", "Екатеринбург", 75000)
employee1.introduce()
```
### Результат.
![image](https://github.com/lowfl3xx3r/main/blob/Tema8/pics/lab8_4.png)

## Самостоятельная работа №5
### Самостоятельно реализуйте полиморфизм.
Возьмем наши классы Person и Employee и добавим к ним метод work(), который будет представлять работу человека. 
В классе Person метод work() будет выводить общее сообщение о том, что человек работает, а в классе Employee мы переопределим этот метод, 
чтобы он выводил специфическое сообщение о том, что работник выполняет свои обязанности.
```python
class Person:
    def __init__(self, name, age, profession, residence):
        self._name = name
        self._age = age
        self._profession = profession
        self._residence = residence
    def introduce(self):
        print(f"Привет! Меня зовут {self._name}. Мне {self._age}. Моя профессия - {self._profession}. Я живу в городе {self._residence}")
    def work(self):
        print("Я занимаюсь обслуживанием сети.")
class Employee(Person):
    def __init__(self, name, age, profession, residence, salary):
        super().__init__(name, age, profession, residence)
        self._salary = salary
    def introduce(self):
        super().introduce()
        print(f"Я зарабатываю {self._salary} рублей в месяц.")
    def work(self):
        print(f"Я работаю как {self._profession} и зарабатываю {self._salary} рублей в месяц.")
person1 = Person("Виктор", 23, "Системный администратор", "Екатеринбург")
person1.introduce()
person1.work()  # Метод work вызывает общее поведение для класса Person

employee1 = Employee("Алиса", 25, "Разработчик", "Екатеринбург", 75000)
employee1.introduce()
employee1.work()
```
### Результат.
![image](https://github.com/lowfl3xx3r/main/blob/Tema8/pics/lab8_5.png)
