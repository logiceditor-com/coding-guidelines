C# coding guidelines
====================

Code conventions
================

Скобки
------

Фигурные скобки ставятся на следующей строке и выравниваются по вертикали.
Блок внутри фигурных скобок отбивается единичным отступом.


    public void foo()
    {
      // Do something
    }

    public class foo : boo
    {
      // Class methods
    }

Фигурные скобки ставятся всегда!

Неправильная запись:

    if (price>0)
      foo();

    for (var i=0; i<10; i++)
      foo(i);

Правильная запись:

    if (price > 0)
    {
      foo();
    }

    for (int i = 0; i < 10; i++)
    {
      foo(i);
    }

Тело `if`, `else`, `while`, `switch`, `try` и `catch` обязательно обрамляется
фигурными скобками.


Пробельные символы
------------------

Максимальная длина строки — 80 символов.

В коде **нужно использовать отступы шириной два пробела**
(**"единичный отступ"**). Использование символов табуляции запрещено.

Бинарные операторы отбиваются с обеих сторон пробелом.
Унарные операторы пишутся слитно с переменной.
Тернарный оператор отбивается пробелами, вокруг условий ставятся скобки.
Символы `;`, `.` и `,` пишутся слитно с предшествующим текстом.

    int a = 1 + 2;
    int b = a++;
    int c = a % b;

После имени функции пробел не ставится.
Пробел между кастом и выражением ставится.

    int a = foo(c);
    int a = (int) b;

После ключевых слов `if`, `while`, `switch` и `catch` ставится пробел.

    if (condition)
    {
      // do something
    }


Строки
------

В конце строки не должно быть пробельных символов.

Допустимы только unix line endings (LF).


Комментарии
-----------

После символа комментария обязателен пробел.
В пустых функциях нужно писать // Intentionally empty

    doNothing()
    {
      // Intentionally empty
    }

Функции, классы и методы
========================

### Примеры

      (
        (typeName) className
          .fieldName
          .methodName(params)
      ).value = anotherValue;

      (
        (typeName) className
          .fieldName
          .methodName(params)
      ).method(params);

Такие конструкции со скобками обязательно отбивать переводами строк до и после
(кроме случаев, когда на следующей строке `{` или `}`).

      typeName valueName = (typeName) className
        .fieldName
        .methodName(params);

      typeName valueName = (typeName) className
        .fieldName
        .methodName(params)
        ;

      classname
        .method1(
            params,
            params
          )
        .method2(
            params,
            params
          )
        .field = value
        ;
