# AJAX

Asynchronous Javascript and XML is somewhat of a misnomer these days as XML is rarely used in modern APIs. Instead you can think of AJAX as a means to asynchronously pull in external resources. These can include data from APIs and services or even local files.

## XML Http Request

The traditional method of connecting to an exteral resource with AJAX is through a [XML Http Request](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest), also known as a XHR request. The process involves setting up the request, opening the connection, handling events, and sending the request. A `GET` request might look like:

```js
// Instantiate new instance of XHR object
const request = new XMLHttpRequest()

// Build our query string
//

const url = "https://path.to.resource"

// Open the request, passing in the type(string: GET, POST, PUT, DELETE), url(string), and whether or not to be ASYNC or not(boolean).
request.open("GET", url, true)

// Listen for onload event.
request.onload = function() {
  // Check for success status codes
  if (request.status >= 200 && request.status < 400) {
    // Parse our Data from JSON (if needed)
    const data = JSON.parse(request.responseText)
    // Do something with the data
    console.log(data)
  } else {
    // Code for Response Errors
    console.log("response error", request)
  }
}

// Listen for connection errors
request.onerror = function() {
  // Code for Connection Errors
  console.log("connection error")
}

// Fire off the request
request.send()
```

## Fetch

While XHR is still a commonly used vanilla js technique, support for the [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API) is universal amungst modern browser.

```js
var url = 'https://path.to.resource'

fetch(url)
// It is common to move each "then" to a new line and indent it.

  // Parse our response to a format we can work with. In this case, we'll pretend the response is json
  .then( response => response.json())

  // Do something with our Data
  .then( responseAsJson => {
    console.log(responseAsJson)
  })
  .catch( error => {
    console.log('An Error Occurred:', error)
  })
```

## Options and Advanced Implementations

In some instances you may need to perform a request with options such as headers, data, and authorization. 

In an XHR request, options are applied to the request itself via specific methods. For example, a header can be applied like so:

```js
...
request.setRequestHeader("Content-Type", "text/plain");
...
```

With Fetch, this is done in an options object that is then passed into the fetch request.

```js
const options = {
  method: 'GET',
  headers: new Headers({
    "Content-Type": "text/plain"
  })
}

fetch(url, options).then((response) => {
 ...
})

```

## Additional Resources and Reading

- [Getting Started - Ajax | MDN](https://developer.mozilla.org/en-US/docs/AJAX/Getting_Started)
- [Using Fetch - Web APIs | MDN](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch)
- [Fetch Standard](https://fetch.spec.whatwg.org/)
- [Using Fetch | CSS-Tricks](https://css-tricks.com/using-fetch/)