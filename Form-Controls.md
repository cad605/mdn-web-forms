# Basic native form controls

## Text input fields

Text `<input>` fields are the most basic form widgets. Some common attributes
are:

1. They can be marked as `readonly` (the user cannot modify the input value but
   it is still sent with the rest of the form data) or `disabled` (the input
   value can't be modified and is never sent with the rest of the form data).
2. They can have a `placeholder`; this is text that appears inside the text
   input box that should be used to briefly describe the purpose of the box.
3. They can be constrained in `size` (the physical size of the box) and
   `maxlength` (the maximum number of characters that can be entered into the
   box).
4. They can benefit from spell checking (using the `spellcheck` attribute), if
   the browser supports it

The behavior and appearance of the field is largely dependant on the `type`
attribute.

### Basic single-line text fields

We set the `type` attribute to `text`, which is also the default value Here is a
basic example:

    <input type="text" id="comment" name="comment" value="I'm a text field">

Note: if a line break is entered into the field, the browser removes these line
breaks before sending the data to the server.

### Password fields

We set the `type` attribute to `password`

    <input type="password" id="pwd" name="pwd">

This obscures the value entered into the field so the text entered cannot be
read by others.

Note: This is only a UI feature! You must encrypt the data before sending it
over a network.

### Hidden content

Such a field is used to hide data that will be sent to the server, but does not
need to be shown to the user.

<input type="hidden" id="timestamp" name="timestamp" value="1286705410">

If you create such an element, it's required to set its name and value
attributes. The value can be dynamically set via JavaScript. The hidden input
type should not have an associated label.

## Checkable items: radio buttons and checkboxes

Both types of checkable items, radio buttons and checkboxes, use the `checked`
attribute to indicate the current state of the control. An interesting deviation
from other form elements is that checkable items are not submitted with the rest
of the form data if not selection(s) have been made; or they are only sent if
they are checked.

### Checkbox

Created using an `input` control with a type of `checkbox`.

    <input type="checkbox" id="questionOne" name="subscribe" value="yes" checked>

Checkboxes grouped together using a `fieldset` and `legend` should also use the
same `name` attribute.

    <fieldset>
      <legend>Choose all the vegetables you like to eat</legend>
      <ul>
        <li>
          <label for="carrots">Carrots</label>
          <input type="checkbox" id="carrots" name="vegetable" value="carrots" checked>
        </li>
        <li>
          <label for="peas">Peas</label>
          <input type="checkbox" id="peas" name="vegetable" value="peas">
        </li>
        <li>
          <label for="cabbage">Cabbage</label>
          <input type="checkbox" id="cabbage" name="vegetable" value="cabbage">
        </li>
      </ul>
    </fieldset>

Checkboxes are often styled to look and work as toggle switches.

### Radio buttons

Created using an `input` control with a type of `radio`.

    <input type="radio" id="soup" name="meal" checked>

Radio buttons can be grouped using a `fieldset` and sharing the same `name`
attribute. When submitted, only the value of the selected button is sent; if no
value is selected, nothing is sent.

## Actual buttons

There are three types of buttons:

1. submit - Sends the form data to the server. For <button> elements, omitting
   the type attribute (or an invalid value of type) results in a submit button.

2. reset - Resets all form widgets to their default values.

3. button - Buttons that have no automatic effect but can be customized using
   JavaScript code.

Using an `input` element with any of these types will result in a button. There
is also the `button` element which has a `type` attribute that also takes these
three options. The `button` element is easier to style.

    <button type="submit">
        This is a <strong>submit button</strong>
    </button>

    <input type="submit" value="This is a submit button">

### Image button

The image button control is rendered exactly like an <img> element, except that
when the user clicks on it, it behaves like a submit button.

    <input type="image" alt="Click me!" src="my-img.png" width="80" height="30">

## File Picker

Forms can send files to the server using the `file` input type.

    <input type="file" name="file" id="file" accept="image/*" multiple>

The types of files that can be selected from the picker can be set using the
`accept` attribute. We can also allow a user to send more than one file by
setting the `multiple` attribute.
