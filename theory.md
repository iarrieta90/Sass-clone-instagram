# Sass theory
### What is SASS? What does SASS stand for?
SASS stands for "Syntactically Awesome Stylesheets" and is a preprocessor scripting language that is compiled into Cascading Style Sheets (CSS). SassScript is the scripting language itself.

### What is a CSS pre-processor?
It is is a program that lets you generate CSS from the preprocessor's own unique syntax. Most CSS preprocessors will add some features that don't exist in pure CSS, making the CSS structure more readable and easy to mantain. To use a CSS preprocessor, you will need to compile on the development environment and then upload the compiled CSS file into the web server, or install a CSS compiler on the server itself.

### What does a pre-processor have to do with SASS?
Sass is a preprocessor scripting language. It lets you use features that don't exist in CSS yet such as variables, mathematical operations, nesting, mixins, inheritance, functions and other interesting functionalitites that make writing CSS much more powerful. You will need to compile Sass in order to save your preprocessed Sass file as a normal CSS file that you can use in your website.

### Why use SASS?
- CSS syntax friendly
- Ability to use variables
- Nested syntax
  Mixings
- Modular flexible code
- Easy to mantain
- Selector inheritance
- Custom functions
- Open source
- Huge amount of documentation and large community

### SASS has disadvantages? Which are?
- Code has to be compiled

### What is a SASS Variable? Explain why are useful
A Sass variable is a way to assign a value to a name that starts with $ (just like on PHP) so you can refer to that name instead of the value itself. Variables make it possible to reduce repetition, do complex math, configure libraries and much more

### Explain the SASS variables property with an example.
````
$font-stack:    Helvetica, sans-serif;
$primary-color: #333;

body {
  font: 100% $font-stack;
  color: $primary-color;
}
````

### What is a mixin? Why is it important? Give an example
Mixings allow you to define styles that can be re-used throughout your stylesheet. They make it easy to avoid using non-semantic classes, and to distribute collections of styles in libraries.

To create a mixin you use the @mixin directive and give it a name. On the example below we've named our mixin transform. We're also using the variable $property inside the parentheses so we can pass in a transform of whatever we want. After you create your mixin, you can then use it as a CSS declaration starting with @include followed by the name of the mixin.

````
@mixin transform($property) {
  -webkit-transform: $property;
  -ms-transform: $property;
  transform: $property;
}
.box { @include transform(rotate(30deg)); }
````

### What is SCSS? Give an example
It is called Sassy Cascaded Style Sheets, and uses the .scss file extension. With a few small exceptions, it’s a superset of CSS, which means essentially all valid CSS is valid SCSS as well. Because of its similarity to CSS, it’s the easiest syntax to get used to and the most popular.

SCSS looks like this:

````
@mixin button-base() {
  @include typography(button);
  @include ripple-surface;
  @include ripple-radius-bounded;

  display: inline-flex;
  position: relative;
  height: $button-height;
  border: none;
  vertical-align: middle;

  &:hover { cursor: pointer; }

  &:disabled {
    color: $mdc-button-disabled-ink-color;
    cursor: default;
    pointer-events: none;
  }
}
````


### What is SASS? Give an example

It is called Sassy Cascaded Style Sheets, and uses the .sass file extension. It was Sass's original syntax, and supports all the same features as SCSS but using indentation instead of curly braces and semicolons to describe the format of the document.

The indented syntax looks like this:

````
@mixin button-base()
  @include typography(button)
  @include ripple-surface
  @include ripple-radius-bounded

  display: inline-flex
  position: relative
  height: $button-height
  border: none
  vertical-align: middle

  &:hover
    cursor: pointer

  &:disabled
    color: $mdc-button-disabled-ink-color
    cursor: default
    pointer-events: none
````


### What is the difference between .scss and .sass syntax.
.scss uses the same syntax as css, while .sass uses indentation instead of curly braces and semicolons to describe the format of the document.

### In which cases would we use SCSS? And in which cases would we use SASS?
Sass is used when we need to use the original syntax for development. Scss is used when there is no requirement or criteria about the code syntax to use, and is particularly useful if we want to copy-paste pure css code snippets.

### Explain how traditional CSS and Preprocessed CSS workflows are different.
CSS is directly processed by the browser, while preprocessed CSS needs to be compiled first into regular CSS in order to be processed by the browser.


### Can we create functions with SASS? If it is true, give an example.
Sass allows us to create complex operations thorugh functions: 

````
@function pow($base, $exponent) {
  $result: 1;
  @for $_ from 1 through $exponent {
    $result: $result * $base;
  }
  @return $result;
}

.sidebar {
  float: left;
  margin-left: pow(4, 3) * 1px;
}
````

### What is nesting? Is it useful? Give an example of nesting
Sass lets you nest CSS selectors in the same way as HTML. It is useful for organizing your CSS and making it more readable, but overly nested rules will result in over-qualified CSS that could prove hard to maintain and is generally considered bad practice.

````
nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  li { display: inline-block; }

  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
}
````

### Why use @import?
Sass @import sule is very useful for modularizing stylesheets and thus making code easier to mantain.
Unlike plain CSS imports, which require the browser to make multiple HTTP requests as it renders your page, Sass imports are handled entirely during compilation and result in a single CSS stylesheet to be handed to the browser.

However, because of a number of issues related to its global scope, the Sass team discourages to continue using the @import rule as it will be soon deprecated and substituted by the @use rule and the new module system.

### How can we import other CSS/SASS files in SASS? Give an example
We can import other CSS/SASS files by using the @use rule. The @use rule loads mixins, functions, and variables from other Sass stylesheets, and combines CSS from multiple stylesheets together. Stylesheets loaded by @use are called "modules".

````
// style.scss

@use 'foundation/code';
@use 'foundation/lists';
````

### Explain the concept of inheritance in SASS.
In Sass it is possible to share a set of CSS properties from one selector to another by using the @extend directive.


### Why use @extend? Give an example
Sass’s @extend rule tells Sass that one selector should inherit the styles of another. It is useful if you have almost identically styled elements that only differ in some small details.
The syntax is as follows:

````
.error {
  border: 1px #f00;
  background-color: #fdd;
}

.error--serious {
  @extend .error;
  border-width: 3px;
}

````

In the case that you want to write a style rule that us only intended to be extended, you can use placeholder selectors:

````
%message-shared {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
}

.error {
  @extend %message-shared;
  border-color: red;
}

````

