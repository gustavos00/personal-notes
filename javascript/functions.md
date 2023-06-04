# Functions vs Arrow Functions

## How they are declared?

- #### Function

```javascript
function mockedFunction() {}
```

- #### Arrow Function

```javascript
const mockedArrowFunction = () => {};
```

## This

### What are the differences?

- #### Function

  The functions have their own **this**.

- #### Arrow Function
  The arrow functions have the **this** of the scope where they were created.

## What is 'this'?

**This** is the value of the function, being able to set some properties on him.

### Practical cases

- #### Function

  ```javascript
  function mockedFunction() {
    this.name = "Gustavo";
  }
  ```

  In this case, when I am using **this**, the function will be converted to a function with a constructer (and this can be proved by calling the function with a **new**. PE: `new mockedFunction()`.).
  By assigning a property to this object, the function's return will become an object of type `mockedFunction` with the value of the declared property.

  ```javascript
  function mockedFunction() {
    this.name = "Gustavo";
  }

  console.log(new mockedFunction()); // mockedFunction { name: "Gustavo" }
  ```

- #### Arrow Function

  An example of how we can confirm what I am saying... For this, we will need to use our browser and use the console on the inspect tab.  
  If you just print the **this** you will that the **this** is the object **window**. So, if you create an arrow function and access the **this** inside it, you will be accessing the object window.

  ```javascript
  console.log(this); //Will return the same data of the object window.

  const mockedArrowFunction = () => {
    this.name = "Gustavo";
  };

  mockedArrowFunction();
  console.log(this.name); //Gustavo
  ```

---

## Params

Besides the `this`, the arrow functions work differently related with the normal functions.

Let's assume that you have a plus function and you want to receive an unknown number of parameters.  
How would you do it? Well, you have some options.

### Use the reserved word "`Arguments`"

#### Important

This just can be used when you are declaring it as a function and **not** as an arrow function.

> Why?

Because the `arguments` have the same behavior as `this`. When you are accessing it on an arrow function, it will inherit the arguments of its scope.

```javascript
function plus() {
  console.log(arguments);
  /* You will receive an object with the value of the arguments _and some trash_
    {
        "0": 1,
        "1": 2,
        "2": 3,
        "3": 4,
        "4": 5,
        "5": 6,
        "6": 7
    } 
  */
}

plus(1, 2, 3, 4, 5, 6, 7);
```

To clear this trash that comes with the `arguments` reserved word, you can use the `Object.values` method. With this, you will have an array of `arguments`.

```javascript
function plus() {
  console.log(Object.values(arguments)); // [1, 2, 3, 4, 5, 6, 7]
}

plus(1, 2, 3, 4, 5, 6, 7);
```

### Or just use an ellipsis...

You can avoid over-complicating things by just using ellipsis.

```javascript
function plus(...someArguments) {
  console.log(someArguments); // [1, 2, 3, 4, 5, 6, 7]
}

plus(1, 2, 3, 4, 5, 6, 7);
```
