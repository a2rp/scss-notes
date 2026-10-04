# 8. Placeholders and @extend

[Back to notes index](../README.md)

| [Previous: Lists, maps, and built-in modules](../chapters/07-lists-maps-and-built-in-modules.md) | [Notes index](../README.md) | [Next: Interpolation and dynamic selectors](../chapters/09-interpolation-and-dynamic-selectors.md) |
|:--|:--:|--:|

## What I am learning here

@extend asks Sass to group a selector with another selector that already has a rule. A placeholder selector begins with a percent sign and is not emitted into CSS by itself. It appears only when another selector extends it.

## Share a small related rule

~~~scss
%message-frame {
  padding: 1rem;
  border: 1px solid currentColor;
  border-radius: 0.5rem;
}

.notice {
  @extend %message-frame;
  color: #2457c5;
}

.warning {
  @extend %message-frame;
  color: #8f2d18;
}
~~~

The compiled CSS groups selectors that share the placeholder declarations. The placeholder itself does not become a class in the output.

Extend is strongest when selectors are conceptually related and can safely share the same rule. It can create complex selector combinations when extended across unrelated contexts. A mixin is often easier to predict when I want to copy a set of declarations into a selector. I inspect the generated CSS to understand the output.

Do not extend a selector just to avoid repeating a few lines. A small amount of explicit CSS can be clearer than a complicated selector relationship.

## Questions to review

1. What does @extend change?
2. What character begins a placeholder selector?
3. Does an unused placeholder appear in the output CSS?
4. How does a selector use placeholder declarations?
5. When is extending a placeholder appropriate?
6. Why can extending unrelated selectors create surprising output?
7. When can a mixin be clearer than @extend?
8. What should I inspect after adding an extend relationship?

| [Previous: Lists, maps, and built-in modules](../chapters/07-lists-maps-and-built-in-modules.md) | [Notes index](../README.md) | [Next: Interpolation and dynamic selectors](../chapters/09-interpolation-and-dynamic-selectors.md) |
|:--|:--:|--:|

