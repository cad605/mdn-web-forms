# How to structure a web form

## The <form> element

The <form> element is used to declare a new form. A <form> cannot be declared
within another form. The content of the form, such as form controls, are nested
within the

<form> tags.

## The <fieldset> and <legend> elements

We use the <fieldset> element to create groups of form controls, and we can
attach a corresponding <legend> element below the opening <fieldset> tag to
formally describe the purpose of the grouping.

  <form>
    <fieldset>
      <legend>Fruit juice size</legend>
      <p>
        <input type="radio" name="size" id="size_1" value="small">
        <label for="size_1">Small</label>
      </p>
      <p>
        <input type="radio" name="size" id="size_2" value="medium">
        <label for="size_2">Medium</label>
      </p>
      <p>
        <input type="radio" name="size" id="size_3" value="large">
        <label for="size_3">Large</label>
      </p>
    </fieldset>
  </form>

## The <label> element

The <label> element is the formal way to define a label for an HTML form widget.
This is the most important element if you want to build accessible forms — when
implemented properly, screenreaders will speak a form element's label along with
any related instructions, as well as it being useful for sighted users

<label for="name">Name:</label> <input type="text" id="name" name="user_name">

Here we associate the label with the input via the `for` attribute. However, we
can also nest our input within the label tags:

  <label for="name">
    Name: <input type="text" id="name" name="user_name">
  </label>

Another advantage of properly set up labels is that you can click or tap the
label to activate the corresponding widget.
