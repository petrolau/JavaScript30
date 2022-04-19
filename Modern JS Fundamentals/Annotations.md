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
