# C coding guidelines

*NOTE: Этот документ нельзя использовать как гайдлайны по C++ или другим языкам*

# Code conventions

## Скобки

Фигурные скобки ставятся на следующей строке и выравниваются по вертикали.
Блок внутри фигурных скобок отбивается единичным отступом.

```c
function foo()
{
    //Do something
}

if (price > 0)
{
    //Positive
}
else
{
    //Negative
}
```

Фигурные скобки ставятся всегда!

Неправильная запись:

```c
if (price > 0)
    foo();
  
for (i = 0; i < 10; i++)
    foo(i);
```

Правильная запись:

```c
if (price > 0)
{
    foo();
}

for (var i=0; i<10; i++)
{
    foo(i);
}
```

Тело `if`, `else`, `while`, `for` и `switch` обязательно обрамляется
фигурными скобками.

## Пробельные символы

Максимальная длина строки — 78 символов (допускается 80).

Единичный отступ оформляется в 2 или 4 пробела в зависимости от того, как принято на проекте. Использование табов запрещено.

Бинарные операторы отбиваются с обеих сторон пробелом. Унарные операторы пишутся
слитно с переменной. Тернарный оператор отбивается пробелами.
Символы `;`, `.` и `,` пишутся слитно с предшествующим текстом.

```с
int a = 1 + 2;
int b = a++;
int c = (a > 0) ? 'yes' : 'no';
```

После имени функции пробел не ставится.

После ключевых слов `if`, `while`, `for` и `switch` ставится пробел.

```c
if (condition)
{
    //do something
}
```

## Line endings

В конце строки не должно быть пробельных символов.

Допустимы только unix line endings (\n).

## Именование переменных

Никакой "венгерской нотации". (Имеется в виду запрет на формальную Systems
Hungarian нотацию, в противовес содержательной Apps Hungarian.)

Константы именуются ЗАГЛАВНЫМИ_БУКВАМИ.

Обычные переменные, имена функций и проч. — через_подчёркивание, без заглавных букв.

Имя переменной, обычно, существительное.

Имя переменной, содержащей объект должно содержать название этого объекта

Имя переменной (таблицы), содержащей в себе коллекцию объектов обычно содержит
существительное во множественном числе (`foos` — коллекция объектов `foo`).

Имя булевой переменной, обычно, `is_*` (`are_*`, `has_*` и проч. формы to be),
`have_*`, `need_*`, `should_*`, `must_*`, `in_*`, `not_*` и т.п.

Количество объектов: `num_*`.

## Именование функций

Имя функции должно заключать в себе глагол либо заканчиваться на существительное
с окончанием -er.

## Указатели

Корректное написание:

```с
type * name_ptr
val_ptr = *name
val_ptr->field
```

## Директивы препроцессора

При оборачивании кода в директиву препроцессора отступ не добавляется:
```с
#ifdef foo
/* code here without indent */
#endif /* #ifdef foo */
```

```с
#ifndef HEADER_NAME_H_INCLUDED_
#define HEADER_NAME_H_INCLUDED_
/* header code here */
#endif /* HEADER_NAME_H_INCLUDED_ */
```

## Булевы операции

Следует ставить скобки вокруг булевых операций:

```с
return (foo && bar)
a = (foo || bar)
(a BOOLOP b) ? op1 : op2;

return (long_name_one && long_name_two)
    ? (long_name_three != long_name_four)
    : false;
```

за исключением подобных ситуаций:

```с
f(foo BOOLOP bar, baz)
```

В тернарном операторе первый операнд всегда пишется в скобках.

```с
(a && b || c) ? op1 : op2;
```

# Best practices

## Стандарты
Допустимо использовать C89 или C99, но стандарт должен быть един по всему
коду проекта.

### Lua modules

Для lua modules код должен соответствовать трём стандартам одновременно:
C89, C99, C++98.

Запрещена динамическая аллокация памяти не через луашный аллокатор, взятый
из стейта.

## Переменные

Необходимо инициализировать переменные при объявлении.

## Глобальные переменные

1) Глобальные переменные должны иметь префикс `g_`.

2) Глобальные переменные в общем случае использовать запрещено. Каждый случай
использования глобальных переменных должен утверждаться.

Вместо глобальных переменных рекомендуется использовать структуру-состояние,
передавая указатель на неё первым аргументом функций.

## Публичные функции

Публичные функции библиотек должны предваряться префиксом библиотеки `prefix_`,
утверждаемым в каждом конкретном случае.

## Приватные функции

Приватные функции обязательно объявлять как `static`.

## Приватные макросы

Приватные макросы обязательно удалять после использования с помощью директивы
`#undef`.

```с
#define MACRONAME(X, Y, Z) ((X) + (Y) + (Z))
/* code here */
#undef MACRONAME
```
