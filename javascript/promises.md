# Promises

## What it is?

A promise is an object that represents the eventual completion or failure of an asynchronous operation and its resulting value.

They can have 3 states

- **Pending** - It is the initial state when the promise is created.
- **Completed** - It will be the state when the promise is **successfully** completed.
- **Rejected** - It will be the state where the promise encounters an error or failure.

## How they are declared?

A promise can be declared by doing this:

```javascript
  const apiCAll = new Promise((resolve, reject) => {
    ...
  })
```

> How we can force the promise to have the all 3 states that you mention?

Well, the **pending state** is already enforced, since is the default value.
For the other ones, you can force them by using the **resolve** or **reject** function that came as a parameter.

- **resolve** - Used to say that the promise occurs successfully.
- **reject** - Used to say that occurs some failure or error in the promise.

## Practical Cases

#### Completed state

```javascript
const apiCAll = new Promise((resolve, reject) => {
  resolve("Success!");
});

console.log(apiCall); // promise { "Success!" }
```

#### Reject state

How to handle a Promise?
So, let's assume that you are fetching an API or something that might take some time.

```javascript
const apiCAll = new Promise((resolve, reject) => {
  setTimeout(() => resolve("Success!"), 2000);
});

console.log(apiCall); // promise { pending }
```

> But wait, it shouldn't return the success message?

Well, no. Because we are not waiting for the promise to finish.

### .then/.catch

The promise will run the **.then/**.catch** as if they were the **resolve** or **reject** method.
Because of this, we can access the parameter that we are sending to the **resolve** or **reject** method on the **.then**/**.catch\*\* methods.

```javascript
// Example 1 - resolve
const apiCAll = new Promise((resolve, reject) => {
  setTimeout(() => resolve("Success!"), 2000);
});

apiCall.catch((message) => {
  console.log(message); // Success!
});

// Example 1 - reject

const apiCAll = new Promise((resolve, reject) => {
  setTimeout(() => reject("Error!"), 2000);
});

apiCall.catch((message) => {
  console.log(message); // Error!
});
```

#### .then

We can handle promises using the **.then**/**.catch**, but how?

```javascript
const apiCAll = new Promise((resolve, reject) => {
  setTimeout(() => resolve("Success!"), 2000);
});

apiCall.then(() => console.log(apiCall)); // promise { 'Success!' }
```

#### .catch

The catch is the error handler of the promise. In practical terms, if anything through an error during the **.then**, it will go to **.catch**.

```javascript
const apiCAll = new Promise((resolve, reject) => {
  setTimeout(() => reject("Error!"), 2000);
});

apiCall
  .then(() => {
    console.log(apiCall); // Will not be showed.
  })
  .catch(() => {
    console.log("Error"); // Will be showed.
  });
```

### async & await

When you use the await, the Javascript will keep this promise blocked on the call stack while this promise is not finished.
However, **we just can use the async & await on a function.**

```javascript
const apiCAll = new Promise((resolve, reject) => {
  setTimeout(() => resolve("Success!"), 2000);
});

const response = await apiCall();
console.log(response); // Throw error because we are not inside a function.
```

```javascript
const apiCAll = new Promise((resolve, reject) => {
  setTimeout(() => resolve("Success!"), 2000);
});

async function run {
  const response = await apiCall();
  console.log(response); // Prints "Success!" after 2 seconds.
}

run()
```

> Since we are without the .catch, how we can handle errors?

Well, we would need to use the try & catch to handle errors.

```javascript
const apiCAll = new Promise((resolve, reject) => {
  setTimeout(() => reject("Success!"), 2000);
});

async function run {
  try {
    const response = await apiCall();
    console.log(response); // Will not be printed.
  } catch(error) {
    console.log(error); // Will be printed with Error! message.
  }

}

run()
```

### What is the difference between the try & catch and the .then/.catch

So, the try and catch will block your code to run while the .then/.catch will run in parallel.
