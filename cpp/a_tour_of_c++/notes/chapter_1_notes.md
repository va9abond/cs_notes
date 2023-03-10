
# 1 Basics
## 1.2 Programms

- С++ компилируемый язык, т.е. для работы программы исходный код должен быть скомпилирован - переработан в `объектный файл`.
  
  ![[cpp_build.png]]
  
- Выполняемая программа создается под конкретную комбинацию железа и ОС, поэтому один и тот же выполнисый файл нельзя запустить на MacOS и Windows 
- Стандарт ISO C++ определяет два вида сущностей 
	- **Фундаментальные возможности языка** - встроенные типы (*например*, `int`, `char`) или циклы (*например*, `for`, `while`)
	- **Компоненты стандартных библиотек** - контейнеры `vector`, `map` или операции ввода-вывода (*например*, `<<` или `getline()` ). Стандатная библиотека реализуется на самом языке C++ с небольшими вставками машинного кода 
- C++ - **статически типизированный язык**, т.е. тип каждой сущности должен быть известен компилятору в точке использования, т.к. тип объекта определяет набор применимых к нему операций

___
## 1.3 Functions

- Функция не может быть вызвана, если она не объявлена ранее
- **Объявление функции** назначает для нее:
	- тип возвращаемого значения
	- имя
	- количество и типы аргументов
- **Семантика передачи** аргументов в функцию идентична **сементике инициализации**: 
	1. выполняется проверка типов аргументов
	   - при необходимости происходит неявное преобразование типов аргументов 
- **Тип фукнции** включает в себя тип возвращаемого значения и последовательность типов аргументов. Если функция является членом класса (или пространства имен), то имя ее класса тоже включается в тип функции 
  ```cpp
  double get (const std::vector<double> &vector, int index) {} 
  // Тогда тип функции: `double(const std::vector<double>&, int)`
  ```
  
  ```cpp
  char& String::operator[] (int index) {}
  // Тип функции: char& String::(int)
  ```

- Если могут быть вызваны две алтернативные функции одновременно, то вызов любой из них будет считаться неоднозначным, компилятор выдаст ошибку:
  ```cpp
  void print (int, double);
  void print (double, int);
  void user2() {
	  print(0,0); // Ошибка компилятора: UB  
  }
  ```

- При перегрузке функции каждая функция с одним и тем же именем должна реализовывать одну и ту же семантику, т.е. в независимости от аргументов она должна делать примерно одно и тоже(*например*, функции `print()` в зависимости от аргументов будут выводить в консоль разные значения, но тем не менее задача функции остается прежней - вывод информации в консоль)

___
## 1.4 Types, variables and arithmetic 

- Каждое имя или выражение должно иметь тип, который определяет, какие операции могут быть над ними выполнены
- **Объявление** - инструкция, которая вводит объявляемую сущность в программу, оно определяет *тип* этой сущности:
	- **Тип** определяет *множество возможных значений* и *множество операций* для сущности
	- **Объект** - место в памяти, в котором хранится значение некоторого типа 
	- **Значение** - *множество битов*, интерпретируемых в соответствии с типом 
	- **Переменная** - именованный объект
- Каждый фундаментальный тип соответствует аппаратным возможностям и имеет фиксированный размер
	- **Размер типа** - определяет диапазон значений, которые могут храниться в объекте этого типа
```note
1. Размер типа зависит от реализации, т.е. он может меняться от машины r  машине
2. Размер типа на данной машине может быть получен с помощью оператора `sizeof()`
```

- [sizeof()](https://en.cppreference.com/w/cpp/language/sizeof)

- Целочисленные литералы по умолчанию - десятичные(*например,* 42)
	- **0b** - двоичный целочесленный литерал(*например,* 0b10101010)
	- **0x** - целочисленный литерал по основанию 16(*например,* 0xBAD1234)
	- 0  - целочисленный литерал по основанию 8(*например,* 0334)
- Для удобства длинный литерал можно разбить символом `'` 
  (*например,* 3.1415'92653'58979 или 0х3.243F'6А88'85А3'0803)

### 1.4.1 Arithmetics

- В присваиваниях и арифметических операциях C++ выполняет неявные преобразования *фундаментальных* типов. Если типы будут пользовательские, то для их неявных преобразований нужны [неявные конструкторы](explicit--) либо пользовательские преобразования типов
  **TODO:** добавить ссылку на заметку о пользовательском преобразовании типов
  Например:
  `int` + `double` = `double`
- Порядок вычисления выражение - слева направо ->
- Порядок вычисления присваиваний - справа налево <-

### 1.4.2 Initialization

- Инициализация присваиванием
```cpp
double d1 = 2.3;
complex<double> z1 = 1;

int a = 7.8; // now a = 7
```

- Инициализация с помощью списка инициализации
```cpp
double d2 {2.3}; // the same double d2 = {2.3};
comlex<double> z2 {12, 234.5};

int b {7.8}; //ERROR:Type 'double' cannot be narrowed to 'int' in initializer list
int b {static_cast<int>(2.4)} // OK 
```

- Проблемы, вызванные неявными сужающими преобразованиями, - цена, заплаченная за совместимость с C
- `const` значения не могут остаться не инициализированными
```note
1. Не вводите сущность, пока у вас не будет для него подходящего значения
```

- `auto` keyword
```cpp
auto b = true;    // bool
auto ch = 'x';    // char
auto i = 123;     // int 
auto d = 1.2;     // double
auto z = sqrt(y); // typeid(z).name() == typeid(sqrt(y)).name()
auto bb {true};   // bool

auto v;           // ERROR: Declaration of variable 'v' with deduced type 'auto'
                  //        requires an initializer
```

**TODO:** добавить про область видимости и время жизни `auto`

## 1.5 Область видимости и время жизни

- Объявление вносит объявляемое имя в область видимости
  
- Локальная область видимости: 
	- начало: место объявления 
	- конец:  до конца блока {} в котором находится объявление
	Например: имена аргументов функции
- Область видимости класса: имя называется *именем члена класса*
  (если оно определено в классе, то)
	- начало: { начало объявление класса
	- конец:  } конец объявления класса
- Область видимости пространства имен:
	- начало: точко объявление
	- конец:  конец пространства имен
- Имя объявленное вне этих конструкций называется *глобальным именем* и считается находящимся в глобальном пространстве имен

```cpp
vector<int> ivector; // ivector -- global name


struct Record {
string name; // name -- member of struct Record
// ...
};


void fct (int arg) { // fct -- globalo func's name
                     // arg -- local name
string motto {"Who dares wins"}; // motto -- local name
auto p = new Record{"Hume"};     // p -- point to temporary object
}
```

- Объект должен быть инициализирован, прежде чем использован, а после выхода из области видимости - уничтожен
- Для объекта пространства имен точка уничтожения - конец программы
- Для члена класса точка уничтожения - момент уничтожения объекта, членом которого он является
- Объект, созданный с помощью оператора `new`, живет пока не будет уничтожен оператором `delete`

___
## 1.6 Constants

