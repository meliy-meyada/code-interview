# Question 1
Assuming http://codequiz.azurewebsites.net/data returns an object {data: 10}.Below function doesn't work correctly.
```js,
function thisIsSyncFunction() {
 let result = 0;
 fetch('https://codequiz.azurewebsites.net/data').then(res => res.json()).then((response) => {
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
  const res = await fetch('https://codequiz.azurewebsites.net/data');
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
  fetch('https://codequiz.azurewebsites.net/data').then(res => res.json()).then((response) => {
    callback(response.data);
  });
}

thisIsSyncFunction((number1) => {
  const calculation = number1 * 10;
  console.log(calculation);
});
```
