# 4. Modules with @use and @forward

[Back to notes index](../README.md)

| [Previous: Nesting and parent selectors](../chapters/03-nesting-and-parent-selectors.md) | [Notes index](../README.md) | [Next: Mixins and content blocks](../chapters/05-mixins-and-content.md) |
|:--|:--:|--:|

## What I am learning here

The Sass module system keeps variables, functions, and mixins in an explicit scope. @use loads a module once and exposes its members through a namespace. @forward makes members available through a public entry point so a consumer can load one file instead of many.

Prefer this module system for new Sass code. Sass @use rules belong near the top of a stylesheet, before style rules.

## Load a module with a namespace

~~~scss
// _tokens.scss
$brand: #b64024;
$radius: 0.75rem;
~~~

~~~scss
// card.scss
@use "tokens";

.card {
  color: tokens.$brand;
  border-radius: tokens.$radius;
}
~~~

The tokens namespace makes the source of each value visible. If two modules have the same default namespace, choose an alias with as.

## Create one public entry point

~~~scss
// tools/_index.scss
@forward "tokens";
@forward "mixins";
~~~

~~~scss
// main.scss
@use "tools";

.button {
  color: tools.$brand;
  @include tools.focus-ring;
}
~~~

A forwarded member is public to consumers, but it is not automatically available inside the file doing the forwarding. Add @use too when that file also needs to refer to the member itself.

Partial files conventionally begin with an underscore. Sass can resolve a module without the underscore or file extension in the URL. Keep module rules before declarations and use clear namespaces instead of loading everything globally with as *.

The older Sass @import rule is deprecated in Dart Sass. Existing stylesheets can be migrated gradually, but new examples here use @use and @forward.

## Questions to review

1. What does @use load?
2. Why does a namespace help readers?
3. How many times does the Sass module system load a module?
4. What does @forward make available?
5. Does a forwarded member become visible inside the forwarding file automatically?
6. Where should @use appear in a stylesheet?
7. How can a module choose a different namespace?
8. Which module rules should new Sass code prefer over Sass @import?

| [Previous: Nesting and parent selectors](../chapters/03-nesting-and-parent-selectors.md) | [Notes index](../README.md) | [Next: Mixins and content blocks](../chapters/05-mixins-and-content.md) |
|:--|:--:|--:|

