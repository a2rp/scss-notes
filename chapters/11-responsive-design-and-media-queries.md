# 11. Responsive design and media queries

[Back to notes index](../README.md)

| [Previous: Conditionals and loops](../chapters/10-conditionals-and-loops.md) | [Notes index](../README.md) | [Next: Design tokens and themes](../chapters/12-design-tokens-and-themes.md) |
|:--|:--:|--:|

## What I am learning here

Responsive design lets a layout adapt to available space and user preferences. Sass can organize repeated media-query rules, but the browser evaluates the CSS media query. I choose breakpoints when the content needs them rather than targeting a list of specific devices.

## Start with a narrow layout

~~~scss
.product-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1rem;
}

@media (min-width: 42rem) {
  .product-grid {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }
}

@media (min-width: 68rem) {
  .product-grid {
    grid-template-columns: repeat(3, minmax(0, 1fr));
  }
}
~~~

minmax(0, 1fr) helps grid tracks shrink without overflowing due to long content. The first rule works at narrow widths; later rules enhance the layout when more room is available.

Keep repeated breakpoints in Sass variables if that helps maintain a consistent system. CSS custom properties cannot be used in every media-query condition, so Sass variables are useful for compile-time breakpoint values. Container queries are useful when a component should adapt to its own container rather than the viewport.

Respect user preferences such as reduced motion:

~~~scss
@media (prefers-reduced-motion: reduce) {
  .animated-card {
    transition-duration: 0.01ms;
    animation-duration: 0.01ms;
  }
}
~~~

Test at widths between breakpoints too. A design can fail in the space between the phone and desktop sizes even when it looks correct at two chosen screenshots.

## Questions to review

1. Who evaluates a media query?
2. How should I choose a breakpoint?
3. Why start with a narrow layout?
4. What does minmax(0, 1fr) help prevent?
5. When is a container query useful?
6. Why are Sass variables useful for some media conditions?
7. What does prefers-reduced-motion represent?
8. Why test widths between chosen breakpoints?

| [Previous: Conditionals and loops](../chapters/10-conditionals-and-loops.md) | [Notes index](../README.md) | [Next: Design tokens and themes](../chapters/12-design-tokens-and-themes.md) |
|:--|:--:|--:|

