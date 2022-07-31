## Конспект по программированию и computer science, различные общие темы


**Первые 4 лекции, из курса [2021 Анализ данных на Python](https://www.youtube.com/playlist?list=PLRDzFCPr95fIgPrFFW-0nXT5YH6ZnjRM6) от старшего преподавателя кафедры информатики и вычислительной математики МФТИ [Тимофея Хирьянова](https://www.youtube.com/channel/UCQfwKTJdCmiA6cXAY0PNRJw)**

- Материалы курса находятся на [github](https://github.com/tkhirianov/pydatan)

- [Telegram-канал для общения по курсу](https://t.me/tkhirianov_data_analysis_with_py)

- https://www.python.org/

- https://pythonworld.ru/

### <a id="contents" />Оглавление

- [Лекция №1. SOLID-принципы. Введение в ООП на Python.](#lection1)
- [Лекция №2. Функциональное программирование на Python, итераторы, генераторы, редуктор, map(), лямбда-функции, цикл for, range, list comprehension.](#lection2)
- [Лекция №3. Параллельное программирование на Python. Многопоточность, асинхронность, Thread, Очередь/Queue, GIL.](#lection3)
- [Лекция №4. Скорость вычислений на Python.  Мультипроцессность/ multiprocessing, родительский процесс, дочерний процесс, очередь/queue.](#lection4)

---
[К оглавлению](#contents)
###  <a id="lection1" /> Лекция №1. SOLID-принципы. Введение в ООП на Python

***В Python все объект!!!***. 

Три кита ООП из 80-х: инкапсуляция, полиморфизм, наследование.

### Парадигма ООП
- Данные структурируются в виде объектов, каждый из которых имеет определенный ***тип***, то есть принадлежит к какому-либо ***классу***.
- ***Классы*** – результат формализации решаемой задачи, выделения главных ее аспектов. ***Класс*** - это абстракция над объектом. А объекты это его конкретные экземпляры, представители.
- Внутри объекта ***инкапсулируется*** логика работы с относящейся к нему информацией. ***Инкапсуляция*** - это некая степень защиты от внешних воздействий, как в "капсулу помещается" для сохранности.
- Объекты в программе взаимодействуют друг с другом, обмениваются запросами и ответами.
- При этом объекты одного типа сходным образом отвечают на одни и те же запросы.
- Объекты могут организовываться в более сложные структуры, например, включать другие объекты или ***наследовать*** от одного или нескольких объектов. ***Наследование*** - подразумевает, что объект является как бы неким частным случаем другого объекта. 

### SOLID-принципы

Современная основа ООП. Как нам разбить программу на понятные людям сущности.  НО это не абсолютная истина, не стоит закосневать в них, и очень глубоко погружаться, везде есть исключения и компромисы.

- ***S*** Принцип единственной ответственности (single responsibility principle) Для каждого класса должно быть определено единственное назначение. У нас не должен возникать "божественный" объект который занимается всем. Каждый созданный объект должен решает одну конкретную задачу. Не стоит забывать о декомпозиции (разделение объектов) и выделении отдельных объектов.

- ***O*** Принцип открытости/закрытости (open–closed principle) «программные сущности ... должны быть открыты для расширения, но закрыты для модификации». Обратная совместимость, аналогия с машиной, можем улучшать от модели к модели, НО не меняя публичные интерфейсы (педали, руль и тп), т.е тот кто водил старую машину, сможет ездить и на новой. Скрытые штуки "под капотом" менять и модифицировать можно т.е это относится к реализации, НО это если сам интерфейс не меняется, т.е остается таким каким он был задуман и спроектирован изначально.

- ***L*** Принцип подстановки Лисков (Liskov substitution principle) «объекты в программе должны быть заменяемыми на экземпляры их подтипов без изменения правильности выполнения программы». Данный принцип про "правильное наследование", так как порой высокая иерархия наследования может быть вредна. У каждого объекта есть тип, т.е класс, и сами классы выстраиваются в иерархию классов и могут наследовать функциональность своих предков. Аналогия: сын электрика должен выполнять всю ту же работу что и сам отец по функционалу, и не требовать взятку, т.е работать за ту же плату. Подтип (сын электрика) заданного типа, должен делать всю старую функциональность как и сам старый тип (электрик), пользователь не должен замечать изменений. 

- ***I*** Принцип разделения интерфейса (interface segregation principle) «много интерфейсов, специально предназначенных для клиентов, лучше, чем один интерфейс общего назначения». Швейцарский нож - это зло. Здесь подразумевается универсальный метод который делает очень многое. Интерфейс - это способ (чаще всего это метод) повзаимодействовать с какой-либо программной сущностью. Лучше сделать несколько узкоспециализированных интерфейсов, чем один общего назначения. НО есть и другая сторона, если включить голову, то можно где-то и нарушить данный принцип. Пример: отдельный объект кофемолка, отдельный объект турка на огне., можно объединить их и получится единая сущность -> кофеварка, которая принимает кофейные зерна на вход, мелит их, и сразу же в себе самой, варит кофе.

- ***D*** Принцип инверсии зависимостей (dependency inversion principle) «Зависимость на Абстракциях. Нет зависимости на что-то конкретное». Пример с машинкой, если мы хотим повесить зависимость на человека, то он должен зависеть не от конкретного устройства автомобиля, а нужно выработать некий абстрактный интерфейс и зависеть от него. Сравнение электромобиля и обычного авто, интерфейс одинаковый, но реализация под капотом разная, но при взаимодействии пользователя с машиной, реализация не должна его волновать.  В Python для этого используются ***абстрактные классы***.

Во многом это и есть владение техникой ООП, а именно познать сущность, выделить сущность, дать имя сущности, по сути абстрагироваться от конкретики

***Объектно-ориентированное программирование (ООП)*** — парадигма программирования, в которой основными концепциями являются понятия объектов и классов.

***Класс***— тип, описывающий устройство объектов. 

***Объект*** — это экземпляр класса.

Простейший пример класса:
```python
class C: 
    pass

имя_объекта = имя_класса()
# когда мы как бы вызываем класс, то создается его экземпляр
```

```python
class Rectangle: 
    #статический атрибут
    default_color = "green"
    
    #конструктор
    def __init__(self, width, height):
        #динамические атрибуты
        self.width = width 
        self.height = height
```

Метод `__init__` называется конструктором. Собственно, конструктор зовется при выполнении конструкции вида `ИмяКласса()`. `__name__` это специальные ***магические методы*** из справочника языка

```python
__init__(self, ...) #  инициализатор класса.

__del__ # деструктор объекта.
def __del__(self): 
	self.file.close() 
	del self.file
```

***Абстрактным*** называется класс, который содержит один и более абстрактных методов. Абстрактным называется объявленный, но не реализованный ***метод***. Т.е он не реализован, у этого класса не бывает экземпляров. Данные классы нужны нам при проектировании 

```python
# для использования необходима библиотека
from abc import ABC, abstractmethod

class ChessPiece(ABC):
    # общий метод, который будут использовать все наследники этого класса
    def draw(self):
        print("Drew a chess piece")
        
    # абстрактный метод, который будет необходимо переопределять для каждого подкласса
    @abstractmethod 
    def passmove(self):
        pass
        
class Queen(ChessPiece):
    def move(self):
        print("Moved Queen to e2e4")
 
    # Мы можем создать экземпляр класса
q = Queen()
    # И нам доступны все методы класса
q.draw()
q.move()
```

### Декомпозиция программы на модули. Менеджер контеста.

Функции модулей:
- Повторное использование кода: такой код может быть загружен много раз во многих местах.

- Управление адресным пространством: модуль — это высокоуровневая организация программ, это пакет имен, который избавляет вас от конфликтов. Каждый объект «проживает» свой цикл внутри своего модуля, поэтому модуль — это средство для группировки системных компонентов.

- Глобализация сервисов и данных: для реализации объекта, который используется во многих местах, достаточно написать один модуль, который будет импортирован.

1. Модуль с именем `my_module` можно импортировать как `import my_module`. После этого мы получаем доступ ко всем функциям определённым в модуле: 
```python
my_module.func1()
my_module.func2()
f1 = my_module.func1
```

2. 
```python
# берем отдельный нужный нам функционал
from my_module import func1, func2 
func1()
```

3. 
```python
# берем все, высыпаем всю коробку с инструментами
from my_module import * 
func1()
```

Библиотек в языке огромное множество вот некоторые: [The Python Standard Library](https://docs.python.org/3/library/index.html)

---
[К оглавлению](#contents)
###  <a id="lection2" /> Лекция №2. Функциональное программирование на Python, итераторы, генераторы, редуктор, map(), лямбда-функции, цикл for, range, list comprehension

Разделение языков программирования: 
- императивные. Блок-схемы, ассемблер (чисто импераативный), машинные коды, в которых четко и строго определена последовательность действий. Пишем как император, т.е повелеваем и управляем. Команды, приказы - это стиль данного языка. Тьюринг полный язык (т.е на данном языке можно вычислить все что угодно)

- функциональные. Вычисляем функциями, здесь нам не нужно описывать и задавать строгую последовательность действий. В чистых функциональных языках НЕТ ПЕРЕМЕННЫХ, нет присваивания и изменяемых структур, циклов, нет массивов и списков, ЕСТЬ функции и константы. 
Python не является чисто функциональным языком. В чистом функциональном языке, циклы заменяются рекурсией. Тьюринг полный язык (т.е на данном языке можно вычислить все что угодно). Функции можно производить в процессе производства.

- логические (Prolog)

***Алгоритм*** - это вычислимая функция (так как можно вычислить на машине Тьюринга). Алгоритм - это последовательность команд означающих действия, на формальном языке исполнителя, идущая к цели за конечное время.

Рассматриваем функциональные:

```python
def foo(x):
    return x + 1
foo(1) # 2
y = foo(1)

def progression(start, stop, step):
    if start >= stop:
        return
    else:
        print(start)
        progression(start + step, stop, step)
        
progression(0, 10, 1)
```
Есть чистые функции - подразумевают вычисления. Можно закэшировать, т.е запомнить значение ее вычисления.. . А есть нечистые функции - подразумевают действия.

### Итерируемые объекты-последовательности

***Генератор*** - повышает размерность последовательности.

***Редуктор*** - понижает/сокращает размерность последовательности.

<img alt="image" src="images/Итерируемые объекты-последовательности.jpg"/>

Пример использования функционального стиля, здесь функция имеет побочный эффект (print) для наглядности процесса. ***Итерируемый объект*** - это тот который можно "доить", здесь мы видим отложенные вычисления.

```python
def f(x):
    print('calculating {x}*10')
    return x * 10
    
A = (1, 2, 3, 4, 5)
B = (f(x) for x in A)
type(B) # <class 'generator'>
for y in B:
    print(y)
```

```bash
calculating {x}*10
10
calculating {x}*10
20
calculating {x}*10
30
calculating {x}*10
40
calculating {x}*10
50
```

В функциональном программировании вычисления выполняются путем объединения функций, которые принимают аргументы и возвращают конкретное значение (или значения). Эти функции не изменяют свои входные аргументы и не изменяют состояние программы. Они просто предоставляют результат данного вычисления. Такие функции обычно называются чистыми функциями (pure functions).

### [Использование функции map в Python](https://www.digitalocean.com/community/tutorials/how-to-use-the-python-map-function-ru)

`map()` — это встроенная функция, которая позволяет обрабатывать и преобразовывать все элементы в итерируемом объекте без использования явного цикла `for`, методом, широко известным как сопоставление (mapping). `map()` полезен, когда вам нужно применить функцию преобразования к каждому элементу в коллекции или в массиве и преобразовать их в новый массив.

`map()` — один из инструментов, поддерживающих стиль функционального программирования в Python.

Встроенная в Python функция `map()` используется для применения функции к каждому элементу итерируемого объекта (например, списка или словаря) и возврата нового итератора для получения результатов. Функция `map()` возвращает объект `map` (итератор), который мы можем использовать в других частях нашей программы. Также мы можем передать объект `map` в функцию `list()` или другой тип последовательности для создания итерируемого объекта.

Функция `map()` имеет следующий синтаксис:

```python
map(function, iterable, [iterable 2, iterable 3, ...])
```

Вместо использования цикла `for` функция `map()` дает возможность применить функцию к каждому элементу итерируемого объекта. Это повышает производительность, поскольку функция применяется только к одному элементу за раз без создания копий элементов в другом итерируемом объекте. Это особенно полезно при обработке больших наборов данных. Также `map()` может принимать несколько итерируемых объектов в качестве аргументов функции, отправляя в функцию по одному элементу каждого итерируемого объекта за раз.

Мы можем передать объект функцию как параметра. Можно передавать последовательность функций, и в результате может появиться даже новая функция. Пока функция не запущена, ее можно передать в качестве параметра и тп. 

```python
def double_performer(f, x):
    return f(f(x))

def f(x): 
    return x*10
print(double_performer(f, 5)) # 500
```

Функции как аргументы:

```python
def double_performer(f, x):
    return f(f(x))

def f1(x): 
    return x*10

def f2(x): 
    return x * x
    
def f3(x): 
    return -x

for f in f1, f2, f3:
    y = double_performer(f, 5)
    print(y)
```

```bash
500
625
5
```

Пример с `map()`

```python
def f1(x): 
    return x*10

A = (1, 2, 3, 4, 5)
C = map(f1, A)
type(C) # <class 'map'>
print(C) # <map object at 0x7ff5ab4c6c18>
for y in C:
    print(y)
```

`range` - это не список, это некий объект, арифметическая прогрессия, и он вычисляет число ровно в тот момент когда мы просит его это сделать (всю последовательность он не хранит, т.к память бы не выдержала)

```python
A = range(1000000000000)
A[50000000] # 50000000
A[128976184345] # 128976184345
A = range(10)
B = (x for x in A if x % 2 == 0)
type(B) # <class 'generator'>

print(B) # <generator object <genexpr> at 0x7ff5ab4d2480>

print(*B) # 0 2 4 6 8

print(*(x * x for x in A if x % 2 == 1)) # 1 9 25 49 81
```

### Безымянные функции - это лямбда, о lambda-функциях [здесь](https://pythonru.com/osnovy/vse-chto-nuzhno-znat-o-lambda-funkcijah-v-python) и [здесь](https://habr.com/ru/company/piter/blog/674234/)

Лямбда-функции в Python являются анонимными. Это означает, что функция безымянна. Как известно, ключевое слов `def` используется в Python для определения обычной функции. В свою очередь, ключевое слово `lambda` используется для определения анонимной функции.

Обычно они нужны тогда, когда в языке возникает возможность передавать функцию в качестве параметра или возвращать в качестве значения.

```python
def defined_cube(y):
    return y*y*y

lambda_cube = lambda y: y*y*y

print(defined_cube(2)) # 8 
print(lambda_cube(2)) # 8 
```

Мы заменяем `def defined_cube(y): return y*y*y` на `lambda y: y*y*y` . После выполнения функция лямбда будет забыта и исчезнет. 

```python
A = range(10)
print(*map(lambda x: x*10 + x, A))
```

```bash
0 11 22 33 44 55 66 77 88 99
```

Язык мультипарадигменный. Парадигма - это подход к программированию. Например чистый Си не поддерживает парадигму функционального программирования, так как он чисто императивный.

Словарь - это хеш-таблица завернутая в Python в готовый красивый объект. Ключи (key) в словаре неизменяемы, и могут быть разными типами, главное чтобы были хешируемыми, а значения (value) можно менять. 

Конструктор как списка так и кортежа, ждет итерируемый объект на вход, и прекрасно с ним работает. 

### Использование zip 

***[Функция zip()](https://pythonru.com/uroki/funkcija-zip-dlja-nachinajushhih)***

Функция `zip()` в Python создает итератор, который объединяет элементы из нескольких источников данных. Эта функция работает со списками, кортежами, множествами и словарями для создания списков или кортежей, включающих все эти данные.

```python
A = (1, 2, 3, 4, 5)
B = tuple(x * 10 for x in A)
for a,b in zip(A,B):
    print(a,b, a + b)
```

```bash
1 10 11
2 20 22
3 30 33
4 40 44
5 50 55
```

```python
>>> s = 'abc'
>>> t = (10, 20, 30)

>>> zip(s,t)
[('a', 10), ('b', 20), ('c', 30)]
```

### Использование zip для создания словаря

У функции `zip()` множество сценариев применения. Например, она пригодится, если нужно создать набор словарей из двух массивов,

```python
d_keys = ['hostname', 'location', 'vendor', 'model', 'IOS', 'IP']
d_values = ['london_r1', '21 New Globe Walk', 'Cisco', '4451', '15.4', '10.255.0.1']

print(list(zip(d_keys, d_values)))
```

```bash
[('hostname', 'london_r1'),
 ('location', '21 New Globe Walk'),
 ('vendor', 'Cisco'),
 ('model', '4451'),
 ('IOS', '15.4'),
 ('IP', '10.255.0.1')]
```

```python
enumerate("HELLO") # enumerate object at 0x7ff5ab3d8c60>
for i, char in enumerate("HELLO"):
    print(i, char)
```

```bash
0 H
1 E
2 L
3 L
4 O
```

### List Comprehensions

```python
squares_2 = [i * i for i in range(10)]

for i in range(len(squares_2)):
    print(squares_2[i])
```

```bash
0
1
4
9
16
25
36
49
64
81
```

### Range and Arange
```python
r_1 = range(10)

for it in r_1:
    print(it, end = ", ")
    
from numpy import arange

print("Float range using NumPy arange():")

print("\nTest 1:")
for i in arange(0.0, 10.0, 0.5):
    print(i, end=', ')

print("\n\nTest 2:")
for i in arange(-1.0, 1.0, 0.5):
    print(i, end=', ') 
```

```bash
0, 1, 2, 3, 4, 5, 6, 7, 8, 9, Float range using NumPy arange():

Test 1:
0.0, 0.5, 1.0, 1.5, 2.0, 2.5, 3.0, 3.5, 4.0, 4.5, 5.0, 5.5, 6.0, 6.5, 7.0, 7.5, 8.0, 8.5, 9.0, 9.5, 

Test 2:
-1.0, -0.5, 0.0, 0.5, 
```

***Со-процессинг*** — это одновременное выполнение двух процедур, одна из которых считывает вывод другой.
***Сопроцессоры*** - тут повычисляли, и там повычисляли, тут, там и тп, т.е перебрасывание активности по сути. Параллейного программирования здесь нет. 

---
[К оглавлению](#contents)
###  <a id="lection3" /> Лекция №3. Параллельное программирование на Python. Многопоточность, асинхронность, Thread, Очередь/Queue, GIL

Последовательное программирование - где есть один лишь исполнитель, один актор.

***Актор*** - деятель, действователь. Некая вычислительная штука (процессор/ядро). Микроконтроллер без операционки, имеющий лишь наши вшитые команды, это пример последовательного программирования.

***Чередование (interleaving)*** - можно даже на одноядерном процессоре осуществить, это некое заданное чередование активности двух процессов, и планировщик задач дает активность то одному, то другому, чередуя их актвиности. Один спит, другой активничает, затем наоборот. Однако так процессы вычисления не ускорятся, а замедлятся, сам планировщик кушает память и время на принятие решения и переключение контекста. 

С помощью операционной системы (ядро) которое дает указание вычислительным процессам, когда стартовать, а когда ожидать, можно повысить эффективность. Также она может распределять роли вычислительных процессов на основе действий пользователя (условно когда он что-то нажимает, или дает указания к старту и тп). 

<img alt="image" src="images/Параллельное программирование1.jpg"/>

### Цели параллейного программирования:
- некая асинхронизация работы с отложенными задачами (по сети, с устройствами, ввод-вывод)
- интерактивность (чтобы наш
- увеличение скорости вычисления (решение: много ядер или много процессоров, бывают материнки с 2 процами, как пример сервера). Это система общей памяти.
- много вычислительный систем (компьютеров), т.е распределенная система. Это отдельные самостоятельные машины связанные между собой сетью. Бывают: ***гамогенные*** - это кластер или фабрика, или ***гетерогенные*** - это вычислительная сеть (арендовать мощность компьютера под свои нужды, есть такие сервисы). 

<img alt="image" src="images/Цели параллейного программирования.jpg"/>

### Схемы взаимодействия процессов

- общая память (shared memory). Ценность в том, что не требуется никаких существенных ресурсов на поддержание памяти, она естественна, как и в обычном компьютере. Из минусов может быть наслоение результата от 2 вычисляемых процессов и плавающая ошибка (гейзенбаг). Race condition - состояние гонки между этими вычислительными процессами, и так называемая критическая секция, где их результаты вычисления могут наложиться, и чтобы предотвратить ошибки ставят блокировки (проверка что критическая секция пустая, и можно производить вычисление, это делает и гарантирует операционка). Одно из решений это Взаимные исключения (mutual exclusion -> mutex) - нужны для защиты доступа к потенциально опасным местам. Если весь программный код это критическая секция, то тогда нет смысла в shared memory, в параллелизации. 
- очереди (queue). Отдельные вычислительные процессы, результаты вычислений кладут в очередь, и другой процесс их может брать, и т.д. Нет явных блокировок, так как при необходимости все выстроится в очередь

<img alt="image" src="images/Схемы взаимодействия процессов.jpg"/>

Нити исполнения - в параллейном исполнении внутри процесса (вызовы функций, результаты, ветки как в гите). У каждой нити свой стек, но у всех общая память (глобальные переменные, ссылки на другие нити), и планировщик переключающий контекст. 

<img alt="image" src="images/параллейность в вычислительном процессе1.jpg"/>

***GIL (Global Interpreter Lock)*** - глобальная блокировка интерпретатора. В языке есть сборщик мусора и он аккуратно следит за объектами, и когда на объект нет ссылок и он уже не нужен, сборщик его съедает, предотвращая утечку памяти (memory leak). Также этот механизм осуществляет контроль в ветках выполнения процесса, и там тоже они осуществляются через чередование, то одна, то системный вызов, то другая ветка, то снова вызов, и прошлая ветка и тп. 

Python Global Interpreter Lock (GIL) — это своеобразная блокировка, позволяющая только одному потоку управлять интерпретатором Python.

По мнению лектора Python не сильно заточен на параллейное программирование (хотя есть библиотечные решения), есть языки которые имеют большую ориентированность на него и в самом языке это больше встроено (С++, Go, Kotlin, Rust)

!!! Глобальные переменные это зло для параллейного программирования, это та самая скрытая критическая зона !!!

В Питоне есть отдельные библиотеки для нитей [_thread](https://docs.python.org/3/library/_thread.html) и [threading](https://docs.python.org/3/library/threading.html). Поток и процесс. Создание нитей (потоков) и процессов.

```python
import _thread
import time

# Define a function for the thread
def print_time(threadName, delay):
   count = 0
   while count < 5:
      time.sleep(delay)
      count += 1
      print("%s: %s" % (threadName, time.ctime(time.time())))

# Create two threads as follows
try:
   _thread.start_new_thread(print_time, ("Thread-1", 2,))
   _thread.start_new_thread(print_time, ("Thread-2", 4,))
except:
   print("Error: unable to start thread")

while 1:
   pass
```

```bash
Thread-1: Fri Jul 29 11:26:09 2022
Thread-2: Fri Jul 29 11:26:11 2022
Thread-1: Fri Jul 29 11:26:11 2022
Thread-1: Fri Jul 29 11:26:13 2022
Thread-2: Fri Jul 29 11:26:15 2022
Thread-1: Fri Jul 29 11:26:15 2022
Thread-1: Fri Jul 29 11:26:17 2022
Thread-2: Fri Jul 29 11:26:19 2022
Thread-2: Fri Jul 29 11:26:23 2022
Thread-2: Fri Jul 29 11:26:27 2022
```

---
[К оглавлению](#contents)
###  <a id="lection4" /> Лекция №4. Скорость вычислений на Python.  Мультипроцессность/ multiprocessing, родительский процесс, дочерний процесс, очередь/queue. 

Лекция носит практический характер, используются библиотеки для параллейности процессов и производится сравнение скорости вычислений. 

1) надо подумать что будем считать, и выбрать самый оптимальный и быстрый алгоритм
2) возможно применить параллейное программирование если оно возможно и уместно
3) или использовать связки с очень быстрыми языками (запуск Python, с алгоритмом на C и C++)
4) использовать динамическое программирование

Рассмотрим скорость на примере вычисления 40 первых чисел Фибоначчи. На Python в зависимости от реализации это ~30 секунд, на C++ это 1-2 секунды, методом динамического программирования на Python это 0.2 сек. Скорость зависит от метода реализации и алгоритма вычисления. 

Замеры лектора, на стареньком i5 2 ядра, 4 потока.

Один процесс на Python: 58.11 секунд

40 процессов - по одному на каждое число: 36.67 секунд

С очередями: 

4 процесса 34.94 секунд

2 процесса 37.40 секунд

Пул из 4 процессов: 34.87 секунд

На С++: 1.25 секунд

На питоне динамическим программированием: 0.3 секунд

С использованием JIT-компилятора Numba (последний пример кода ниже): 2.12 секунд

У меня относительно схожие результаты, но я тестил код в браузере (который конечно замедляет относительно консоли) в https://replit.com/ и https://www.onlinegdb.com/online_python_compiler 

***Метод динамического программирования***
```python
final_fibonacci_number = 40
fib = [0, 1] + [None]*(final_fibonacci_number - 1)
for i in range(2, final_fibonacci_number + 1):
    fib[i] = fib[i-1] + fib[i-2]
for i in range(0, final_fibonacci_number + 1):
    print(fib[i])
```

```bash
0
1
1
2
3
5
8
13
21
34
55
89
144
233
377
610
987
1597
2584
4181
6765
10946
17711
28657
46368
75025
121393
196418
317811
514229
832040
1346269
2178309
3524578
5702887
9227465
14930352
24157817
39088169
63245986
102334155
```

---

Никаких параллельных вычислений
```python
import time

final_fibonacci_number = 40
def fib(n: int) -> int:
    return fib(n-1) + fib(n-2) if n > 2 else 1
    
def main():
    tasks = list(range(0, final_fibonacci_number + 1))
    start_time = time.perf_counter()
    # Никаких параллельных вычислений! Работаем сами:
    answers = []
    for number in tasks:
        answers.append(fib(number))
    # Работает один родительский процесс по-прежнему.
    finish_time = time.perf_counter()
    print("Duration:", finish_time - start_time)
    
    print(*answers)
    
if __name__ == '__main__':
    main()
```

```bash
Duration: 54.08748500799993
1 1 1 2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597 2584 4181 6765 10946 17711 28657 46368 75025 121393 196418 317811 514229 832040 1346269 2178309 3524578 5702887 9227465 14930352 24157817 39088169 63245986 102334155
```

---

С процессами
```python
from multiprocessing import Process, Queue
import os
import time

final_fibonacci_number = 40

def worker(task: int, process_index: int):
    def fib(n: int) -> int:
        return fib(n-1) + fib(n-2) if n > 2 else 1
    
    number = task
    answer = fib(number)
    print(f"worker {process_index}, PID={os.getpid()}: fib({number}) = {answer}")
    
def main():
    tasks = []
    for n in range(0, final_fibonacci_number + 1):
        tasks.append(n)

    workers = []
    for process_index in range(final_fibonacci_number + 1):
        worker_process = Process(target=worker, args=(tasks[process_index],
                                                      process_index,))
        workers.append(worker_process)
    print("Parent process prepared all the tasks.")

    start_time = time.perf_counter()
    for worker_process in workers:
        worker_process.start()
    print("Parent process started workers processes.")

    for worker_process in workers:
        worker_process.join()
    finish_time = time.perf_counter()
    print("Parent process joined all the workers processes. Duration:",
          finish_time - start_time)
    
if __name__ == '__main__':
    main()
```

```bash
Parent process prepared all the tasks.
worker 1, PID=1699: fib(1) = 1
worker 0, PID=1698: fib(0) = 1
worker 3, PID=1701: fib(3) = 2
worker 2, PID=1700: fib(2) = 1
worker 4, PID=1702: fib(4) = 3
worker 6, PID=1704: fib(6) = 8
worker 5, PID=1703: fib(5) = 5
worker 7, PID=1705: fib(7) = 13
worker 9, PID=1707: fib(9) = 34
worker 8, PID=1706: fib(8) = 21
worker 12, PID=1710: fib(12) = 144
worker 11, PID=1709: fib(11) = 89
worker 13, PID=1711: fib(13) = 233
worker 10, PID=1708: fib(10) = 55
worker 14, PID=1712: fib(14) = 377
worker 16, PID=1714: fib(16) = 987
worker 15, PID=1713: fib(15) = 610
worker 19, PID=1717: fib(19) = 4181
worker 20, PID=1718: fib(20) = 6765
worker 17, PID=1715: fib(17) = 1597
worker 22, PID=1720: fib(22) = 17711
worker 23, PID=1721: fib(23) = 28657
worker 18, PID=1716: fib(18) = 2584
worker 21, PID=1719: fib(21) = 10946
worker 24, PID=1722: fib(24) = 46368
Parent process started workers processes.
worker 25, PID=1723: fib(25) = 75025
worker 27, PID=1725: fib(27) = 196418
worker 26, PID=1724: fib(26) = 121393
worker 28, PID=1726: fib(28) = 317811
worker 29, PID=1727: fib(29) = 514229
worker 30, PID=1728: fib(30) = 832040
worker 31, PID=1729: fib(31) = 1346269
worker 32, PID=1730: fib(32) = 2178309
worker 33, PID=1731: fib(33) = 3524578
worker 34, PID=1732: fib(34) = 5702887
worker 35, PID=1733: fib(35) = 9227465
worker 36, PID=1734: fib(36) = 14930352
worker 37, PID=1735: fib(37) = 24157817
worker 38, PID=1736: fib(38) = 39088169
worker 39, PID=1737: fib(39) = 63245986
worker 40, PID=1738: fib(40) = 102334155
Parent process joined all the workers processes. Duration: 64.41719395000018
```

---

Очереди
```python
from multiprocessing import Process, Queue
import os
import time

workers_number = 2
final_fibonacci_number = 40

def worker(tasks: Queue, answers: Queue, process_index: int):
    def fib(n: int) -> int:
        return fib(n-1) + fib(n-2) if n > 2 else 1
    
    while not tasks.empty():  # пока очередь не пуста выполняем одну очередную задачу
        number = tasks.get()
        answer = fib(number)
        answers.put((process_index, os.getpid(), number, answer,))
        #print(f"worker {process_index}, PID={os.getpid()}: fib({number}) = {answer}")
    
def main():
    tasks = Queue()
    answers = Queue()
    for n in range(1, final_fibonacci_number + 1):
        tasks.put(n)

    workers = []
    for process_index in range(workers_number):
        worker_process = Process(target = worker,
                                 args = (tasks, answers, process_index,))
        workers.append(worker_process)
    print("Parent process queued all the tasks.")

    start_time = time.perf_counter()
    for worker_process in workers:
        worker_process.start()
    print("Parent process started workers processes.")

    for worker_process in workers:
        worker_process.join()
    # Всё, тут мы вышли из режима многозадачности. Работает один родительский процесс.
    finish_time = time.perf_counter()
    print("Parent process joined all the workers processes. Duration:",
          finish_time - start_time)

    # Отладочная распечатка результатов
    ordered_answers = []
    while not answers.empty():
        process_index, PID, number, answer = answers.get()
        ordered_answers.append((number, answer,))
        print(f"worker {process_index}, PID={PID}: fib({number}) = {answer}")

    # Красивая распечатка полученных результатов:
    ordered_answers.sort()
    print(*(answer for number, answer in ordered_answers))
    
if __name__ == '__main__':
    main()
```

```bash
Parent process queued all the tasks.
Parent process started workers processes.
Parent process joined all the workers processes. Duration: 50.01943492200007
worker 0, PID=1467: fib(1) = 1
worker 0, PID=1467: fib(2) = 1
worker 0, PID=1467: fib(3) = 2
worker 0, PID=1467: fib(4) = 3
worker 0, PID=1467: fib(5) = 5
worker 0, PID=1467: fib(6) = 8
worker 0, PID=1467: fib(7) = 13
worker 0, PID=1467: fib(8) = 21
worker 0, PID=1467: fib(9) = 34
worker 0, PID=1467: fib(10) = 55
worker 0, PID=1467: fib(11) = 89
worker 0, PID=1467: fib(12) = 144
worker 0, PID=1467: fib(13) = 233
worker 0, PID=1467: fib(14) = 377
worker 0, PID=1467: fib(16) = 987
worker 0, PID=1467: fib(17) = 1597
worker 0, PID=1467: fib(18) = 2584
worker 0, PID=1467: fib(19) = 4181
worker 1, PID=1468: fib(15) = 610
worker 1, PID=1468: fib(20) = 6765
worker 0, PID=1467: fib(22) = 17711
worker 1, PID=1468: fib(21) = 10946
worker 1, PID=1468: fib(23) = 28657
worker 0, PID=1467: fib(24) = 46368
worker 1, PID=1468: fib(25) = 75025
worker 0, PID=1467: fib(26) = 121393
worker 1, PID=1468: fib(27) = 196418
worker 0, PID=1467: fib(28) = 317811
worker 1, PID=1468: fib(29) = 514229
worker 0, PID=1467: fib(30) = 832040
worker 1, PID=1468: fib(31) = 1346269
worker 0, PID=1467: fib(32) = 2178309
worker 1, PID=1468: fib(33) = 3524578
worker 0, PID=1467: fib(34) = 5702887
worker 1, PID=1468: fib(35) = 9227465
worker 0, PID=1467: fib(36) = 14930352
worker 1, PID=1468: fib(37) = 24157817
worker 0, PID=1467: fib(38) = 39088169
worker 1, PID=1468: fib(39) = 63245986
worker 0, PID=1467: fib(40) = 102334155
1 1 2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597 2584 4181 6765 10946 17711 28657 46368 75025 121393 196418 317811 514229 832040 1346269 2178309 3524578 5702887 9227465 14930352 24157817 39088169 63245986 102334155
```

---

Параллейные вычисления, используем Pool. Откажемся от явного использования Process, да и от Queue тоже, в пользу Pool.
```python
from multiprocessing import Pool
import os
import time

workers_number = 4
final_fibonacci_number = 40

def fib(n: int) -> int:
    return fib(n-1) + fib(n-2) if n > 2 else 1 

def main():
    tasks = list(range(1, final_fibonacci_number + 1))
    start_time = time.perf_counter()
    # Уход в паралельные вычисления:
    with Pool(workers_number) as pool_of_processes:
        answers = list(pool_of_processes.map(fib, tasks))
    # Всё, тут мы вышли из режима многозадачности. Работает один родительский процесс.
    finish_time = time.perf_counter()
    print("Duration:", finish_time - start_time)
    
    print(*answers)
    
if __name__ == '__main__':
    main()
```

```bash
Duration: 31.977911179999865
1 1 1 2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597 2584 4181 6765 10946 17711 28657 46368 75025 121393 196418 317811 514229 832040 1346269 2178309 3524578 5702887 9227465 14930352 24157817 39088169 63245986
```

---
C++
```C++
#include <iostream>
#include <vector>
using namespace std;

int64_t final_fibonacci_number = 40;

int64_t fib(int64_t number)
{
    return (number > 2)? fib(number - 1) + fib(number - 2) : 1;
}

int main()
{
    vector<int64_t> tasks;
    for(int i = 0; i < final_fibonacci_number + 1; i++)
        tasks.push_back(i);
    vector<int64_t> answers;
    for(int i = 0; i < final_fibonacci_number + 1; i++)
        answers.push_back(fib(tasks[i]));
    for(auto answer: answers) {
        cout << answer << ' ';
    }
    cout << endl;

    return 0;
}
```

~ 0.2 сек
```bash
1 1 1 2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597 2584 4181 6765 10946 17711 28657 46368 75025 121393 196418 317811 514229 832040 1346269 2178309 3524578 5702887 9227465 14930352 24157817 39088169 63245986 102334155
```

---
С использованием JIT-компилятора Numba

```python
from numba import jit
import time

final_fibonacci_number = 40

@jit(nopython=True)
def fib(n: int) -> int:
    return fib(n-1) + fib(n-2) if n > 2 else 1
    

def main():
    tasks = list(range(0, final_fibonacci_number + 1))
    start_time = time.perf_counter()
    # Никаких параллельных вычислений! Работаем сами:
    answers = []
    for number in tasks:
        answers.append(fib(number))
    # Работает один родительский процесс по-прежнему.
    finish_time = time.perf_counter()
    print("Duration:", finish_time - start_time)
    
    print(*answers)
    
if __name__ == '__main__':
    main()
```

```bash
Duration: 13.37228933199367
1 1 1 2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597 2584 4181 6765 10946 17711 28657 46368 75025 121393 196418 317811 514229 832040 1346269 2178309 3524578 5702887 9227465 14930352 24157817 39088169 63245986 102334155
```

Лекция №5. Командная строка GNU/Linux. Команды оболочки bash, файлы, написание скриптов с потоками ввода и вывода. 

Асинхронность в работе, предназначена для того чтобы, отправив системный вызов, не дожидаться его окончания, а продолжить вычислительный процесс дальше. 

В GNU/Linux все - файл

Данная лекция носила сугубо практический характер, ничего нового для себя не нашел, много о командной оболочке bash и zsh, у меня есть в другом конспекте [The Command Line and Terminal](https://github.com/artemiosdev/Command-Line-Bash-Zsh)


---
[К оглавлению](#contents)