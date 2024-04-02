# Тема 9. Концепции и принципы ООП
Отчет по Теме #9 выполнил(а):
- Катаев Виктор Алексеевич
- ИНО ЗБ ПОАС-22-1

| Задание | Сам_раб |
| ------ | ------ |
| Задание 1 | + |

знак "+" - задание выполнено; знак "-" - задание не выполнено;

Работу проверили:
- к.э.н., доцент Панов М.А.

## Самостоятельная работа №1
### Задание садовник и помидоры

```python
import random

# Определяем класс помидора
class Tomato:
    # Словарь стадий созревания помидора
    states = {0: 'отсутствует', 1: 'цветение', 2: 'зеленый', 3: 'красный'}

    # Метод инициализации объекта помидора
    def __init__(self, index):
        self._index = index
        self._state = random.randint(0, 3)  # Рандомная начальная стадия созревания

    # Метод роста помидора
    def grow(self):
        if self._state < len(self.states) - 1:
            self._state += 1

    # Метод проверки созрел ли помидор
    def is_ripe(self):
        return self._state == 3

    # Метод получения текущего состояния помидора
    def get_state(self):
        return self.states[self._state]

# Определяем класс куста помидоров
class TomatoBush:
    # Метод инициализации объекта куста помидоров
    def __init__(self, num_tomatoes):
        self.tomatoes = [Tomato(index) for index in range(1, num_tomatoes + 1)]

    # Метод для просмотра роста всех помидоров на кусте
    def grow_all(self):
        for tomato in self.tomatoes:
            tomato.grow()

    # Метод для проверки, все ли помидоры на кусте созрели
    def all_are_ripe(self):
        return all([tomato.is_ripe() for tomato in self.tomatoes])

    # Метод для сбора урожая (очистки списка помидоров)
    def give_away_all(self):
        self.tomatoes = []

    # Метод для получения информации о сборе урожая
    def get_harvest_info(self):
        # Получаем количество и виды помидоров на кусте
        tomato_states = [tomato.get_state() for tomato in self.tomatoes]
        tomato_counts = {state: tomato_states.count(state) for state in set(tomato_states)}

        # Формируем строку с информацией о сборе урожая
        info = ", ".join([f"{count} {state} помидоров" for state, count in tomato_counts.items()])
        return info

# Определяем класс садовода
class Gardener:
    # Метод инициализации объекта садовода
    def __init__(self, name, plant):
        self.name = name
        self._plant = plant

    # Метод для работы с кустом (процесс ухода за кустом)
    def work(self):
        self._plant.grow_all()

    # Метод для сбора урожая
    def harvest(self):
        ripe_flag = False
        while not ripe_flag:
            if self._plant.all_are_ripe():
                ripe_flag = True
            else:
                # Если не все помидоры красные, продолжаем работу с кустом
                print("Не все помидоры красные, происходит работа по уходу за ними...")
                self.work()
                # Выводим состояние куста после ухода за ним
                print("Состояние куста после ухода за ним:", [tomato.get_state() for tomato in self._plant.tomatoes])

        # Сбор урожая после того, как все помидоры стали красными
        harvest_info = self._plant.get_harvest_info()
        print(f"{self.name} собрал урожай из {harvest_info}")
        self._plant.give_away_all()

    # Статический метод для вывода справки по садоводству
    @staticmethod
    def knowledge_base():
        print("Справка по садоводству:\n...")

# Вызываем справку по садоводству
Gardener.knowledge_base()

# Создаем куст помидоров и садовника
bush = TomatoBush(5)
gardener = Gardener("Виктор", bush)

# Выводим состояние куста до ухода за ним
print("Состояние куста до ухода за ним:", [tomato.get_state() for tomato in bush.tomatoes])

# Собираем урожай
gardener.harvest()
```
### Результат.
![image](https://github.com/lowfl3xx3r/main/blob/Tema9/pics/lab9.png)
