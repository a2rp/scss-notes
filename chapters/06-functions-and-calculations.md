# 6. Functions and calculations

[Back to notes index](../README.md)

| [Previous: Mixins and content blocks](../chapters/05-mixins-and-content.md) | [Notes index](../README.md) | [Next: Lists, maps, and built-in modules](../chapters/07-lists-maps-and-built-in-modules.md) |
|:--|:--:|--:|

## What I am learning here

A Sass function calculates and returns a value that can be used in a declaration. It should express a calculation, not emit a block of selector rules. A mixin emits declarations or nested rules; a function returns a value. Choosing between them makes the stylesheet easier to read.

## Create a small function

~~~scss
@function spacing($step) {
  @return $step * 0.5rem;
}

.card {
  padding: spacing(4);
  gap: spacing(2);
}
~~~

The function runs during compilation. Its result becomes a CSS value. Keep functions predictable and name their inputs clearly. If a value can be expressed directly with a CSS custom property or calc(), consider whether runtime adjustment is more useful.

~~~scss
.panel {
  width: calc(100% - 2rem);
  padding: clamp(1rem, 3vw, 2.5rem);
}
~~~

CSS calc(), min(), max(), and clamp() let the browser calculate values using runtime measurements and CSS variables. Sass can simplify values it knows at compile time, but it should not replace CSS capabilities that are useful in the browser. Units must be compatible for arithmetic. Use the sass:math module for Sass-specific math operations rather than relying on ambiguous slash division.

## Questions to review

1. What does a Sass function return?
2. What should a mixin do compared with a function?
3. Which directive returns a value from a Sass function?
4. When is a custom Sass function useful?
5. What is a benefit of CSS calc()?
6. What does clamp() help express?
7. Why should function inputs have clear names?
8. Where should Sass math functions come from?

| [Previous: Mixins and content blocks](../chapters/05-mixins-and-content.md) | [Notes index](../README.md) | [Next: Lists, maps, and built-in modules](../chapters/07-lists-maps-and-built-in-modules.md) |
|:--|:--:|--:|

