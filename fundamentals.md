# MERN - JS Fundamentals
{{ JS IMAGE }}
introduction


<hr>

# Variables
When we need to be able to store information we need to use variables in js. Typically we will combine both the step of declaring a variable and the step setting a variable. 

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

{{ DIAGRAM: ANATOMY OF VARIABLE ASSIGNMENT }}

### New in ES6

```javascript
const pi = 3.141592;
let temp = "hello";
```

ES6 introduces two new ways to declare variables. `const` is essentially a constant, once we set it it does not support reassignment (use of the `=` operator). `let` is a variable that we intend to allow to change and therefore does support reassignment. Where `var` is considered "function scoped", `let` is instead "block scoped". We promise to get back to the idea of scope later on... but to see the difference in action, [the MDN has us covered](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/block).

<hr>

# Hello Operators?

### Math Operators

The following operations can be performed on numbers in Javascript.

| operator | description                                                               |
|----------|---------------------------------------------------------------------------|
| +        | add the values on the left and right                                      |
| -        | subtract the value on the right from the value on the left                |
| *        | multiply the values on the left and right                                 |
| /        | divide the value on the left by the value on the right                    |
| %        | find the remainder of value on the left divided by the value on the right |
| ++       | increment the value by 1 ( adds one )                                     |
| --       | decrement the value by 1 ( subtracts one )                                |

### Assignment Operators

| operator | description                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| =        | set the variable on the left to the value on the right                                                      |
| +=       | increase the variable on the left by the value on the right                                                 |
| -=       | decrease the variable on the left by the value on the right                                                 |
| \*=      | mulitply the variable on the left by the value on the right and set it equal to the result                  |
| /=       | divide the variable on the left by the value on the right and set it equal to the result                    |
| %=       | find the remainder of variable on the left divided by the value on the right and set it equal to the result |

### Comparison Operators

The following `operators` will compare two values of any type and return a boolean (true of false).

| operator | description                                                           |
|----------|-----------------------------------------------------------------------|
| ==       | checks that the values are the same                                   |
| ===      | checks that the values are the same                                   |
| !=       | checks that the values are **not** the same                           |
| !==      | checks that the values are **not** the same                           |
| >        | checks that the first value is larger than the second                 |
| <        | checks that the first value is smaller than the second                |
| >=       | checks that the first value is larger than or the same as the second  |
| <=       | checks that the first value is smaller than or the same as the second |

Note there is no such thing as `!>` (not greater than) or `!<` (not less than)... instead use `<=` (less than or equal to) for the former or `>=` (greater than or equal to) for the latter.

#### Not all Equals are the same

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

