# Object-Oriented JavaScript (OOJS)

## What is Object-Oriented Programming?

Object-oriented programming (or OOP) is a paradigm or pattern of programming whereby the solution to a programming problem is modelled as a collection of collaborating objects.

An object is an entity that possesses both state (or properties or attributes) and behaviour. Put another way, an object encapsulates data and the functions that operate on that data. The data is usually hidden from other objects so that the only way to affect the data is through the object’s functions (or methods)

- [Medium.com - What is Object-Oriented Programming](https://medium.com/learn-how-to-program/chapter-3-what-is-object-oriented-programming-d0a6ec0a7615)
- [Medium.com - A Simple Explanation of OOP](https://medium.com/@richardeng/a-simple-explanation-of-oop-46a156581214)
- [freeCodeCamp.com - How to explain object-oriented programming concepts to a 6-year-old](https://medium.freecodecamp.org/object-oriented-programming-concepts-21bb035f7260)
- [Video - Object-Oriented Programming in 7 Minutes](https://youtu.be/pTB0EiLXUC8)

## Ways to create Objects in JavaScript

- Object Literal
- Function ([Factory Pattern](http://www.javascripttutorial.net/create-objects-in-javascript/#factory_pattern))
- [Constructor Function](http://www.javascripttutorial.net/create-objects-in-javascript/#constructor_pattern)
- [Constructor & Prototype Pattern](http://www.javascripttutorial.net/create-objects-in-javascript/#constructor_prototype_pattern)
- [ES6 Class](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)

### Object Literal

```
let coco = {
  name: "Coco",
  age: 10,
  makeNoise: () => {
    console.log('UhhUhhUhh')
  }
};

let ophelia =   {
  name: "Ophelia",
  age: 6,
  makeNoise: () => {
    console.log('Meooow')
  }
};

let tweety =   {
  name: "Tweety",
  age: 7,
  makeNoise: () => {
    console.log('Chirp Chirp')
  }
};
```

#### Downsides:

- A lot of duplication (keys) = Not DRY
- If you change one object's methods you have to change it on all objects to achieve same functionality

### Function

```
function createAnimal(name, age, noise) {
  var obj = {};
  obj.name = name;
  obj.age = age;
  obj.noise = noise;
  obj.makeNoise = function() {
   console.log(noise)
  };
  return obj;
}

let coco = createAnimal('Coco', 10, 'UhhUhhUhh');
let ophelia = createAnimal('Ophelia', 6, 'Meooow');
let tweety = createAnimal('Tweety', 7, 'Chirp Chirp');
```

#### Upsides:

- Less duplication

#### Downsides:

- Have to create empty object first
- Have to return object
- Methods are still not shared across all objects

### Constructor Function

```
// Convention is to uppercase first letter of constructor function
function Animal(name, age, noise) {
  this.name = name;
  this.age = age;
  this.noise = noise;
  this.makeNoise = function() {
   console.log(this.noise)
  };
}

// "new" Keyword
let coco = new Animal('Coco', 10, 'UhhUhhUhh');
let ophelia = new Animal('Ophelia', 6, 'Meooow');
let tweety = new Animal('Tweety', 7, 'Chirp Chirp');
```

#### Upsides:

- Even less duplication

#### Downsides:

- Methods are still duplicated across all objects

### Constructor & Prototype Pattern

This is the most common used pattern before ES6 class syntax came around.

```
function Animal(name, age, noise) {
  this.name = name;
  this.age = age;
  this.noise = noise;
}

// Methods are moved outside of constructor onto the "prototype" object

Animal.prototype.makeNoise = function() {
  console.log(this.noise);
}

// Instantiation stays the same with "new" Keyword
let coco = new Animal('Coco', 10, 'UhhUhhUhh');

...
```

### ES6 Class

The latest and greatest...

```
class Animal(name, age, noise) {
  constructor {
    this.name = name;
    this.age = age;
    this.noise = noise;
  }

  // method within class
  makeNoise() {
    console.log(this.noise);
  }
}


// Instantiation still the same with "new" Keyword
let coco = new Animal('Coco', 10, 'UhhUhhUhh');

...
```
