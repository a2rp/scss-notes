# 7. Lists, maps, and built-in modules

[Back to notes index](../README.md)

| [Previous: Functions and calculations](../chapters/06-functions-and-calculations.md) | [Notes index](../README.md) | [Next: Placeholders and @extend](../chapters/08-placeholders-and-extend.md) |
|:--|:--:|--:|

## What I am learning here

Sass lists hold ordered values. Maps associate keys with values. They are useful for compact design scales and for generating related declarations from structured data. Built-in Sass modules group functions under namespaces such as sass:map, sass:list, sass:math, and sass:color.

## Read a map through its module

~~~scss
@use "sass:map";

$colors: (
  "brand": #b64024,
  "ink": #252525,
  "paper": #ffffff
);

.button {
  color: map.get($colors, "paper");
  background-color: map.get($colors, "brand");
}
~~~

A list is useful for an ordered scale:

~~~scss
$space-scale: 0.25rem, 0.5rem, 1rem, 1.5rem;

.compact {
  padding: nth($space-scale, 2);
}
~~~

For new code, use the namespaced sass:list functions rather than legacy global built-ins:

~~~scss
@use "sass:list";

.compact {
  padding: list.nth($space-scale, 2);
}
~~~

Namespacing shows where an operation comes from and avoids collisions with CSS functions. For example, import sass:math and use math.div for Sass division. Use sass:color functions for compile-time color work. Keep values in maps when a loop or function needs to look them up; a plain variable is simpler for one value.

## Questions to review

1. What type of data does a Sass list store?
2. What does a map associate?
3. Why use built-in Sass modules?
4. Which module contains map lookup functions?
5. Which namespaced function reads an item by position from a list?
6. Why prefer list.nth over the legacy global nth form?
7. Where should Sass division helpers come from?
8. When is a simple variable better than a map?

| [Previous: Functions and calculations](../chapters/06-functions-and-calculations.md) | [Notes index](../README.md) | [Next: Placeholders and @extend](../chapters/08-placeholders-and-extend.md) |
|:--|:--:|--:|

