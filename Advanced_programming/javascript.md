## JavaScript

- Side funktionalitet - imperativt

- can
  - change all the HTML elements in the page
  - change all the HTML attributes in the page
  - change all the CSS styles in the page
  - remove existing HTML elements and attributes
  - add new HTML elements and attributes
  - react to all existing HTML events in the page
  - create new HTML events in the page

###  JavaScript vs Java

- Casual og tilgivende - i modsætning til Java
- Syntax linger Java, men går meget anderledes
- Browser vs JVM
- Typersvagt og dynamisk vs Typestærk og statisk
- funktioner er variable
- Object-orientering
  - **Java** - strengt objektorienteret. Funktioner skal være i en klasse (metoder og felter)
  - **JavaScript** - Afslappet. Funktioner og variable kan defineres i global scope. Prototyper, men klasser kommet med senere

### Creating objects i Javascript 

#### POJO ( object literal  )

- Plain Old JavaScript Object

```javascript
var obj = { // using brackets syntactic sugar also know as object literal
    a : "SomeString",
    b : function(){
        // some code
    }
}; 
var obj = new Object();  // using the Object() constructor
```

##### Object Literal vs JSON

- Object Literal is simplest way to create javascript object

```javascript
var perons = {
    firstName: "josh",
    lastname: "don"
};
```

- JSON, on the other hand is widely used as language independent data transfer format between computer systems
- JSON is language independent, althought syntax, borrowing simplicity from Javascipt

```javascript
{
    "firstname": "josh",
    "lastname" : "don"
}
```

- If you create an object using JSON format, javascript engine treats it the same as you would have created the object using the object literal. Safe to say that all JSON data are valid Javascript object.
- Javascript has built-in support for conversion between JSON and javascript object. To convert an object ‘obj’ to a JSON data, you can use `JSON.stringify(obj)`. To create javascript object from JSON data ‘data1’, you can use `JSON.parse(data1)`

[Reference](https://medium.com/@easyexpresssoft/object-literal-vs-json-7a2084872907)


#### Other Than Plain Object

```javascript
var Obj = function(name){ // using function constructor
	this.name = name;
}
var c = new Obj("hello");
```

```javascript
class myObject {  // using ES6 class syntax
	constructor(name){
		this.name = name
	}
}
var e = new myObject("hello");
```

### Svagt/dynamiske typer

```javascript
var d;
var e;
d = {color : "red", speed : 200}; // object
e = ["Hello", 1, true]; // Array
e = function(arg1, arg2){}; // function
```

### Functioner som argumenter

```javascript
var myfunction = function(arg1, someFunction){
    someFunction("got arguemnt:", arg1);
}
function displayText(text){
    alert(text);
}
myfunction("some text", displayText)
```

