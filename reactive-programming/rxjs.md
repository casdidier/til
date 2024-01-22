# RxJS Primer

## Summary TLDR;

RxJs is like using the concept of push mechanism made of (observable and observers) to facilitate programming mostly based on events, observers react to obersable emits and RxJs has a lot of operators available to handle all the data streams from the sources emitting

## Observable

An observable represents a stream, or source of data that can arrive over time. You can create an observable from nearly anything, but the most common use case in RxJS is from events.

```ts
// import the fromEvent operator
import { fromEvent } from 'rxjs';

// grab button reference
const button = document.getElementById('myButton');

// create an observable of button clicks
const myObservable = fromEvent(button, 'click');
```

## Subscription

Subscriptions are what set everything in motion. You can think of this like a faucet, you have a stream of water ready to be tapped (observable), someone just needs to turn the handle. In the case of observables, that role belongs to the subscriber.
To create a subscription, you call the subscribe method, supplying a function (or object) - also known as an observer. This is where you can decide how to react(-ive programming) to each event. Let's walk through what happens in the previous scenario when a subscription is created:

```ts
// import the fromEvent operator
import { fromEvent } from 'rxjs';

// grab button reference
const button = document.getElementById('myButton');

// create an observable of button clicks
const myObservable = fromEvent(button, 'click');

// for now, let's just log the event on each click
const subscription = myObservable.subscribe((event) => console.log(event));
```

## Operators

Operators offer a way to manipulate values from a source, returning an observable of the transformed values.

```ts
import { of } from 'rxjs';
import { map } from 'rxjs/operators';
/*
 *  'of' allows you to deliver values in a sequence
 *  In this case, it will emit 1,2,3,4,5 in order.
 */
const dataSource = of(1, 2, 3, 4, 5);

// subscribe to our source observable
const subscription = dataSource
  .pipe(
    // add 1 to each emitted value
    map((value) => value + 1)
  )
  // log: 2, 3, 4, 5, 6
  .subscribe((value) => console.log(value));
```

## Pipe

The pipe function is the assembly line from your observable data source through your operators. Just like raw material in a factory goes through a series of stops before it becomes a finished product, source data can pass through a pipe-line of operators where you can manipulate, filter, and transform the data to fit your use case

```ts
// observable of values from a text box, pipe chains operators together
inputValue
  .pipe(
    // wait for a 200ms pause
    debounceTime(200),
    // if the value is the same, ignore
    distinctUntilChanged(),
    // if an updated value comes through while request is still active cancel previous request and 'switch' to new observable
    switchMap((searchTerm) => typeaheadApi.search(searchTerm))
  )
  // create a subscription
  .subscribe((results) => {
    // update the dom
  });
```

### operators categories

There are :

- creator
  allow the creation of an observable from nearly anything

```ts
fromEvent(scrollContainerElement, 'scroll')
  .pipe(
    // we will discuss cleanup strategies like this in future article
    takeUntil(userLeavesArticle)
  )
  .subscribe((event) => {
    // calculate and update DOM
  });
```

- combination
  The combination operators allow the joining of information from multiple observables

```ts
// give me the last emitted value from each source, whenever either source emits
combineLatest(sourceOne, sourceTwo).subscribe(
  ([latestValueFromSourceOne, latestValueFromSourceTwo]) => {
    // perform calculation
  }
);
```

- error handling
  The error handling operators provide effective ways to gracefully handle errors and perform retries, should they occur.

```ts
source
  .pipe(
    mergeMap((value) => {
      return makeRequest(value).pipe(
        catchError(handleErrorByReturningObservable)
      );
    })
  )
  .subscribe((value) => {
    // take action
  });
```

- filtering operators
  operators provide techniques for accepting - or declining - values from an observable source and dealing with backpressure, or the build up of values within a stream.

```ts
source.pipe(take(5)).subscribe((value) => {
  // take action
});
```

### ressources

https://www.learnrxjs.io/learn-rxjs/recipes
examples reviewed:
https://www.learnrxjs.io/learn-rxjs/recipes/type-ahead
