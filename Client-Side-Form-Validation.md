# Client-side form validation

When you enter data, the browser and/or the web server will check to see that
the data is in the correct format and within the constraints set by the
application.

There are two main ways to implement form-validaton:

1. Built-in form validation using HTML5 validation features
2. JavaScript validation

## HTML5 validation features

Useful validation attributes include the following:

1. required: Specifies whether a form field needs to be filled in before the
   form can be submitted.
2. minlength and maxlength: Specifies the minimum and maximum length of textual
   data (strings)
3. min and max: Specifies the minimum and maximum values of numerical input
   types
4. type: Specifies whether the data needs to be a number, an email address, or
   some other specific preset type.
5. pattern: Specifies a regular expression that defines a pattern the entered
   data needs to follow.

The `:valid` and `:invalid` CSS pseudo-classes are matched to the corresponding
form controls, allowing us to style the controls appropriately. The form will
not submit and display an error message if a form control is invalid.

## Validating using JavaScript

You must use JavaScript if you want to take control over the look and feel of
native error messages or to deal with legacy browsers that do not support HTML's
built-in form validation.

### The Constraint Validation API

This API provides a number of methods on multiple DOM elements:

1. HTMLButtonElement (represents a `<button>` element)
2. HTMLFieldSetElement (represents a `<fieldset>` element)
3. HTMLInputElement (represents an `<input>` element)
4. HTMLOutputElement (represents an `<output>` element)
5. HTMLSelectElement (represents a `<select>` element)
6. HTMLTextAreaElement (represents a `<textarea>` element)

It makes the following properties available on the above elements:

1. validationMessage: Returns a localized message describing the validation
   constraints that the control doesn't satisfy (if any). If the control is not
   a candidate for constraint validation (willValidate is false) or the
   element's value satisfies its constraints (is valid), this will return an
   empty string.
2. validity: Returns a ValidityState object that contains several properties
   describing the validity state of the element.

And it makes the following methods available on the form and form elements:

1. checkValidity(): Returns true if the element's value has no validity
   problems; false otherwise. If the element is invalid, this method also fires
   an invalid event on the element.
2. reportValidity(): Reports invalid field(s) using events. Useful in
   combination with preventDefault() in an onSubmit event handler
3. setCustomValidity(message): Adds a custom error message to the element; if
   you set a custom error message, the element is considered to be invalid, and
   the specified error is displayed. This lets you use JavaScript code to
   establish a validation failure other than those offered by the standard HTML5
   validation constraints. The message is shown to the user when reporting the
   problem.

We can also validate forms without using this API, but we will have to do some
more heavy lifting!
