# how to optimize rendering of components ?

## use v-once

skip futures updates if value is the same on re-renders

```html
<!-- single element -->
<span v-once>This will never change: {{msg}}</span>
<!-- the element have children -->
<div v-once>
  <h1>comment</h1>
  <p>{{msg}}</p>
</div>
<!-- component -->
<MyComponent v-once :comment="msg"></MyComponent>
<!-- `v-for` directive -->
<ul>
  <li v-for="i in list" v-once>{{i}}</li>
</ul>
```

https://vuejs.org/api/built-in-directives.html#v-once