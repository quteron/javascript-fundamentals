# Statements

*Javascript* supports numerous number of different statements. Most all of them have very similar syntax to other programming languages and work pretty similar too.

* [Single statement](#single-statement)
* [Block stement](#block-statement)
* [Empty stement](#empty-statement)

## Single statement <a name="single-statement"></a>
What is a **statement**? It is an instruction that commands the computer to perform a specified action. In *Javascript* each expression is a *statement*. Here is a simple statement that prints a greeding to the console:
```javascript
console.log("Hello, world!");
> Hello, world!
```
A semicolon (**;**) character is used to separate different statements. Usually you will specify each statement on a single line. In this case you can even omit semicolon. *Javascript* is a very forgiven language, it will add missed semicolon by its own. 
Try this example:
```javascript
console.log("You do not need to end each statement by semicolon.")
> You do not need to end each statement by semicolon.
```

Other situation when you wish to put multiple statements on one line. In this case you cannot omit semicolon, it will be the only sign for *Javascipt* to distinguish different statements from each other:
```javascript
console.log("First statement."); console.log("Second statement.");
> First statement.
  Second statement.
```
You can also spread a single statement on multiple lines:
```javascript
console.log(1
+ 5);
> 6
```
Please be accurate using this technique, sometimes you will get a different result from what you have expected:
```javascript
function sum(a, b) {
  return 
    a + b;
}
console.log(sum(2, 3));  
> undefined
```
This happens because *Javascript* is so forgiven and is trying to fix user input errors. As it parses code line by line - it first finds single `return` keyword without semicolon at the end. For *Javascipt* it's a valid statement, it just adds semicolon at the end, executes this statement and proceed with the next line of code. As a result we see `undefined` in console instead of `5`.

> It's considered the best practice to always put each statement of a single line and end it with semicolon.

## Block statement <a name="block-statement"></a>
You can also group several statements in a **block statement** by inclosing set of instructions in curly braces, **{ }**:
```javascript
{
  console.log("This is a block."); 
  console.log("of several statement.");
}
> This is a block.
  of several statement.
```
THe *Block statement* can even have a zero number of statements, it's a valid statement too:
```javascript
{
}
```

The *block statement* is commonly used with control flow statements or loops, it allows to specify several statements in place where only one statement is allowed by *Javascript* language.

> Note that the block statement does not end with a semicolon. If you will put it there, *Javascipt* will consider it as an [Empty statement](#empty-statement).

## Empty statement <a name="empty-statement"></a>
An **empty statement** is used to provide no statement where statement is required by *Javascipt* language. Consider the following example where user don't want to execute any statement if `condition` is true but do provide statement when `condition` is false:
```javascipt
if(5 != 5) 
;
else 
  console.log("5 equals 5");
> 5 equals 5
```
Note, it's always a good idea to comment intentional usage of *empty statement* to make it more obvious. Sometimes it's not so obvious to distinguish this stamement from semicolon ending another statement:
```javascipt
if(5 != 5) ;
  console.log("5 equals 5");
> 5 equals 5
```
