# The HTML5 input types

Looking at the functionality of newer form controls in detail, including some
new input types, which were added in HTML5 to allow collection of specific types
of data.

## Email address field

We set the `type` attribute of an `input` element to `email`:

    <input type="email" id="email" name="email">

When this type is used, the user is required to type a valid email address into
the field

Using the `multiple` attribute can allow for the collection of comma-separated
addresses to be entered.

To implement different validation behavior, you can use the `pattern` attribute,
and you can also customize the error messages.

## Search field

Search fields are intended to be used to create search boxes on pages and apps

We set the `type` attribute of an `input` element to `search`:

    <input type="search" id="search" name="search">

Another worth-noting feature is that the values of a search field can be
automatically saved and re-used to offer auto-completion across multiple pages
of the same website; this tends to happen automatically in most modern browsers.

## Phone number field

Used to collect phone numbers.

We set the `type` attribute of an `input` element to `tel`:

    <input type="tel" id="tel" name="tel">

To implement validation behavior, you can use the `pattern` attribute.

## URL field

We set the `type` attribute of an `input` element to `url`:

    <input type="url" id="url" name="url">

It adds special validation constraints to the field. The browser will report an
error if no protocol (such as http:) is entered, or if the URL is otherwise
malformed.

## Numeric field

We set the `type` attribute of an `input` element to `number`:

    <input type="number" name="age" id="age" min="1" max="10" step="2">

You can constrain the values by using the `min` and `max` attributes, as well as
set a `step` used for incrementing the value.

## Slider controls

We set the `type` attribute of an `input` element to `range`:

    <label for="price">Choose a maximum house price: </label>
    <input type="range" name="price" id="price" min="50000" max="500000" step="100" value="250000">
    <output class="price-output" for="price"></output>

It's important to properly configure your slider. To that end, it's highly
recommended that you set the `min`, `max`, and `step` attributes which set the
minimum, maximum and increment values, respectively.

To actually display the current value, and update it as it changed, you must use
JavaScript:

    const price = document.querySelector('#price');
    const output = document.querySelector('.price-output');

    output.textContent = price.value;

    price.addEventListener('input', function() {
      output.textContent = price.value;
    });

## Date and Time

A date and time control is created using the <input> element and an appropriate
value for the type attribute, depending on whether you wish to collect dates,
times, or both. Here are some examples:

    <input type="datetime-local" name="datetime" id="datetime">
    <input type="month" name="month" id="month">
    <input type="time" name="time" id="time">
    <input type="week" name="week" id="week">

We can also added constraints:

    <label for="myDate">When are you available this summer?</label>
    <input type="date" name="myDate" min="2013-06-01" max="2013-08-31" step="7" id="myDate">

## Color picker control

We set the `type` attribute of an `input` element to `color`:

    <input type="color" name="color" id="color">

The value returned is always a lowercase 6-value hexadecimal color.
