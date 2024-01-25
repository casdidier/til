Ref vs Reactive
There is a lot of discussions out there about when to use what. I find that when working with primitives, always go with ref(). When working with objects, go with reactive()


```js
//When working with primitives like string, numbers etc:
const myName = ref('Nicky')
//When working with objects:
const user = reactive({
  name: 'Nicky',
  age: 37
});
```
