It’s rarely used, but in JavaScript you can use a labeled statement to add a label to a for loop. This then allows you to break and interrupt the loop when needed – even from inside another loop.

```js
function loop() {
  dance: for (let i = 0; i < 4; i++) {
    for (let j = 0; j < 4; j++) {
      if (j === 2) {
        break dance;
      }
    }
  }
}
```

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/label?ck_subscriber_id=1001736634

or just

```js
function loop() {
  for (let i = 0; i < 4; i++) {
    for (let j = 0; j < 4; j++) {
      if (j === 2) {
        break;
      }
    }
  }
}
```
