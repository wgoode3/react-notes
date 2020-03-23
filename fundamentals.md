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

We may be asking what is the difference between `==` and `===`? They seem to work the same for most things...

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

In the first example the string `"3"` could be converted to the number `3` so the double equals `==` will return true, and in the second example the number `1` is considered truthy (a concept we'll touch on soon) so it is also considered true. However the triple equals `===` will mandate that the things being compared must be the same type to be equal. This strictness when it comes to type means that `===` can run faster then `==` and can also help us avoid tricky to identify bugs in our code. 

### && and/or ||

Sometimes we need conditions where we want more than one thing to be true...

```javascript
if (condition === "sunny") {
  if(windspeed > 10) {
    wear_a_hat();
  }
}
```

Instead of needing to nest the two checks inside of each other we can use an additional operator `&&` (and) to write just one if statement that runs when both things are true.

```javascript
if (condition === "sunny" && windspeed > 10) {
  wear_a_hat();
}
```

If we wanted to `wear_a_hat()` when either it's sunny or windy, we could use the `||` (or) operator instead.

```javascript
if (condition === "sunny" || windspeed > 10) {
  wear_a_hat();
}
```

To see a breakdown of how this logic will play out when each side is true and or false, we can consult what are known as truth tables.

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

**Note:** don't mistake the `||` operator for the `|` operator or the `&&` operator for the `&` operator. The single character versions are used with bit arithmetic (1's and 0s') and not logic operations (true's and false's). 

### "Truthiness"

In Javascript, conditionals can infer if a value is true of false even if the value isn't actually `true` or `false`. This means we can use our if statements without having to mess around with comparison operators like `===` or `>`.  Some examples that are consided true or false are displayed below...

| Type          | example(s) when false | example(s) when true   |
|---------------|-----------------------|------------------------|
| `'booleans'`  | `if ( false )`        | `if ( true )`          | 
| `'strings'`   | `if ("")`             | `if ( "hello" )`       |
| `'numbers'`   | `if (0) / if(NaN)`    | `if (-1) || if (5)`    |
| `'objects'`   | `if (null)`           | `if ([]) / if ({})`    |
| `'undefined'` | `if ({}.errors)`      |                        |
| `'function'`  |                       | `if ( function(){} )`  |

In fact almost everything is considered true except the following items:

* `false`
* `""`
* `0`
* `NaN`
* `null`
* `undefined`

These rules also can apply to loops...

**Caution:** Make sure you have `ctrl+c` handy if you test the two below pieces of code... they are infinite loops.

```javascript

while(1) {
  process.stdout.write("hello world ");
}

for(let i=0; ; i++) {
  console.log(i);
}
```

### Ternary Operators

Let's say we want to write as simple program to simulate flipping a coin...

```javascript
if( Math.random() > 0.5) {
  console.log("heads");
} else {
  console.log("tails");
}
// Math.random() will give us a number with a decimal between 0 and 1, randomly
```

It might be surprising, but we can condense this into one line...

```javascript
Math.floor() > 0.5 ? console.log("heads") : console.log("tails");
```

This is equivalent to the above `if else` that we have written. In a ternary, the condition (something that we're checking if it's true or false) will go first -> followed by a `?` (basically our `if`) -> followed by the code we want to run if the condition is true -> followed by a `:` (basically our `else`) -> and finished up by the the code we want to run if the condition is false.

These ternaries can take your coding to the next level and take up a lot less space on a whiteboard. We'd recommend you play around with them a bit, but while yes you can chain ternaries together you may be better off with the humble `if / else if / else`.

### switchcase

```javascript
switch( new Date().getDay() ) {
  case(0):
    console.log("It's Sunday");
    break;
  case(1):
    console.log("It's Monday");
    break;
  case(2):
    console.log("It's Tuesday");
    break;
  default:
    console.log("It's some other day");
}
```


### returning booleans

<hr>

# Loops

### for

### while

### New in ES6
block scoped variables

# Objects and Arrays

# Strings

# Functions
