# Other form controls

Non-`input` type elements.

## Multi-line text fields

We can use the `textarea` element. This is a non-empty element, and we can place
any default value between the opening and closing tags. This differs from
`input` which is an empty element and has its default value set through the
`value` property.

    <textarea cols="30" rows="8"></textarea>

Users are able to include line breaks within a `textearea` and have those breaks
included when the form is submitted.

It accepts three attributes:

1. `cols`: Specifies the visible width (columns) of the text control, measured
   in average character widths. This is effectively the starting width, as it
   can be changed by resizing the `<textarea>`, and overridden using CSS. The
   default value if none is specified is 20.

2. `rows`: Specifies the number of visible text rows for the control. This is
   effectively the starting height, as it can be changed by resizing the
   `<textarea>`, and overridden using CSS. The default value if none is
   specified is 2.

3. `wrap`: Specifies how the control wraps text. The values are `soft` (the
   default value), which means the text submitted is not wrapped but the text
   rendered by the browser is wrapped; `hard` (the cols attribute must be
   specified when using this value), which means both the submitted and rendered
   texts are wrapped, and off, which stops wrapping.

## Dropdown controls

There are two variants: the `select box` and the `autocomplete box`

### Select box

Created using a `select` element with multiple `option` elements nested within
ad children. The `selected` attribute sets a default selection.

    <select id="simple" name="simple">
      <option>Banana</option>
      <option selected>Cherry</option>
      <option>Lemon</option>
    </select>

The `optgroup` element can be used to group related elements:

    <select id="groups" name="groups">
      <optgroup label="fruits">
        <option>Banana</option>
        <option selected>Cherry</option>
        <option>Lemon</option>
      </optgroup>
      <optgroup label="vegetables">
        <option>Carrot</option>
        <option>Eggplant</option>
        <option>Potato</option>
      </optgroup>
    </select>

If a `value` attribute is set, that value is sent when the form is submitted.
Otherwise, the content of the selected option will be submitted.

We can also use the `multiple` attribute to allow for users to select more than
one element from the list.

### Autocomplete box

This control requires a `datalist` element with an `id`, and its children being
a set of options. We then associate an `input` element (with a `text` or `email`
type attribute) and set its `list` attribute to the id of the datalist.

    <label for="myFruit">What's your favorite fruit?</label>
    <input type="text" name="myFruit" id="myFruit" list="mySuggestion">
    <datalist id="mySuggestion">
      <option>Apple</option>
      <option>Banana</option>
      <option>Blackberry</option>
      <option>Blueberry</option>
      <option>Lemon</option>
      <option>Lychee</option>
      <option>Peach</option>
      <option>Pear</option>
    </datalist>

## Other controls

### Progress

Created using the `progress` element:

    <progress max="100" value="75">75/100</progress>

We specify the max value using the `max` attribute.

### Meter bar

Such a bar is created using a `<meter>` element.

    <meter min="0" max="100" value="75" low="33" high="66" optimum="50">75</meter>

The `low` and `high` attributes divide the bar into three parts, and together
with an `optimum` attribute define the preferred range. The following visual
effects render depending on the current value of `optimum` in relation to the
`low` and `high` values:

1. If the current value is in the preferred part of the range, the bar is green.
2. If the current value is in the average part of the range, the bar is yellow.
3. If the current value is in the worst part of the range, the bar is red.
