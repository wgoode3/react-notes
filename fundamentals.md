# MERN - JS Fundamentals
{{ JS IMAGE }}
introduction


<hr>

# Variables
when we need to be able to store information we need to use variables in js. Typically we will combine both the step of declaring a variable and the step setting a variable. 

{{ DIAGRAM OF VARIABLE ASSIGNMENT }}

```javascript
var a = 3;
var b = true;
var c = [5, 1.2, 7];
var d = "abacus";
var e = function() {};
```

Javascript needs us to use the `var` keyword before naming our variable. The `=` is used to set the variable equal to whatever value is on the right.

Javascript will determine what type each of the variables will be. 

```javascript
typeof(a); // 'number'
typeof(b); // 'boolean'
typeof(c); // 'object'
typeof(d); // 'string'
typeof(e); // 'function'
```

### New in ES6

```javascript
const pi = 3.141592;
let temp = "hello";
```

# Conditionals

### if / else if / else


### Hello Operators

The following `operators` will compare two values (one before and one after) and return a boolean (true of false).

| comparison operator | what it does                                                          | example |
|---------------------|-----------------------------------------------------------------------|---------|
| ==                  | checks that the values are the same                                   | a == 1  |
| ===                 | checks that the values are the same                                   | b === 3 |
| !=                  | checks that the values are **not** the same                           | b != a  |
| !==                 | checks that the values are **not** the same                           | a !== 3 |
| >                   | checks that the first value is larger than the second                 | a > 1   |
| <                   | checks that the first value is smaller than the second                | a < 3   |
| >=                  | checks that the first value is larger than or the same as the second  | a >= b  |
| <=                  | checks that the first value is smaller than or the same as the second | b <= 3  |

Note there is no such thing as `!>` (not greater than) or `!<` (not less than)... instead use `<=` (less than or equal to) for the former or `>=` (greater than or equal to) for the latter.

### Not all Equals are the same

We may be asking what is the difference between `==` and `===`? In fact we've seen the `==` and `!=` operators referred to as the evil twins of the `===` and `!==` operators.

They seem to work the same for most things...

```javascript
1 ==  2     // false
1 === 2     // false
1 ==  "one" // false
1 === "one" // false
```

However the `==` will sometimes try a little harder to make things equal.

```javascript
3 == "3"   // true 
3 === "3"  // false
1 == true  // true
1 === true // false
```

In the first example the string `"3"` could be converted to the number `3` so the double equals `==` will return true, and in the second example the number `1` is considered truthy (a concept we'll touch on soon) so it is also considered true. However the triple equals `===` will mandate that the things being compared must be the same type to be equal. This strictness when it comes to type means that `===` can run faster then `==` and can also help us avoid tricky to fix bugs. Some frameworks may even be opinionated enough about this to complain (but work anyway) when we use `==` or `!=` instead of `===` or `!==`.

{{ IMAGES OF REACT COMPLAINING ABOUT USING == }}

### Truth tables

explanation of and and or

#### And
| **&&**    | true    | false   | 
|:---------:|:-------:|:-------:|
| **true**  | &check; | &times; |
| **false** | &times; | &times; |

#### Or
| **\|\|**  | true    | false   | 
|:---------:|:-------:|:-------:|
| **true**  | &check; | &check; |
| **false** | &check; | &times; |

### truthyness

When we've been working with JavaScript

| Type      | example when false | example when true   |
|-----------|--------------------|---------------------|
| booleans  | if ( false )       | if ( true )         | 
| strings   | if ("")            | if ( "hello" )      |
| numbers   | if (0)             | if (-1) || if (5)   |
| objects   | if (null)          | if ([]) || if ({})  |
| undefined | if ({}.errors)     |                     |
| function  |                    | if ( function(){} ) |



### ternary

### switchcase

<hr>

# Loops

### for

### while

### New in ES6
block scoped variables

# Objects and Arrays
