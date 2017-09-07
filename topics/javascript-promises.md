# Javascript Promises

## What is a Promise in Javascript?

EcmaScript 6 (or ES6) has brought a ton of new functionality to Javascript. Along with the several improvements and features came something called __Promises__. The concept of promises can be tricky, but they are not completly unlike promises in real life. This document wouldm't be complete without _atleast_ one good analogy, so here goes. 

### Think about buying a house:

1. First you decide what house you would like to buy.
2. Then you go to the bank and get approved.
3. You then take your approval and purchase your house.
4. After you have negotiated the money changes hands and you move in, right?

Now, when you get your approval you don't actually have any money, what you have is a __Contract__ or a __Promise__ that you can use to negotiate or perform an action. This is how a promise in JavaScript works. You write code that performs an action based on the _possible future availability or unavailabilty_ of something, usually data. 

### Here's a code example of a promise, and the Fetch API to load some Asynchronous data from a url.


```javascript
let promise = fetch(url);

promise.then(function(response) {
        return response.json();
    }).then(processData).catch(function(error){
        console.log(error);
    });
```



#### Let's deconstruct what's going on above.

```javascript
let promise = fetch(url);
```
First we declared our variable that will hold our promise and we give it the value we returned from `fetch(url)`.
Fetch will request information from the url and that request will either succeed (_fulfulled_) or fail (_rejected_). So, now the promise is going to decide to do one of two things. 
#### Fullfillment will run this code
```javascript
promise.then(function(response){
    return response.json();
}).then(processData)...
```
Remember promise either succeeded or failed, essentially. So the promise will succeed `.then` run the call back function and pass in the `response` value from `fetch(url)`. This response is then converted into json using the `.json()` method. `.then` we call the function `processData` to perform an actions we need to with the data.
#### Failure, in all its beauty.
```javascript
.catch(function(error){
    console.log(error);
    //what ever else you want.
})
```
This is something special. Promises come with their own error handling. `.catch` runs as soon as an error occurs in any portion of the promise and a call back function runs with the `error` passed in and some action can be performed.