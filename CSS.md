## CSS Anatomy
The diagram below shows two different methods, or _syntaxes_, for writing CSS code. The first syntax shows CSS applied as a _ruleset_, while the second shows it written as an _inline style_. Two different methods of writing CSS may seem a bit intimidating at first, but it’s not as bad as it looks!
![[CSS_Anatomy.svg|700]]
Both methods contain common features in their [anatomy](https://www.codecademy.com/resources/docs/css/anatomy?page_req=catalog). Notice how both syntaxes contain a _declaration_. Declarations are the core of CSS. They apply a style to the selected element. Here, the [`<p>`](https://www.codecademy.com/resources/docs/html/paragraphs?page_req=catalog) element has been selected in both syntaxes and will be styled to display the text in blue.

There is another way to style in HTML called, internal style sheet, it works by using the `<style></style>` tags.

The best way to style in HTML is via an external `.css` file. This file will hold all the styles that are to be used. It is linked in the head of the HTML file, `<link>`, It is a self-closing tag and requires the following attributes:
1. `href` — like the anchor element, the value of this attribute must be the address, or path, to the CSS file.
2. `rel` — this attribute describes the relationship between the HTML file and the CSS file. Because you are linking to a stylesheet, the value should be set to `stylesheet`.

When linking an HTML file and a CSS file together, the `<link>` element will look like the following:

```html
<link href='https://www.codecademy.com/stylesheets/style.css' rel='stylesheet'>
```

## Selectors
### Type
Remember that _declarations_ are a fundamental part of CSS because they apply a style to a selected element. But how do you decide which elements will get the style? With a _selector_.

A selector is used to target the specific HTML element(s) to be styled by the declaration. One selector you may already be familiar with is the _type_ selector. Just like its name suggests, the type selector matches the _type_ of the element in the HTML document.

In the previous lesson, you changed the color of a paragraph element.

```css
p {  color: green;}
```

This is an instance of using the type selector! The element type is `p`, which comes from the HTML `<p>` element.

Some important notes on the type selector:
- The type selector does not include the angle brackets.
- Since element types are often referred to by their opening tag name, the type selector is sometimes referred to as the _tag name_ or _element_ selector.

### Universal
You learned how the _type selector_ selects all elements of a given type. Well, the _universal selector_ selects all elements of _any_ type.

Targeting all of the elements on the page has a few specific use cases, such as resetting default browser styling or selecting all children of a parent element. Don’t worry if you don’t understand the use cases right now; we will get to them later on in our Learn CSS journey.

The universal selector uses the `*` character in the same place where you specified the type selector in a ruleset, like so:

```css
* {   font-family: Verdana;}
```

In the code above, every text element on the page will have its font changed to `Verdana`.

### Class
CSS is not limited to selecting elements by their type. As you know, HTML elements can also have attributes. When working with HTML and CSS a _class_ attribute is one of the most common ways to select an element.

For example, consider the following HTML:

```html
<p class='brand'>Sole Shoe Company</p>
```

The paragraph element in the example above has a `class` attribute within the opening tag of the`<p>` element. The `class` attribute is set to `'brand'`. To select this element using CSS, we can create a ruleset with a class selector of `.brand`.

```css
.brand {}
```

To select an HTML element by its class using CSS, a period (`.`) must be prepended to the class’s name. In the example above, the class is `brand`, so the CSS selector for it is `.brand`.

### Multiple Classes
We can use CSS to select an HTML element’s `class` attribute by name. And so far, we’ve selected elements using only one class name per element. If every HTML element had a single class, all the style information for each element would require a new class.

Luckily, it’s possible to add more than one class name to an HTML element’s `class` attribute.

For instance, perhaps there’s a heading element that needs to be green and bold. You could write two CSS rulesets like so:

```css
.green {
	color: green;
}

.bold {
	font-weight: bold;
}
```

Then, you could include both of these classes on one HTML element like this:

```html
<h1 class='green bold'> ... </h1>
```

We can add multiple classes to an HTML element’s `class` attribute by separating them with a space. This enables us to mix and match CSS classes to create many unique styles without writing a custom class for every style combination needed.

### ID
Oftentimes it’s important to select a single element with CSS to give it its own unique style. If an HTML element needs to be styled uniquely, we can give it an ID using the `id` attribute.

```html
<h1 id='large-title'> ... </h1>
```

In contrast to `class` which accepts multiple values, and can be used broadly throughout an HTML document, an element’s `id` can only have a single value, and only be used once per page.

To select an element’s ID with CSS, we prepend the `id` name with a number sign (`#`). For instance, if we wanted to select the HTML element in the example above, it would look like this:

```css
#large-title {}
```

The `id` name is `large-title`, therefore the CSS selector for it is `#large-title`.

### Attribute
You may remember that some HTML elements use attributes to add extra detail or functionality to the element. Some familiar attributes may be `href` and `src`, but there are [many more](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes)—including `class` and `id`!

The _attribute selector_ can be used to target HTML elements that already contain attributes. Elements of the same type can be targeted differently by their attribute or attribute value. This alleviates the need to add new code, like the `class` or `id` attributes.

Attributes can be selected similarly to types, classes, and IDs.

```
[href]{   color: magenta;}
```

The most basic syntax is an attribute surrounded by square brackets. In the above example: `[href]` would target all elements with an `href` attribute and set the color to `magenta`.

And it can get [more granular](https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute_selectors#syntax) from there by adding type and/or attribute values. One way is by using `type[attribute*=value]`. In short, this code selects an element where the attribute contains any instance of the specified value. Let’s take a look at an example.

```
<img src='/images/seasons/cold/winter.jpg'><img src='/images/seasons/warm/summer.jpg'>
```

The HTML code above renders two `<img>` elements, each containing a `src` attribute with a value equaling a link to an image file.

```
img[src*='winter'] {  height: 50px;}img[src*='summer'] {  height: 100px;}
```

Now take a look at the above CSS code. The _attribute selector_ is used to target each image individually.

- The first ruleset looks for an `img` element with an attribute of `src` that contains the string `'winter'`, and sets the `height` to `50px`.
- The second ruleset looks for an `img` element with an attribute of `src` that contains the string `'summer'`, and sets the `height` to `100px`.

Notice how no new HTML markup (like a class or id) needed to be added, and we were still able to modify the styles of each image independently. This is one advantage to using the attribute selector!

### Pseudo-class
You may have observed how the appearance of certain elements can change, or be in a different state, after certain user interactions. For instance:

- When you click on an `<input>` element, and a blue border is added showing that it is in _focus_.
- When you click on a blue `<a>` link to _visit_ to another page, but when you return the link’s text is purple.
- When you’re filling out a form and the submit button is grayed out and _disabled_. But when all of the fields have been filled out, the button has color showing that it’s _active_.

These are all examples of pseudo-class selectors in action! In fact, `:focus`, `:visited`, `:disabled`, and `:active` are all pseudo-classes. Factors such as user interaction, site navigation, and position in the document tree can all give elements a different state with pseudo-class.

A pseudo-class can be attached to any selector. It is always written as a colon `:` followed by a name. For example `p:hover`.

```css
p:hover {
	background-color: lime;
}
```

In the above code, whenever the mouse hovers over a paragraph element, that paragraph will have a lime-colored background.