# Functions

**Functions** are the core of any language, especially in *JavaScript* where they are one of the fundamental building blocks. Thruthly saying, *functions* are all for this language, without them it would be very few things possible to implement.

1. [Declaration](#declaration)
2. [Calling function](#calling-function)
3. [Return value](#return-value)
4. [Overloading](#overloading)
5. [Arguments](#arguments)
6. [IIFE](#iife)
6. [Strict mode](#strict-mode)

## Declaration <a name="declaration"></a>

To declare a new function you need to:
* specify **function** keyword
* followed by the **name** of the function
* specify list of parameters enclosed in parentheses and separated by commas
* put statements enclosed in curly brackets, **{ }**.

Here is an example:
```javascript
function sayHello(username) {
  console.log("Hello, " + username + ".");
}
```
As you can see we have a function named **sayHello** that accept one parameter **username** and print greeting. Nothing complicated, is not it?

> You don't need to put semicolon after closed bracket. If you do put it compiler will treat it as an empty separated statement.

## Calling function <a name="calling-function"></a>

To call the function just enter function name and input arguments in paretheneses saperated by commas. Don't forget to put semicolon at the end:
```javascript
sayHello("John");
> Hello, John.
```

But what will happen if we will forget to specify input argument and call function without it? Let's try:
```javascript
sayHello("John");
> Hello, undefined.
```

As you can see in JavaScript it's not an error (in comparison with some other languages - Java, etc.), the missed value is substituted with **undefined** value.

Let's try now pass more arguments than we have parameters in the function declaration:
```javascript
sayHello("John", "Peter");
> Hello, undefined.
```

Once again there are no errors, extra argument is just ignored by the compiler. Is not it awesome? Very forgiven language.

And what about types? The situation is the same as with variable declaration, the type of the argument is calculated dynamically in runtime. So you can pass parameters of different types in each function call, all of them will be accepted. 

Keep in mind that all arguments are passed by value in *Javascrip*. So if we will pass *Number* argument to the function and will try to update it value inside, we won't see updated value after returning from the function:
```javascript
function incrementByFive(a) {
  console.log("Here is an input value - " + a + ".");
  a += 5;
  console.log("I have incremented it by five - " + a + ".");
}

var b = 10;
incrementByFive(b);
console.log("Here is an input value - " + b + ".");

> Here is an input value - 10.
> I have incremented it by five - 15.
> Here is an input value - 10.
```

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
  console.log("I have no return statement but still return a value.");
}
var result = doNothing();
console.log(result);

> undefined
```

> It's recommended that a function either always return a value with *return* statement or never use *return* statement at all. Writing a function that sometimes returns a value causes confusion, especially during debugging.

## Overloading <a name="overloading"></a>

Unfortunately, in *Javascript* there is no function overlaoding in its traditional sense. In some other languages, e.g. *Java*, it's possible to declare two functions with the same name as long as they have different signatures (type and number of parameters). In *Javascript* as you know we cannot specify type of parameter - you can pass value of any type. Also you can pass less or more arguments to the functions. 

It seems that we cannot apply term *signature* to functions here. So, what will happen if we will declare two functions with the same name and different number of parameters? Let's try:
```javascript
function sum(a, b, c) {
  return a + b + c;
}

function sum(a, b) {
  return a + b;
}

var result = sum(1, 2, 3);
console.log(result);

> 3
```

In *Javascript* the last declared function is finally associated with the specified function name, it's like the second declaration overrides the first one. That is why be accurate in function declaration and don't use the same name twice!

> It's possible to simulate function overloading by checking type and number of parameters that have been passed into a function. For more details, please, read [Advanced Javascript Tutorial]().

## Implicit parameter *arguments* <a name="arguments"></a>

As we have learned *Javascript* does not care how many arguments do you specify in the fucntion call, it does complain for few or more values than function has arguments. Why does it happen? This happens because arguments are represented as an array internally. This array is always passed to the function as in input and function does not care what is in the array. It can be empty or not. This *implicit* parameter is called **arguments**.

Here is an example:
```javascript
function guessMyName() {
  console.log("Your name is " + arguments[0] + ".");
}

guessMyName("Peter");
> Your name is Peter.
```
Thruthly saying it's not a fully-implemented array, you cannot use any methods that are declared in *Array* object. All what is available is iterating over it and getting its length:
```javascript
function printAllParameters() {
  for(var i = 0; i < arguments.length; i++) {
    console.log("Parameter #" + i + " contains value " + arguments[i] + ".");
  }
}

printAllParameters("one", "two", "three");
> Parameter #0 contains value one.
  Parameter #0 contains value two.
  Parameter #0 contains value three.
```

The *arguments* parameter can also be used in cojunction with named parameters, there is no restiction for this:
```javascript
function printUsername(username) {
  console.log("Here is named parameter value - " + username + ".");
  console.log("Here is 'arguments' array values:");
  for(var i = 0; i < arguments.length; i++) {
    console.log("Parameter #" + i + " contains value " + arguments[i] + ".");
  }
}

printUsername("Grant");
> Here is named parameter value - Grant.
  Here is 'arguments' array values:
  Parameter #0 contains value Grant.
```

## IIFE <a name="iife"></a>

## Strict mode <a name="strict-mode"></a>

There are several restrictions if you are using **strict mode**, compiler is just not so forgiven:

* **No two named parameters can have the same name**

 Let's first try to call the following function without *strict mode*:
 ```javascript
function sum(a, a) {
  return a + a;
}

var result = sum(1, 5);
console.log(result);

> 10
 ```

 As you can see the behaviour is very similar with the function duplicate declaration. If there are two or more parameters with the same name, the last parameter declaration overrides all previous ones. That is why we get `10` - `5 + 5` equals `10`.

## Function variable vs Function expression <a name="variable-vs-expression"></a>




