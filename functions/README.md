# Functions

**Functions** are the core of any language, especially in *JavaScript* where they are one of the fundamental building blocks. Thruthly saying, *functions* are all for this language, without them it would be very few things possible to implement.

1. [Declaration](#declaration)
2. [Calling function](#calling-function)
3. [Return valuee](#return-value)
4. [Overloading](#overloading)
5. [Arguments](#arguments)
6. [IIFE](#iife)

## Declaration <a name="declaration"></a>

To declare a new function you need to:
- specify **function** keyword
- followed by the **name** of the function
- specify list of arguments enclosed in parentheses and separated by commas
- put statements enclosed in curly brackets, **{ }**.

Here is an example:
```javascript
function sayHello(username) {
  console.log('Hello, ' + username + '.');
}
```
As you can see we have a function named **sayHello** that accept one argument **username** and print greeting. Nothing complicated, is not it?

> You don't need to put semicolon after closed bracket. If you do put it compiler will treat it as an empty separated statement.

## Calling function <a name="calling-function"></a>

To call the function just enter function name and input parameters in paretheneses saperated by commas. Don't forget to put semicolon at the end:
```javascript
sayHello('John');
> Hello, John.
```

But what will happen if we will forget to specify input parameter and call function without it? Let's try:
```javascript
sayHello('John');
> Hello, undefined.
```

As you can see in JavaScript it's not an error (in comparison with some other languages - Java, etc.), the missed value is substituted with **undefined** value.

Let's try now pass more parameters than we have arguments in the function declaration:
```javascript
sayHello('John', 'Peter');
> Hello, undefined.
```

Once again there are no errors, extra parameter is just ignored by the compiler. Is not it awesome? Very forgiven language.

And what about types? The situation is the same as with variable declaration, the type of the argument is calculated dynamically in runtime. So you can pass parameters of different types in each function call, all of them will be accepted. 

## Return value <a name="return-value"></a>

To return a value use **return** keyword followed with any value that you wish to return from the function. Let's define another function to sum up two numbers:
```javascript
function add(a, b) {
  return a + b;
}
```
> Note that aside from the *return* statement there is no special declaration indicating that the function returns something.

To use returned value further in the program set it to a variable:
```javascript
var sum = add(3, 4);
```

Keep in mind that function returns emediately when it meets the *return* statement. Any code that comes after a *return* statement will never be executed. Let's try this:
```javascript
function add(a, b) {
  console.log("This message will be printed to the console.");
  return a + b;
  console.log("This will never by be executed and appeared in the console.");
}
add(3, 2);
```

You should see onle one message in the console:
```
> This message will be printed to the console.
```

You are not limited to use only one *return* statement inside functions:
```javascript
function smaller(a, b) {
  if(a > b) {
    return b;
  } else {
    return a;
  }
}
```

But if you will specify two consecutive *return* statements, only the first will be executed (the second one will be ignored):
```javascript
function add(a, b) {
  return a + b;
  return a - b;
}

var sum = add(2, 3);
console.log(sum);

> 5
```

The *return* statement can also be used without any value (followed by semicolon):
```javascript
function doNothing() {
  return;
}
```

In this case the **undefined** value will be returned back:
```javascript
var result = doNothing();
console.log(result);
```
You should see `undefined` in the console. Actually even if you won't specify any *return* statement in the function it will still return *undefined* value. As you remember when we discussed expressions and staments we learned that they do always return something, *function call* is not an exception. 

Try this:
```javascript
function doNothing() {
  console.log('I have no return statement but still return a value.');
}
var result = doNothing();
console.log(result);

> undefined
```

> It's recommended that a function either always return a value with *return* statement or never use *return* statement at all. Writing a function that sometimes returns a value causes confusion, especially during debugging.

## Overloading <a name="overloading"></a>

## Arguments <a name="arguments"></a>

## IIFE <a name="iife"></a>

## Function variable vs Function expression <a name="variable-vs-expression"></a>




