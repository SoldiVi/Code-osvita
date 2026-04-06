+++
title = 'Лекція 7: Використання ітераційних циклів в Python'
+++

## План

1. [Цикл `for`](#цикл-for)
   - 1.1 Синтаксис циклу `for`
   - 1.2 Функція `range()`
   - 1.3 Цикл `for` і послідовності
   - 1.4 Функція `enumerate()`
   - 1.5 Функція `zip()`

---

## 1. Цикл `for`

### 1.1 Синтаксис циклу `for`

Цикл `while` продовжує виконуватися доти, доки умова залишається істинною. Якщо необхідно виконати блок коду лише визначену (відому) кількість разів, то використовують цикл `for` і функцію `range()`. Синтаксис:

```python
for змінна in range():
    блок коду
```

В Python команда `for` завжди складається з таких елементів:

- ключове слово `for`
- ім'я змінної
- ключове слово `in`
- виклик функції `range()`, в яку можна передати до трьох цілих чисел, розділених комами
- двокрапка
- блок коду з відступом, що починається на наступному рядку

Приклад:

```python
print('My name is')
for i in range(5):
    print('Anakin Skywalker (' + str(i) + ')')
```

Блок коду циклу `for` виконується 5 разів. На першій ітерації значення змінної `i` встановлюється рівним `0`. Виклик функції `range(5)` забезпечує п'ятикратне виконання блоку коду циклу, встановлюючи для `i` послідовно значення `0, 1, 2, 3` і `4`. Ціле значення `5` у цей ряд не входить.

Результат:

```
My name is
Anakin Skywalker (0)
Anakin Skywalker (1)
Anakin Skywalker (2)
Anakin Skywalker (3)
Anakin Skywalker (4)
```

Команди `break` і `continue` використовуються у циклі `for` по аналогії, як і у випадку з циклом `while`.

Усе те, що робить цикл `for`, можна зробити і за допомогою циклу `while`:

```python
print('My name is')
i = 0
while i < 5:
    print('Anakin Skywalker (' + str(i) + ')')
    i = i + 1  # i += 1
```

---

### 1.2 Функція `range()`

У функцію `range()` можна передавати аргументи — значення трьох цілих чисел, розділених комами.

**Два аргументи** — початок і кінець діапазону (кінець не входить):

```python
for i in range(12, 16):
    print(i)
```

Результат:

```
12
13
14
15
```

**Три аргументи** — початок, кінець і крок зміни:

```python
for i in range(1, 10, 2):
    print(i)
```

Результат:

```
1
3
5
7
9
```

**Від'ємний крок** — значення змінюється від більших до менших:

```python
for i in range(3, -4, -1):
    print(i)
```

Результат:

```
3
2
1
0
-1
-2
-3
```

---

### 1.3 Цикл `for` і послідовності

Цикл `for` дозволяє проходити по різним структурам даних, які є послідовностями.

**Прохід по списку:**

```python
birds = ['pigeon', 'crow', 'owl', 'eagle']
for bird in birds:
    print(bird)
```

Результат:

```
pigeon
crow
owl
eagle
```

Списки, рядки, кортежі та словники є прикладами ітеративних об'єктів у Python. Ітерація по рядку повертає один символ за раз:

```python
word = 'crab'
for letter in word:
    print(letter)
```

Результат:

```
c
r
a
b
```

**Ітерація по ключах словника** (або з використанням `keys()`):

```python
professions = {'business': 'economist', 'tv': 'newsreader', 'it': 'web developer', 'education': 'teacher'}
for key in professions:  # або: for key in professions.keys()
    print(key)
```

Результат:

```
business
education
tv
it
```

**Ітерація по значеннях словника** за допомогою `values()`:

```python
professions = {'business': 'economist', 'tv': 'newsreader', 'it': 'web developer', 'education': 'teacher'}
for value in professions.values():
    print(value)
```

Результат:

```
teacher
newsreader
web developer
economist
```

**Ітерація по парах ключ-значення** за допомогою `items()`:

```python
professions = {'business': 'economist', 'tv': 'newsreader', 'it': 'web developer', 'education': 'teacher'}
for item in professions.items():
    print(item)
```

Результат:

```
('business', 'economist')
('education', 'teacher')
('it', 'web developer')
('tv', 'newsreader')
```

Значення елементів кортежу можна отримати окремо на кожній ітерації:

```python
professions = {'business': 'economist', 'tv': 'newsreader', 'it': 'web developer', 'education': 'teacher'}
for key, value in professions.items():
    print('Category', key, 'has a profession', value)
```

Результат:

```
Category business has a profession economist
Category education has a profession teacher
Category it has a profession web developer
Category tv has a profession newsreader
```

Для отримання елементів словника у певному порядку можна скористатися функцією `sorted()`:

```python
favorite_languages = {'john': 'Python', 'catherine': 'C', 'mary': 'Ruby', 'alex': 'Python'}
for name in sorted(favorite_languages.keys()):
    print(name.title() + ", thank you for taking the poll.")
```

Результат:

```
Alex, thank you for taking the poll.
Catherine, thank you for taking the poll.
John, thank you for taking the poll.
Mary, thank you for taking the poll.
```

---

### 1.4 Функція `enumerate()`

Один з варіантів отримання індексів під час перебору — використання `range()` і `len()`:

```python
popular_sites = ['Google.com', 'Youtube.com', 'Facebook.com', 'Baidu.com', 'Wikipedia.org', 'Yahoo.com', 'Amazon.com']
for index in range(len(popular_sites)):
    print(index, popular_sites[index])
```

Результат:

```
0 Google.com
1 Youtube.com
2 Facebook.com
3 Baidu.com
4 Wikipedia.org
5 Yahoo.com
6 Amazon.com
```

Проте Python надає вбудовану функцію `enumerate()`, яка робить комбінацію `range()` і `len()` зайвою. Функція `enumerate()` повертає кортеж `(індекс, елемент)` для кожного елемента послідовності:

```python
popular_sites = ['Google.com', 'Youtube.com', 'Facebook.com', 'Baidu.com', 'Wikipedia.org', 'Yahoo.com', 'Amazon.com']
for index, value in enumerate(popular_sites, 1):
    print(index, value)
```

Необов'язковий аргумент `1` вказує, з якого числа починати нумерацію (за замовчуванням — з `0`):

```
1 Google.com
2 Youtube.com
3 Facebook.com
4 Baidu.com
5 Wikipedia.org
6 Yahoo.com
7 Amazon.com
```

---

### 1.5 Функція `zip()`

Функція `zip()` використовується для паралельної ітерації по декількох послідовностях одночасно:

```python
days = ['Monday', 'Tuesday', 'Wednesday']
fruits = ['coconut', 'lemon', 'mango']
drinks = ['coffee', 'tea', 'fruit juice']
desserts = ['marmalade', 'ice cream', 'pie', 'pudding']

for day, fruit, drink, dessert in zip(days, fruits, drinks, desserts):
    print(day, ': drink', drink, 'eat', fruit, 'enjoy', dessert)
```

Результат:

```
Monday : drink coffee eat coconut enjoy marmalade
Tuesday : drink tea eat lemon enjoy ice cream
Wednesday : drink fruit juice eat mango enjoy pie
```

> Функція `zip()` припиняє роботу при досягненні кінця **найкоротшої** послідовності. Список `desserts` виявився довшим за інші, тому `pudding` не потрапив у результат.

Функцію `zip()` можна використати для створення кортежів із елементів з однаковими індексами:

```python
english = 'Monday', 'Tuesday', 'Wednesday'
french = 'Lundi', 'Mardi', 'Mercredi'

print(list(zip(english, french)))
```

Результат:

```
[('Monday', 'Lundi'), ('Tuesday', 'Mardi'), ('Wednesday', 'Mercredi')]
```

Передавши результат `zip()` у функцію `dict()`, отримаємо словник:

```python
print(dict(zip(english, french)))
```

Результат:

```
{'Wednesday': 'Mercredi', 'Monday': 'Lundi', 'Tuesday': 'Mardi'}
```
