# Тема 7. Работа с файлами (Ввод, вывод)
Отчет по Теме #7 выполнил(а):
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
### Найдите в интернете любую статью (объем статьи не менее 200
слов), скопируйте ее содержимое в файл и напишите программу,
которая считает количество слов в текстовом файле и определит
самое часто встречающееся слово. Результатом выполнения задачи
будет: скриншот файла со статьей, листинг кода, и вывод в консоль,
в котором будет указана вся необходимая информация.

```python
def count_words(file_path):
    word_count = {}
    total_words = 0
    with open(file_path, 'r', encoding='utf-8') as file:
        for line in file:
            words = line.split()
            for word in words:
                word = word.strip('.,!?;:"()\'')
                if word:
                    total_words += 1
                    if word in word_count:
                        word_count[word] += 1
                    else:
                        word_count[word] = 1

    return total_words, word_count
def main():
    file_path = 'article.txt'
    total_words, word_count = count_words(file_path)
    print("Количество слов в тексте:", total_words)
    if word_count:
        most_common_word = max(word_count, key=word_count.get)
        print("Самое часто встречающееся слово:", most_common_word, "(встречается", word_count[most_common_word],
              "раз)")
    else:
        print("Текстовый файл пуст или не содержит слов.")
if __name__ == "__main__":
    main()
```
### Результат.
![image](https://github.com/lowfl3xx3r/main/blob/Tema7/pics/lab7_1.png)
![image](https://github.com/lowfl3xx3r/main/blob/Tema7/pics/lab7_1_1.png)

## Самостоятельная работа №2
### Присвоить значения трем переменным и вывести их в консоль, используя только две строки редактора кода

```python
a, b, c = 6, 9, 8
print(a, b, c)
```
### Результат.
![image](https://github.com/lowfl3xx3r/main/blob/Tema7/pics/lab7_2.png)

## Самостоятельная работа №3
### Имеется файл input.txt с текстом на латинице. Напишите программу,
которая выводит следующую статистику по тексту: количество букв
латинского алфавита; число слов; число строк.
• Текст в файле:
Beautiful is better than ugly.
Explicit is better than implicit.
Simple is better than complex.
Complex is better than complicated.
• Ожидаемый результат:
Input file contains:
108 letters
20 words
4 lines

```python
def count_statistics(file_path):
    letters_count = 0
    words_count = 0
    lines_count = 0
    with open(file_path, 'r') as file:
        for line in file:
            lines_count += 1
            line_without_dots = line.replace('.', '')
            words = line_without_dots.split()
            words_count += len(words)
            for word in words:
                letters_count += len(word)
    return letters_count, words_count, lines_count
def main():
    file_path = 'input.txt'  # Укажите путь к вашему файлу
    letters_count, words_count, lines_count = count_statistics(file_path)
    print("Input file contains:")
    print(f"{letters_count} letters")
    print(f"{words_count} words")
    print(f"{lines_count} lines")
if __name__ == "__main__":
    main()
```
### Результат.
![image](https://github.com/lowfl3xx3r/main/blob/Tema7/pics/lab7_3.png)

## Самостоятельная работа №4
### Напишите программу, которая получает на вход предложение,
выводит его в терминал, заменяя все запрещенные слова
звездочками * (количество звездочек равно количеству букв в
слове). Запрещенные слова, разделенные символом пробела,
хранятся в текстовом файле input.txt. Все слова в этом файле
записаны в нижнем регистре. Программа должна заменить
запрещенные слова, где бы они ни встречались, даже в середине
другого слова. Замена производится независимо от регистра: если
файл input.txt содержит запрещенное слово exam, то слова exam,
Exam, ExaM, EXAM и exAm должны быть заменены на ****.
• Запрещенные слова:
hello email python the exam wor is
• Предложение для проверки:
Hello, world! Python IS the programming language of thE future. My
EMAIL is....
PYTHON is awesome!!!!
• Ожидаемый результат:
*****, ***ld! ****** ** *** programming language of *** future. My
***** **....
****** ** awesome!!!!

```python
def censor_sentence(sentence, banned_words):
    censored_sentence = sentence.lower()
    for word in banned_words:
        censored_sentence = censored_sentence.replace(word, '*' * len(word))
    return censored_sentence
def main():
    with open('input.txt', 'r') as file:
        banned_words = file.read().split()
    sentence = input("Введите предложение: ")
    censored_sentence = censor_sentence(sentence, banned_words)
    print("Цензурированное предложение:")
    print(censored_sentence)
if __name__ == "__main__":
    main()
```
### Результат.
![image](https://github.com/lowfl3xx3r/main/blob/Tema7/pics/lab7_4.png)

## Самостоятельная работа №5
### Самостоятельно придумайте и решите задачу, которая будетвзаимодействовать с текстовым файлом
Задача подсчета частоты встречаемости каждого символа в текстовом файле. Программа будет считывать содержимое файла, а затем подсчитывать, сколько раз каждый символ встречается в тексте. 
Результаты будут выводиться в консоль.
За пример взят файл input.txt из 3 самостоятельной работы

```python
def count_characters(file_path):
    character_count = {}
    with open(file_path, 'r') as file:
        for line in file:
            for char in line:
                if char in character_count:
                    character_count[char] += 1
                else:
                    character_count[char] = 1
    return character_count
def main():
    file_path = 'input.txt'
    character_count = count_characters(file_path)
    print("Частота встречаемости символов в файле:")
    for char, count in character_count.items():
        print(f"{char}: {count}")
if __name__ == "__main__":
    main()
```
### Результат.
![image](https://github.com/lowfl3xx3r/main/blob/Tema7/pics/lab7_5.png)
