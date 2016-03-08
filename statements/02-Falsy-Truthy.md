#Falsy/Truthy
In *Javascript* you can use not only *boolean* values in condition place but any expression that you wish. It can be value of any primitive or object type, or even assignment statement. As soon as expression returns a value you can use it as a `condition` for *if-else statement*.

How will different values be considered in place of condition? If value is considered to be **Falsy** then `condition` will be 'false', otherwise - `condition` will be 'true'. But what does it mean *Falsy*?

In *Javascipt* the following values are considered to evaluate to `false` in place where boolean value should take place:
* false
* null
* underfined
* ''
* 0
* NaN

Let's see an example:
```javascript
if(false) console.log("false is not a 'falsy' value.");
if(null) console.log("null is not a 'falsy' value.");
if(undefined) console.log("undefined is not a 'falsy' value.");
if('') console.log("'' is not a 'falsy' value.");
if(0) console.log("0 is not a 'falsy' value.");
if(NaN) console.log("NaN is not a 'falsy' value.");
```
Any other values are considered to be **Truthy**. But be accurate with `Boolean` object values:
```javascript
var b = new Boolean(false);
if(b) console.log("new Boolean(false) is not a 'falsy' value.");

> "new Boolean(false) is not a 'falsy' value."
```
As you can see `new Boolean(false)` is evaluated to *Truthy* because any instance on any object type is considered to be *Truthy*, even if it's an instance of `Boolean` type. 

Let's now take a look at different assignment statements on `condition` place:
```javascript
var a;
if(a = 10) {
  console.log("Assignment (a = 10) evaluated to true.");
}
> "Assignment evaluated to true."

var a;
if(a = 0) {
  console.log("Assignemnt (a = 0) evaluated to true.");
} else {
  console.log("Assignemnt (a = 0) evaluated to false.");
}
> "Assignemnt (a = 0) evaluated to false."
```
As you can see the statement is evaluated to `true` as long as we assign *truthy* value.

> It's always a good practice to put assignment in additional parentheses to distinguish from `equality operator`.
