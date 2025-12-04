# Asynchronous JavaScript

## Callbacks:
   
- Callback is a function passed as an argument to the another function.

- Callback function can run after another function has finished.

```javascript
function sayHello(name){
console.log("Hello " + name);
}

function greet(callback){
callback("Everyone!");
}
greet(sayHello);
```

### Problems:

- Deeply nested code.

- Difficult to handle errors consistently.

- Hard to read and maintain.

### Solution:

Use Promises or async/await to flatten the code and make it more readable.


## Promises
Promise is a JavaScript object that represents the result of an asynchronous operation, which will either succeed (resolve) or fail (reject) in the future. 
- It can be in one of three states:

**1. Pending**

**2. Fulfilled**

**3. Rejected**


```javascript
function fetchData() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            const success = true;
            if (success) {
                resolve("Data fetched successfully!");
            } else {
                reject("Error fetching data");
            }
        }, 2000);
    });
}

fetchData.then((message) => {
   console.log(message); // Data fetched successfully!
}).catch((error) => {
   console.error(error);
});
```

## Promise functions

**1. Promise.resolve()**

**2. Promise.reject()**

**3. Promise.all()**

**4. Promise.allSettled()**

**5. Promise.any()**

**6. Promise.race()**


## Event loop

The event loop continuously checks whether the callstack is empty and if it is, it pushes pending callbacks (from queues) into the stack so they can run.

**Call stack:** Executes functions one at a time

**Web APIs:** Handle asynchronous tasks

**Callback Queue:** Stores asynchronous callbacks

**Event loop:** Pushes callbacks to stack when free


## Synchronous vs Asynchronous

### Synchronous:
- Synchronous tasks runs one after another.
- Slower for long task takes time
- Blocks the code until the task finishes.

```javascript
console.log("1"); // 1
console.log("2"); // 2
console.log("3"); // 3
```

### Asynchronous:
- Asynchronous tasks runs without waiting.
- Faster and more efficient.
- Non-blocking code continues running.

```javascript
console.log("Start");

setTimeout(() => {
  console.log("This runs later");
}, 2000);

console.log("End");
```
