# JavaScript Design Patterns

## Prototype

### Object Constructor

```js
function Superhero(superName, realName, powers) {
  this.superName = superName;
  this.realName = realName;
  this.powers = powers;
}

// create an instance:
const wonderWoman = new Superhero(`Wonder Woman`, `Diana Prince`, `Strength and flight`);

// add property to prototype, not instance:
Superhero.prototype.equipment = `Lasso of truth`;

// wonderWoman does not have that property:
console.log(wonderWoman.hasOwnProperty(`equipment`))
// => false

// neither does the actual Superhero object:
console.log(Superhero.hasOwnProperty(`equipment`));
// => false

// however, the prototype does have it!
console.log(Superhero.prototype.hasOwnProperty(`equipment`));
// => true
```

### Object Creator

```js
// Using an object constructor to establish
// a prototype object to use later:
function Player(name, health) {
  this.name = name;
  this.health = health;
}
// create an instance to be copied:
const defaultPlayer = new Player("Unnamed Player", 100);

// Object.create() uses an existing object's prototype:
const player = Object.create(defaultPlayer);
player.name = "Patrick";
```

### Object Literal

```js
const player = {
  name: "Patrick",
  health: 100
};
```

### Object Shorthand Properties

```js
const name = "Patrick";
const health = 100;

// instead of doing this:
const player = {
  name: name,
  health: health
};

// new shorthand syntax:
const player2 = {
  name,
  health
}

// compare both options:
console.log(player);
console.log(player2);

// { name: "Patrick", health: 100 }
// { name: "Patrick", health: 100 }
```

#### Shorthand Functions

```js
// traditional way:
const player = {
  name: "Patrick",
  attack: function() {
    return "Attacked creatures for 10 dmg";
  }
};

// new optional way 
// (removes the colon and function keyword)
const player2 = {
  name: "Patrick",
  attack() {
    return "Attacked creatures for 10 dmg";
  }
}
```

### ECMAScript Classes

> This is just syntactic suger for function constructor. Classes are still using the prototype under the hood.

```js
class Book {
  constructor(title, author) {
    this.title = title;
    this.author = author;
  }
  
  publicizeBook() {
    return `This book ${this.title} is written by renowned author ${this.author}.`;
  }

  static youMightLight(title, similarTitle) {
    return `If you like ${title}, you might also like ${similarTitle}.`;
  }
}

// create an instance:
const novel = new Book('Moby Dick', 'Herman Melville');

console.log(novel.publicizeBook());
// => "This book Moby Dick is written by renowned author Herman Melville"

console.log(Book.prototype.hasOwnProperty(`publicizeBook`));
// => true

// using the static method, note the use of Book,
// not novel class:
console.log(Book.youMightLike(novel.title, "A Midsummer Night's Dream"));
// => "If you like Moby Dick, you might also like A Midsummer Night's Dream."
```

### Extending Class

```js
class Animal {
  constructor(name) {
    this.name = name;
  }
  speak() {
    console.log(`${this.name} makes a noise!`);
  }
}

class Horse extends Animal {
  constructor(name) {
    super(name);
  }
  speak() {
    console.log(`${this.name} whinnies.`);
  }
}

let thoroughbred = new Horse('Seabiscuit');
console.log(thoroughbred.speak());
// => "Seabiscuit whinnies."
```

-----

## Sources

- [Enhanced Object Literal Value Shorthand: JavaScript ES6 Feature Series (Pt 6)](https://itnext.io/enhanced-object-literal-value-shorthand-javascript-es6-feature-series-pt-6-e00dfdc24f64)
- [Classes and Inheritance: JavaScript ES6 Feature Series (Pt 8)](https://itnext.io/classes-and-inheritance-javascript-es6-feature-series-part-8-4a81fa3adf0f)
