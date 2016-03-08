# Conditional statements <a name="conditional-statements"></a>
A **conditional statement** is a statement that executes if some condition is 'true'. In *Javascript* there are two conditional statements:
 * [if-else statement](#if-else-statement)
 * [switch statement](#switch-statement)

Truthly saying, one of the most frequently used statement (not only in *Javascript*!) is **if-else statement**. Why is it so? 
Well, just think about long journey, you cannot always go straightforward, you always meet crossroads and need to choose either left or right turn. If you only need to buy a milk, it will be enough to cross road and do in the nearest market. But in this case this trip cannot be called a *journey*, even word *trip* is too big for such boring action. The same situation is for programming. If you use only normal flow when your code is executed line by line, you will have a valid but boring and probably very small applications. *Turns* (in our case *conditions*) bring fun and power to your code.

## if-else statement <a name="if-else-statement"></a>
The **if statement** executes a statement if a specified condition is 'true'. If a specified condition is 'false' - a statement defined in an **else statement** is executed. Let's see a simple example:
```javascript
if(5 == 5)
 console.log("5 equals 5");
else
 console.log("5 not equals 5, strange");

> "5 equals 5"
```
The *else statement* is optional, you can omit this part and specify code only for *if statement*:
```javascript
if(5 == 5)
 console.log("5 equals 5");

> "5 equals 5"
```
Let's now test *else statement* execution:
```javascript
if(5 != 5) 
 console.log("5 not equals 5, strange");
else
 console.log("5 equals 5");

> "5 equals 5"
```
If you need to specify more than one statement use [**block statement**](00-Overview.md#block-statement):
```javascript
if(5 == 5) {
 console.log("5 equals 5");
 console.log("I knew this!");
}

> "5 equals 5"
  "I knew this!"
```
You can specify block statement either in *if* or in *else* part of statement, even in both of them:
```javascript
if(5 != 5) {
 console.log("5 not equals 5");
 console.log("It's very strange!");
} else {
 console.log("5 equals 5");
 console.log("I knew this!");
}

> "5 equals 5"
  "I knew this!"
```
> It's a good practice to always use **block statement** instead of single statement, even if only one line of code needs to be executed. This prevent future confusion when you will need another statement, or another one will need to update your code, or indends will be wrong due to IDE formatting.

You can put nested *if-else statement* if you wish:
```javascript
var age = 16;
if(age > 15) {
  if(age < 17) {
    console.log("Your age is 15-17.");
  } else {
    console.log("Your age is greater than 17");
  }
} else {
  console.log("Your age is less than 15.");
}

> "Your age is 15-17."
```
You can even compound several conditions in *if-else* staircase:
```javascript
var age = 16;
if(age < 15) {
  console.log("Your age is less than 15.");
} else if (age < 17) {
  console.log("Your age is 15-17.");
} else {
  console.log("Your age is greater than 17");
}

> "Your age is 15-17."
```

## switch statement <a name="switch-statement"></a>
