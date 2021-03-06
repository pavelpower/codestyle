JavaScript CodeStyle
====================

##Общие положения

  * Кодировка UTF-8 без [BOM](http://en.wikipedia.org/wiki/Byte-order_mark).
  * Перевод строки: LF (\n). В конце файла перевод строки **обязателен**. 
  * Отступ 4 пробела, знаки табуляции не применяются.
  * Длина линии не должна превышать 120 символов.
  * Нет лишних пробелов в конце строк (настраиваем свой текстовый редактор, чтобы он удалял лишние пробелы при сохранении).
  * При написании текста всегда нужно помнить одно правило: до знака препинания пробел не ставится, а после знака препинания пробел необходимо ставить обязательно. (Есть исключения для скобок, тире, кавычек).

##Именование
  * `variableNamesLikeThis`
  * `functionNamesLikeThis`
  * `ClassNamesLikeThis`
  * `methodNamesLikeThis`
  * `CONSTANTS_LIKE_THIS`
  * `namespaceLikeThis`
  * `event-like-this`
  * `private` свойства и методы объектов начинаются с подчеркивания `_`
  * `protected` свойства и методы объектов также начинаются с подчеркивания `_`
  * Избегаем коротких или немногословных названий
  * В именовании аббревиатур соблюдаем `CamelCase`. Например: `Json`, `Xml`.

##Объявление переменных
  * Все переменные объявленные через **var** должны быть объявлены в начале scope
  * Переменные объявленные с помощью оператора **let** должны должны быть объявлены рядом с местом использования
  * Каждая переменная в пределах одной области видимости объявляется только один раз.

**Хорошо:**
```javascript

function fn() {
    var keys, values, object;
    
    keys = ['foo', 'bar'];
    values = [23, 42];
    object = {};
    
    while (items.length) {
        let key = keys.pop();
        object[key] = values.pop();
    }
}

```

**Плохо:**
```javascript
function fn () {
    var keys = ['foo', 'bar'],
        values = [23, 42],
        object = {},
        key;
    
    while (items.length) {
        key = keys.pop();
        object[key] = values.pop();
    }
}
````

**Допустимо, при необходимости дополнительной информации к переменным:**
```javascript
function fn2 () {
    /** keys - список ключей к объекту */
    var keys = ['foo', 'bar'];
    
    /** values - список ключей к объекту */
    var values = [23, 42];
    
    var object = {};
    while (items.length) {
        var key = keys.pop();
        object[key] = values.pop();
    }

}
```

##Литералы

###Объекты

  * После открывающей фигурной скобки и перед закрывающей пробел не ставится:

```javascript
var obj = {a: 1, b: 2, c: 3};

this.method({a:1, b:2});
```
  * Пробел перед двоеточием не ставится:

```javascript
var obj = {
    prop: 0
};
```
  * Выравнивание не используется:

**Хорошо:**

```javascript
var obj = {
    a: 0,
    b: 1,
    lengthyName: 2
};
```
**Плохо:**

```javascript
var obj = {
    a          : 0,
    b          : 1,
    lengthyName: 2
};
```
  * Имена ключей заключаются в кавычки только по необходимости:

**Хорошо:**

```javascript
var obj = {
    key: 0,
    'key-key': 1
};
```
**Плохо:**
```javascript
var obj = {
    'key': 0,
    'key-key': 1
};
```

###Массивы

При объявлении массива, пробел ставится лишь после запятой:

```javascript
var fellowship = ['foo', 'bar', 'baz'];
```

###Строки
  * Строки записываются с использованием одинарных кавычек:

```javascript
var lyrics = 'Never gonna give you up, Never gonna let you down';
```

  * Если в строке встречается одинарная кавычка, она экранируется:

```javascript
var test = 'It shouldn\'t fail';
```

##Точка с запятой
* Точка с запятой ставится всегда, при объявлении переменной, включая функции.
```javascript
  var a = 2;
  var fn = function(n) {
      return 2 * n;
  };
```

* И не ставится если функция объявленна без присвоения ее переменной:
```javascript
function fn (n) {
     return 2 * n;
}
```

##Пробелы
  * Ключевые слова отделяются пробелом:

```javascript
if (test) {
    // ...
}

function foo() {
    // ...
}

var bar = function () {
    // ...
};
```

  * Перед точкой с запятой пробел не ставится:

```javascript
return;
```

##Фигурные скобки
  * Открывающая фигурная скобка ставится на той же строке и отделяется пробелом от предыдущей конструкции:

```javascript
if (test) {
    // ...
}

function foo() {
    // ...
}
```
  * Фигурные скобки ставятся всегда:

**Хорошо:**

```javascript
if (test) {
    return;
}
```
**Плохо:**

```javascript
if (test)
    return;

if (test) return;

if (test) { return; }
```

  * Фигурные скобки также могут быть использованы для создания блочной конструкции с целью выделения участка кода из окружающего кода:

```javascript
expression1();

{
   function logicallyGroupedMethod1() {
      // ...
   }
   function logicallyGroupedMethod2() {
      // ...
   }
   function logicallyGroupedMethod3() {
      // ...
   }
}

expression2();
```

  * Впоследствии такая блочная конструкция может быть выделена в функцию, либо вынесена в отдельный файл:

```javascript
function callLogicalGroup() {
   function logicallyGroupedMethod1() {
      // ...
   }
   function logicallyGroupedMethod2() {
      // ...
   }
   function logicallyGroupedMethod3() {
      // ...
   }
}

expression1();

callLogicalGroup();

expression2();
```

##Условные инструкции
###if
  * `else` пишется на той же строке, что и закрывающая фигурная скобка

```javascript
if (test) {
    // ...
} else {
    // ...
}
```
  * Присваивание в условном выражении не используется:

**Хорошо:**

```javascript
var foo = bar();
if (foo > 0) {
    // ...
}
```

**Плохо:**
```javascript
var foo;
if ((foo = bar()) > 0) {
    // ...
}
```
  * Выражения используются только там, где требуется значение:

**Хорошо:**

```javascript
if (condition) {
    actionIfTrue();
} else {
    actionIfFalse();
}
```

**Плохо:**
```javascript
condition && actionIfTrue() || actionIfFalse();
```

  * Длинные условия, которые не вмещаются на одну строку, разбиваются следующим образом:

```javascript
if (longCondition ||
    anotherLongCondition &&
    yetAnotherLongCondition
) {
    // ...
}
```

 * [Yoda conditions](http://en.wikipedia.org/wiki/Yoda_conditions) не используются:

**Хорошо:**
```javascript
if (getType() === 'driving') {

}
```

**Плохо:**
```javascript
if ('driving' === getType()) {

}
```

###switch

```javascript
switch (value) {
    case 1:
        // ...
        break;

    case 2:
        // ...
        break;

    default:
        // ...
        // no break keyword on the last case
}
```

##Циклы
###for
По возможности вместо `for` используется [Array.prototype.forEach](https://developer.mozilla.org/ru/docs/JavaScript/Reference/Global_Objects/Array/forEach):

```javascript
[1, 2, 3].forEach(function (value) {
    console.log(value);
});
```

Код с ипользованием `forEach` проще читать (легче абстрагироваться от того, что происходит в каждой итерации). Где
критична скорость используется обычный `for`.

###for (var i in obj)
По возможности вместо `for-in` используется [Object.keys](https://developer.mozilla.org/ru/docs/JavaScript/Reference/Global_Objects/Object/keys):
```javascript
Object.keys(obj).forEach(function (key) {
    console.log(key);
});
```

##Операторы
###with

Оператор `with` не используется.

###Оператор равенства
Всегда используется строгое равенство `===` (неравенство `!==`), если нет необходимости в приведении типов.

###Тернарный оператор

```javascript
var x = a ? b : c;

var y = a ?
    longButSimpleOperandB : longButSimpleOperandC;

var z = a ?
    moreComplicatedB :
    moreComplicatedC;
```

###Унарный оператор
Все унарные операторы пишутся слитно с операндами:

```javascript
var foo = !bar;
```

##eval
Избегаем использования `eval`. Для парсинга `json` используется [JSON.parse](https://developer.mozilla.org/en-US/docs/JavaScript/Reference/Global_Objects/JSON/parse).

##undefined

Проверяем значение через строгое сравнение.

**Хорошо:**
```javascript
x === undefined;
```

**Допустимо толькол для (null):**
```javascript
x == null;

(x === undefined) // true
//then
(x == null) // true
  
```

**Плохо:**
```javascript
// в современных браузерах уже определен immutable undefined.
var undefined;
x === undefined;

// больше писать
typeof x === 'undefined'

x === void 0
```

##Круглые скобки
  * Ставятся, если только это необходимо синтаксисом или семантикой.
  * Не используются с унарными операторами `delete`, `typeof` и `void`, а также ключевыми
словами `return`, `throw`, `new`.

##Исключения

Создаём сиключения с помощью `new Error`:

**Хорошо:**
```javascript
throw new Error('msg');
```
**Плохо:**
```javascript
throw 'msg';
```

##Приведение типов

Используются явные приведения типов:

**Хорошо:**
```javascript
Boolean(foo)
Number(bar)
String(baz)
[].indexOf(qux) === -1 или [].indexOf(qux) < 0
```
**Плохо:**
```javascript
!!foo
+bar
baz + ''
~[].indexOf(qux)
```

##Переносы строк
  * Максимальная длина строки `120` символов, если строка выходит длиннее, то по возможности делаются переносы строки, с соответствующими отступами после переноса.
  * Операторы размещаются на предыдущей строке:

```javascript
var debt = this.calculateBaseDebt() + this.calculateSharedDebt() + this.calculateDebtPayments() +
    this.calculateDebtFine();
```

  * Закрывающие скобки не прижимаются к переносимому коду:

**Хорошо:**
```javascript
DoSomethingThatRequiresALongFunctionName(
    very_long_argument1,
    argument2,
    argument3,
    argument4
);
anotherStatement;
```
**Плохо:**
```javascript
DoSomethingThatRequiresALongFunctionName(
    very_long_argument1,
    argument2,
    argument3,
    argument4);
anotherStatement;
```

##Конкатенация строк
  * Для конкатенации строк используется оператор `+`.
  * Конструкция `[].join('')` не используется (это было актуально для старых браузеров).
  * `\` не используется.

**Хорошо:**
```javascript
var foo = 'A rather long string of English text, an error message ' +
    'actually that just keeps going and going -- an error ' +
    'message to make the Energizer bunny blush (right through ' +
    'those Schwarzenegger shades)! Where was I? Oh yes, ' +
    'you\'ve got an error and all the extraneous whitespace is ' +
    'just gravy.  Have a nice day.';
```
**Плохо:**
```javascript
var foo = 'A rather long string of English text, an error message \
          actually that just keeps going and going -- an error \
          message to make the Energizer bunny blush (right through \
          those Schwarzenegger shades)! Where was I? Oh yes, \
          you\'ve got an error and all the extraneous whitespace is \
          just gravy.  Have a nice day.';
```

##Пустые линии
Могут использоваться для логической группировки частей кода:

```javascript
doSomethingTo(x);
doSomethingElseTo(x);
andThen(x);

nowDoSomethingWith(y);

andNowWith(z);
```

##`this` в замыкании

* Рекомендуется использовать `Function.prototype.bind`:

```javascript
doAsync(function () {
    this.fn();
}.bind(this));
```

* Если функция позволяет передать `this` параметром, используем его:

**Хорошо:**

```javascript
[1, 2, 3].forEach(function (n) {
    this.fn(n);
}, this);
```

**Плохо:**

```javascript
[1, 2, 3].forEach(function (n) {
    this.fn(n);
}.bind(this));
```

* Если используется переменная, называем ее `_this`:

```javascript
var _this = this;
doAsync(function () {
    _this.fn();
});
```

##Комментарии
  * Комментарии пишутся на русском языке.
  * Для инлайновых комментариев используется `//`. После `//` ставится 1 пробел.
  * Комментарии к функциям, классам и т.п. пишутся в формате [jsduck](jsduck.md)
  
##Функции
###Аргументы
Выбирая сигнатуру функции, необходимо избегать [Boolean Trap](http://doc.qt.digia.com/qq/qq13-apis.html#thebooleanparametertrap):

```javascript
/**
 * @param {Boolean} async
 */
function fetchResults(async) {}

// По вызову функции непонятно, что означает false.
fetchResults(false);
```

Используем следующие методы для того, чтобы избежать Boolean Trap:

* Разделить метод или функцию на несколько:

```javascript
function fetchResultsSync() {}
function fetchResultsAsync() {}
```

* Использовать константы, перечисления или статические поля классов для значений параметров;

```javascript
/**
 * @enum {Boolean}
 */
var FetchMethod = {
    SYNC: false,
    ASYNC: true
};

/**
 * @param {FetchMethod} method
 */
function fetchResults(method) {}

fetchResults(FetchMethod.SYNC);
```

Так же избегаем [Convinience Trap](http://doc.qt.digia.com/qq/qq13-apis.html#theconveniencetrap):

```javascript
// Пример из WebGL (предлагается угадать без документации, что каждое число и false означают)
glCtx.vertexAttribPointer(this._glHandler, 4, glCtx.FLOAT, false, 0, 0);
```

От Convinience Trap и Boolean Trap необходимо использовать именованные параметры:

```javascript
/**
 * @param {Object} params
 * @param {Boolean} params.async
 */
function fetchResults(params) {}

fetchResults({async: false});

glCtx.vertexAttribPointer(this._glHandler, {
    size: 4,
    type: glCtx.FLOAT,
    normalizeData: false,
    stride: 0,
    offset: 0
});
```

##Классы
* Объявление классов и наследование реализуется с помощью `inherit`.
* Деструктор называем `destruct()`.
* "Симметричные" методы размещаем рядом. Например:

```javascript
var FooClass = inherit({
    __constructor: function () {},

    // деструктор рядом с конструктором
    destruct: function () {},

    someMethod: function() {}
});
```

##jQuery
* `jQuery` используем только для работы с `DOM`.
* Реализация `extend` и `inherit` заключена в отдельных одноименных модулях. Зависеть от `jQuery` при этом не следует.
* `jQuery.Deferred` не используется. Промисы реализованы с помощью библиотеки [vow](https://github.com/dfilatov/vow) и
подключаются модулем `vow`.

##node.js

### Импортирование модулей

* Все модули импортируются в начале файла сразу после описания к нему, если оно есть:

**Хорошо:**

```javascript
var http = require('http');
var fs = require('fs');

// code here
```
**Плохо:**

```javascript
var http = require('http');

// code here

var fs = require('fs');

// code here
```

Исключение: модули, импортируемые по требованию.

* Импорты должны быть сгруппированы в следующем порядке:

1. стандартные модули node.js
2. модули сторонних библиотек
3. модули вашего приложения
