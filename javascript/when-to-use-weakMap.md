# use case

WeakMap enables to store objects and make them loose when the garbage collector is working.
Map has strong references, meaning if we store an object on it, strong reference will block GC to work.

Let's say I'm using an API that gives me a certain object:

var obj = getObjectFromLibrary();
Now, I have a method that uses the object:

```js
function useObj(obj) {
  doSomethingWith(obj);
}
```

I want to keep track of how many times the method was called with a certain object and report if it happens more than N times. Naively one would think to use a Map:

```js
var map = new Map(); // maps can have object keys
function useObj(obj) {
  doSomethingWith(obj);
  var called = map.get(obj) || 0;
  called++; // called one more time
  if (called > 10) report(); // Report called more than 10 times
  map.set(obj, called); // setting up strong reference thus, it causes memory leaks as the GC does not know what to collect
}
```

This works, but it has a memory leak - we now keep track of every single library object passed to the function which keeps the library objects from ever being garbage collected. Instead - we can use a WeakMap:

```js
var map = new WeakMap(); // create a weak map
function useObj(obj) {
  doSomethingWith(obj);
  var called = map.get(obj) || 0;
  called++; // called one more time
  if (called > 10) report(); // Report called more than 10 times
  map.set(obj, called);
}
```

https://stackoverflow.com/questions/29413222/what-are-the-actual-uses-of-es6-weakmap
