# Sending form data

These notes provide details around where the data goes after a user submits a
form and how we can handle such interactions, as well as security concerns.

## Client-Server Architecture

A client sends a request to a server at an address provided using HTTP. The
server then responds back to the client, also using HTTP.

An HTML form can be thought of as a convient way to format an HTTP request, with
attributes such as `method` and `action` being APIs to configure this request.

## Client-side

### The `action` attribute

The `action` attribute details where the data is sent. Using HTTPS as the
protocol for the URL provided to this attribute will encrypt the data before
sending to the server.

A map of key-value pairs using the names and values of the form controls are
sent to the server, which is responsible for handling the request and returing a
response to the client.

### The `method` attribute

The `method` attribute defines the HTTP method used to send the data to the
server. The two most common are HTTP `GET` and HTTP `POST`.

#### The `GET` request

This request asks the server to return a resource to the client. The form data
is appended to the URL as a series of key-value pairs separated by ampersands.

#### The `POST` request

This request asks the server to mutate data using the form data sent, and return
a response that takes this new data into account. The data is not appended to
the URL, like in GET, but instead included in the request `body`: The
Content-Length header indicates the size of the body, and the Content-Type
header indicates the type of resource sent to the server.

## Server-side

Whichever HTTP method you choose, the server receives a string that will be
parsed in order to get the data as a list of key/value pairs.

Check out any of the following server-side frameworks:

1. Django for Python (a bit more heavyweight than Flask, but with more tools and
   options).
2. Express for Node.js.
3. Laravel for PHP.
4. Ruby On Rails for Ruby.
5. Spring Boot for Java.

## A special case: sending files

HTTP is a text protocol; thus we have to treat binary data such as files
differently.

### The enctype attribute

This attribute lets you specify the value of the Content-Type HTTP header
included in the request generated when the form is submitted.

The following steps are required to configure a form to correctly send file
data:

1. Set the `method` attribute to POST because file content can't be put inside
   URL parameters.
2. Set the value of `enctype` to multipart/form-data because the data will be
   split into multiple parts, one for each file plus one for the text data
   included in the form body (if text is also entered into the form).
3. Include one or more `<input type="file">` controls to allow your users to
   select the file(s) that will be uploaded.
