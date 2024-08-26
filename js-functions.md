## Functions

Functions are first–class citizens in JS, meaning that they can be passed around like any other type of data, eg, variables. http://en.wikipedia.org/wiki/First-class_function

### Declared function

Declared functions build in memory immediately when the program loads.

#### Basic syntax
```javascript
function sumOfCubes(a, b) {
  return a*a*a + b*b*b;
}

sumOfCubes(4, 9); // returns 793

// Parameters can also be expressions
sumOfCubes(1+2, 3+5); // returns 539
```

`console.log(myFunction);` will print function body

#### A more complex declared function
```javascript
function countE() {
  var phrase = prompt("Which phrase would you like to examine?");
  if ( typeof(phrase) != "string" ) {
    alert("That's not a valid entry!");
    return false;
  } else {
    var eCount = 0;
    for var index = 0; index < phrase.length; index++ {
      if (prase.charAt(index) == 'e' || phrase.charAt(index) == 'e') {
        eCount++;
      }
    }
    alert("There are " + eCount + " E's in \"" + phrase + "\".");
    return true;
  }
}
```

### Local vs Global Scope

Inside functions the scope is local. Outside of the function the scope is global meaning that variable are potentially accessible everywhere

```javascript
var x = 6; // x is global
var y = 4; // y is global

function add (a, b) { // a and b are local to the function
  var x = a + b;  // x is local b/c declaring w/ var inside a function doesn't
  return x;       // modify same-name variable outside the function.
}

function add (a, b) {
  x = a + b;  // if x is not declared with var, it will shadow the same-name 
  return x;   // variable from the nearest external scope.
}
```


### Function expressions

Function expressions load when it's line of code is reached. 

#### Anonymous function expression
```javascript
var myFunction = function() {
    ...
}; // semi-colon on final bracket
```

#### Function expression as direct parameter

The built-in `map` function will loop through array elements. The following example will take an array of arrays and convert it to 1 dimensional array of strings

```javascript
var peopleNames = [ ["Jonas", "Rogers"], 
                    ["Mel", "Gibson"], 
                    ["Lucy", "Liu"], 
                    ["Edward", "Scissorhands"] ];

var modifiedNames = peopleNames.map(function(arrayCell){
	return arrayCell[0] + " " + arrayCell[1];
});

--> ["Jonas Rogers", "Mel Gibson", "Lucy Liu", "Edward Scissorhands"] 

```
##### Returned Functions
Since a function can be an expression, it can be returned as a value. 

```javascript
function aGoodThing ( chickenShit ) {
	return function ( chickenShit ) {
		alert ("The chicken salad is good today.");
	};
}
```

##### Immediate Invocation
Javascript functions can be invoked without the need to store in a variable. Behold.

```javascript
function makeSandwich (bread, meat, cheese)(); // Need parameter parenthesis and semi–colon to execute
```