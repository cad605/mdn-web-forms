# Sending forms through JavaScript

HTML forms are capable of sending HTTP requests declaratively without the use of
JavaScript: Standard HTML form submission, as described in the previous
section,loads the URL where the data was sent, which means the browser window
navigates with a full page load.

However, JavaScript can be used to access form data and prepare the HTTP request
directly.

This is useful for modern applications such as SPAs and other framework based
applications. This is useful if we wish to send data asynchronously, updating
the parts of the UI that need to show this change, and not load an entire new
document from the server.

## Gaining control of the global interface

Many modern UIs only use HTML forms to collect input from the user, and not for
data submission. When the user tries to send the data, the application takes
control and transmits the data asynchronously in the background, updating only
the parts of the UI that require changes.

Sending arbitrary data asynchronously is generally called AJAX, which stands for
"Asynchronous JavaScript And XML".

There are 3 ways to send form data:

1. Using the `Fetch` API (new API, instead of building an XMLHttpRequest
   manually)
2. Using a standalone `FormData` object.
3. Using `FormData` bound to a `<form>` element.

### The `Fetch` API

The Fetch API provides a JavaScript interface for accessing and manipulating
parts of the HTTP pipeline, such as requests and responses.

Here is an example of a basic `Fetch` usage:

    fetch('http://example.com/movies.json')
      .then(response => response.json())
      .then(data => console.log(data));

The `fetch()` method returns a promise that resolves with a `Response` object.
The `Response` object, in turn, does not directly contain the actual JSON
response body but is instead a representation of the entire HTTP response. So,
to extract the JSON body content from the `Response` object, we use the `json()`
method, which returns a second promise that resolves with the result of parsing
the response body text as JSON.

Here is a detailed example of `fetch()` in action:

    // Example POST method implementation:
    async function postData(url = '', data = {}) {
      // Default options are marked with *
      const response = await fetch(url, {
        method: 'POST', // *GET, POST, PUT, DELETE, etc.
        mode: 'cors', // no-cors, *cors, same-origin
        cache: 'no-cache', // *default, no-cache, reload, force-cache, only-if-cached
        credentials: 'same-origin', // include, *same-origin, omit
        headers: {
          'Content-Type': 'application/json'
          // 'Content-Type': 'application/x-www-form-urlencoded',
        },
        redirect: 'follow', // manual, *follow, error
        referrerPolicy: 'no-referrer', // no-referrer, *no-referrer-when-downgrade, origin, origin-when-cross-origin, same-origin, strict-origin, strict-origin-when-cross-origin, unsafe-url
        body: JSON.stringify(data) // body data type must match "Content-Type" header
      });
      return response.json(); // parses JSON response into native JavaScript objects
    }

    postData('https://example.com/answer', { answer: 42 })
      .then(data => {
        console.log(data); // JSON data parsed by `data.json()` call
      });
