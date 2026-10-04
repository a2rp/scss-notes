# 9. Interpolation and dynamic selectors

[Back to notes index](../README.md)

| [Previous: Placeholders and @extend](../chapters/08-placeholders-and-extend.md) | [Notes index](../README.md) | [Next: Conditionals and loops](../chapters/10-conditionals-and-loops.md) |
|:--|:--:|--:|

## What I am learning here

Interpolation inserts a Sass value into a selector, property name, or string. It is written with hash braces. Most declarations can use a Sass variable directly, so interpolation is mainly useful when the value must become part of syntax such as a selector or property name.

## Build a small selector family

~~~scss
$variants: brand, quiet, danger;

@each $variant in $variants {
  .button--#{$variant} {
    border-color: var(--color-#{$variant});
  }
}
~~~

The loop emits a rule for each controlled name. The browser receives ordinary selectors such as .button--brand. Sass variables are resolved during compilation; interpolation does not make a selector dynamic at runtime.

Interpolation can also be used in CSS custom property names and generated strings. Keep generated output finite and predictable. If a fixed set of states is small, writing those selectors directly may be easier for teammates to find and maintain. Do not build selectors from arbitrary user-provided input.

## Questions to review

1. What does interpolation insert?
2. How is interpolation written in SCSS?
3. When is interpolation needed in a selector?
4. What does the example loop generate?
5. Does Sass interpolation create runtime selectors?
6. Why should generated names come from controlled values?
7. When can writing selectors directly be clearer?
8. Where else can interpolation be useful?

| [Previous: Placeholders and @extend](../chapters/08-placeholders-and-extend.md) | [Notes index](../README.md) | [Next: Conditionals and loops](../chapters/10-conditionals-and-loops.md) |
|:--|:--:|--:|

