# async component

In large applications, we may need to divide the app into smaller chunks and only load a component from the server when it's needed. To make that possible, Vue has a defineAsyncComponent function:

```ts
const AsyncComp = defineAsyncComponent({
  // the loader function
  loader: () => import('./Foo.vue'),

  // A component to use while the async component is loading
  loadingComponent: LoadingComponent,
  // Delay before showing the loading component. Default: 200ms.
  delay: 200,

  // A component to use if the load fails
  errorComponent: ErrorComponent,
  // The error component will be displayed if a timeout is
  // provided and exceeded. Default: Infinity.
  timeout: 3000
})
```

https://vuejs.org/guide/components/async
https://www.youtube.com/watch?v=muaBCsVE-NM&list=PLC2LZCNWKL9aOR9Hgj05jbKItS0GEg3On&index=8