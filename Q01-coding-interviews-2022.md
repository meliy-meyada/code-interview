# Question 1
Assuming http://codequiz.example.net/data returns an object {data: 10}.Below function doesn't work correctly.
```js,
function thisIsSyncFunction() {
 let result = 0;
 fetch('https://codequiz.example.net/data').then(res => res.json()).then((response) => {
  result = response.data;
});
 return result;
}
const number1 = thisIsSyneFunction()
const calculation = number1 * 10;
console.log(calculation);
```

### Answer 
The function ``thisIsSyncFunction`` doesn't work correctly because it is attempting to return ``result`` before the value of ``result`` has been set. The ``fetch`` function is asynchronous, meaning that the code in the ``then`` block will not be executed until the response is received from the server, which may take some time.

To fix this issue, you can either make the function asynchronous by using the ``async`` and ``await`` keywords, or you can use a callback function to handle the result of the fetch call.

Here's an example of how you could rewrite the function using ``async`` and ``await``:

```js,
async function thisIsSyncFunction() {
  let result = 0;
  const res = await fetch('https://codequiz.example.net/data');
  const response = await res.json();
  result = response.data;
  return result;
}

const number1 = await thisIsSyneFunction();
const calculation = number1 * 10;
console.log(calculation);
```

> Note that the ``thisIsSyncFunction`` function must be marked as ``async`` and the call to ``thisIsSyncFunction`` must be preceded by the ``await`` keyword in order for this approach to work.

> Alternatively, you could use a callback function to handle the result of the ``fetch`` call:

```js,
function thisIsSyncFunction(callback) {
  fetch('https://codequiz.example.net/data').then(res => res.json()).then((response) => {
    callback(response.data);
  });
}

thisIsSyncFunction((number1) => {
  const calculation = number1 * 10;
  console.log(calculation);
});
```
This way, the callback function will be executed once the value of ``number1`` has been determined.

## Question 1.1
Please correct the code, so it really prints out the expected result (100). You can fix it anyway you like but it still has to call fetch as the source of data.

### Answer 
Here's one way you could rewrite the function to correctly print out the expected result of 100:
```js,
async function thisIsSyncFunction() {
  let result = 0;
  const res = await fetch('https://codequiz.example.net/data');
  const response = await res.json();
  result = response.data;
  return result;
}

async function main() {
  const number1 = await thisIsSyncFunction();
  const calculation = number1 * 10;
  console.log(calculation);
}

main();
```
This approach uses the ``async`` and ``await`` keywords to make the ``thisIsSyncFunction`` function asynchronous, and ``then`` calls the function inside an ``async`` function called ``main``. The ``main`` function is ``then`` called, which allows the ``await`` keyword to be used to wait for the ``result`` of the ``thisIsSyncFunction`` call before performing the ``calculation`` and logging the ``result``.

## Question 1.2
Is there a way to make thisIsSync Function really synchronous, so number has the value 10 before it is used for the calculation on the next line.

### Answer 
It is not possible to make the ``fetch`` function synchronous, as it is designed to be asynchronous and makes an HTTP request to a server, which takes time.

However, if you want to ensure that the value of ``number1`` is set before it is used in the calculation, you can use the ``async`` and ``await`` keywords to pause the execution of the code until the value of ``number1`` has been determined.

Here's an example of how you could rewrite the function to use ``async`` and ``await``:
```js,
async function thisIsSyncFunction() {
  let result = 0;
  const res = await fetch('https://codequiz.example.net/data');
  const response = await res.json();
  result = response.data;
  return result;
}

async function main() {
  const number1 = await thisIsSyncFunction();
  const calculation = number1 * 10;
  console.log(calculation);
}

main();
```
This way, the code will wait for the result of the fetch call before proceeding with the calculation.
