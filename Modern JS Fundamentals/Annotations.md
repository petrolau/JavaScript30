# ES6 JavaScript Annotations

## Var and Let

- var is accessible inside of the function in which it was defined.
  **Scoped to the function.**

- let is accessible in the block in which it was defined. **Block scoped.** Suggested to use only when you need to reasign a value.

- const is accessible in the block in which it was defined. **Block scoped.**

## Objects

```
const person = {
    name: 'Mosh',
    walk() {},
    talk(){}
};

// accessing the name property from person.
person['name']

const targetMember = 'name';
person[targetMember.value] = 'John';
```

**This** keyword

```
const person = {
    name:"Mosh",
    walk() {
        console.log(this);
    };
};

// returns a reference to the person object
person.walk();


// getting a reference to the walk() function.
const walk = person.walk;
// returns undefined. why?
walk();

```

This situation happened because of the 'this' keyword. If it _called a function as a method in an object_, **this will always return a reference to that object.**
However, if you call a function as a _standalone object_, or outside of an object, **this will return the global object, which is the window object in browsers. And, if the strict mode is enabled, this will return UNDEFINED.**

**Every function in JavaScript is an Object.** One of the most important methods is BIND, with this method, we can set a value of the object permanently. The argument of **This** is based/attached on the argument of the method.

```
// with the instatiation, the problem is fixed.
const walk = person.walk.bind(person);
walk();
```

## Arrow Functions

```
const square = (number) => {
    return number*number;
};
```

Something you need to know about arrow functions is that they dont rebind **This**.

```
const person = {
    talk(){
        setTimeout(() => {
            console.log("this",this);
        },1000);
    };
};

person.talk();
```

## Map

```
const colors = ['red','green','blue'];

// introducing template literals (using html) and the map function.
const items = colors.map(color => {
    return `<li> ${color}</li>`;
});
console.log(items);
```

Used to render lists.

## Object Destructuring

```
const address = {
    street: '',
    city: '',
    country: ''
};

//destructuring syntax
const {street: st, city: ci, country: cou} = address;

// which basically is equivalent to:

const street = address.street;
const city = address.city;
const country = address.country;


```

## Spread Operator

```
const first = [1,2,3];
const second = [4,5,6];

// we get a new array with all the items from the first array, then we have 'a', all the elements from the second array, and then 'b'.
const combined = [...first, 'a', ...second, 'b']
```

Used to easily clone an array.