In the first example the string `"3"` could be converted to the number `3` so the double equals `==` will return true, and in the second example the number `1` is considered *"truthy"* (a concept we'll touch on soon) so it is also considered true. However the triple equals `===` will mandate that the things being compared must be the same type to be equal. This strictness when it comes to type means that `===` can run faster then `==` and can also help us avoid tricky to identify bugs in our code. 

### Logical Operators

The following `operators` are used with booleans.

| operator | description                                                               |
|----------|---------------------------------------------------------------------------|
| !        | is the oposite of whatever boolean follows (**not** true / **not** false) |
| &&       | is true if **both** the before and after values are true                  |
| \|\|     | is true if **either** the before or after values are true                 |

We'll see more about the last two operators in in the Conditionals module, but we're introducing them here for completeness.

**Note:** don't mistake the `||` operator for the `|` operator or the `&&` operator for the `&` operator. The single character versions are used with bit arithmetic (1's and 0s') and not logic operations (true's and false's). We're going to leave out bitwise operators for now if you are curious about them check out [the MDN once again](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Bitwise_Operators).

### New in ES6

One somewhat uncommon operation we may need to perform is finding the exponential of some value. ES6 introduces the `**` operator to make this a lot easier.

```javascript
console.log(2**8); // 256
```

In the past we'd have to use the `Math` library to find an exponential.

```javascript
console.log( Math.pow(2, 8) ); // 256
```

We are also able to use `**=`, the assignment version of the exponential operator.

```javascript
let b = 2;
b **= 16;
console.log(b); // 65536
```

<hr>

# Conditionals

### if / else if / else

Sometimes our code needs to react differently based on some condition. 

```javascript
var lightCount = 4;
console.log("there are", lightCount, "lights");
```

The console log will work just fine in the first case and print out `there are 4 lights`.

```javascript
var lightCount = 1;
console.log("there are", lightCount, "lights");
```

It will aslo work for the second case albeit with some grammatical inaccuracy printing out `there are 1 lights`.

If we want to fix this we need our code to be able to branch off one way or the other, we need a conditional.

```javascript
if (lightCount === 1) {
  console.log("there is", lightCount, "light");
} else {
  console.log("there are", lightCount, "lights");
}
```

Sometimes we need more options than just the two we get with `if` and `else`.

We can chain as any if / else statements together as we need and they will run in succession.

```javascript
if( weather === "sunny" ) {
  console.log("bring sunglasses");
} else if( weather === "cold" ) {
  console.log("bring a coat");
} else if( weather === "rainy" ) {
  console.log("bring an umbrella");
} else {
  console.log("you don't need to bring anything");
}
```

In this case it will first check if weather is sunny, then if the weather is cold, then if the weather is rainy, and if none of those are true it will run the else statement. If the weather is sunny, it won't bother checking any of the other conditions. In general it's a good idea to write the most specific condition first followed by less and less specific conditions and allow the `else` to be what happens if nothing matches.

Imagine we've written this code...

```javascript
if( number % 2 === 0 ) {
  console.log("the number is divisible by 2");
} else if( number % 3 === 0 ) {
  console.log("the number is divisible by 3");
} else if( number % 6 === 0 ) {
  console.log("the number is divisible by 6");
}
```

The message `"the number is divisible by 6"` will never run because the first check will always be true before we get to it. We should instead write this code like...

```javascript
if( number % 6 === 0 ) {
  console.log("the number is divisible by 6");
} else if( number % 3 === 0 ) {
  console.log("the number is divisible by 3");
} else if( number % 2 === 0 ) {
  console.log("the number is divisible by 2");
}
```

### "Truthiness"

In Javascript, conditionals can infer if a value is true of false even if the value isn't actually `true` or `false`. This means we can use our if statements without having to mess around with comparison operators like `===` or `>`.  Some examples that are consided true or false are displayed below...

| Type          | example(s) when false | example(s) when true   |
|---------------|-----------------------|------------------------|
| `'booleans'`  | `if ( false )`        | `if ( true )`          | 
| `'strings'`   | `if ("")`             | `if ( "hello" )`       |
| `'numbers'`   | `if (0) / if(NaN)`    | `if (-1) \|\| if (5)`  |
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

### Ternary Operators

Let's say we want to write a simple program to simulate flipping a coin...

```javascript
if( Math.random() > 0.5 ) {
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

{{ DIAGRAM, ANATOMY OF A TERNARY }}

### switchcase

Yet another way we can write a conditional is by using a switchcase. In the following example we check what day it is, the `new Date().getDay()` will return a different number for each day of the week. 

```javascript
switch( new Date().getDay() ) {
  case(0):
    console.log("It's Sunday");
    break;
  case(1):
    console.log("It's Monday");
    break;
  default:
    console.log("It's some other day");
}
```

With a switchcase, we provide a value to the `switch()` and check for each value one after the other in the `case()` statements. As only one case should ideally match, it's common to use a `break` to end the `switch()` code block and avoid checking unnecessary cases. The `default` case is there to execute if no other case will match. It's similar to the `else` we might have at the end of an `if / else if / else` conditional.

{{ DIAGRAM, ANATOMY OF A SWITCHCASE }}

<hr>

# Loops

When we think about the major advantages that computing can provide for us, handling repetative tasks is probably one of the first things that come to mind. As programmers we should see code like this...

```javascript
console.log(1);
console.log(2);
console.log(3);
// ...
console.log(10);
```

and think there must be a better way.

### for

For loops are one of the better ways. The code we saw above can be rewritten like the below example.

```javascript
for(var i=1; i<11; i++) {
  console.log(i);
}
```

To write a for loop we use the `for` keyword, and we need to provide 3 clauses. The first clause `var i=1` is declaring a variable and setting it equal to 1. This runs once, at the very beginning of the loop. The second clause `i<11` should be some sort of comparison and as long as the value is true (or is considered truthy) the for loop will keep running. The final clause `i++` will run with every iteration of the loop, in this case each time the loop is run the variable `i` will increase by 1 until the second clause (`i<11`) is no longer true.

For loops like this are convenient as they provide an easily controlled way to generate the numbers from some starting value to some ending value. We can make the numbers count down instead fairly easily as well...

```javascript
for(vari=10; i>0; i--){
  console.log(i);
}
```

This time starting at a high value, running as long as the value is greater than 0, and decreasing by one each time. 

It's also common to set the increment to change by more than one using the `+=` and `-=` operators.

### while

A while loop is a bit like an `if` that keeps running its contents as long as the condition is true. They are especially good if we don't know how many times something should run.

```javascript
var done = false;

while( !done ) {
  var input = prompt("Say uncle!");
  if( input === "uncle" ) {
    done = true;
  }
}
```

This program will keep prompting with the text of "Say uncle!", until the user types in "uncle". It would be a bit unnatural to write this using a for loop, but with a while loop we can manage. 

We could make a while loop that counts much like the for loop we've written above. In fact we can hopefully see some similarities in how the logic works in this while loop.

```javascript
var i = 1;

while(i < 11) {
  console.log(i);
  i++;
}
```

Note how can still make an `i` variable and set it to 1. We can have the while loop run as long as `i < 11`. The `console.log` will still get run multiple times. And lastly we need to make sure we still have that `i++` or some other code that will make `i` increase to at least 11, otherwise the while loop will run forever (infinite loop).

### New in ES6
block scoped variables

<hr>

# Objects and Arrays

<hr>

# Strings

<hr>

# Functions

### variable scope

### returning booleans

