# 3. Nesting and parent selectors

[Back to notes index](../README.md)

| [Previous: Variables and CSS custom properties](../chapters/02-variables-and-css-custom-properties.md) | [Notes index](../README.md) | [Next: Modules with @use and @forward](../chapters/04-modules-use-and-forward.md) |
|:--|:--:|--:|

## What I am learning here

Nesting places a related selector inside another selector. Sass combines the selectors when it compiles the stylesheet. This can keep a small component's rules together, but excessive nesting creates long selectors that are harder to override and reuse.

## Nest related component rules

~~~scss
.card {
  padding: 1rem;
  border: 1px solid #d7d7d7;

  &__title {
    margin: 0;
    font-size: 1.25rem;
  }

  &__link {
    color: #8f2d18;

    &:hover,
    &:focus-visible {
      text-decoration-thickness: 0.12em;
    }
  }
}
~~~

The ampersand represents the full parent selector. Here, it creates .card__title and .card__link. When it is followed by a pseudo-class, it creates a state selector such as .card__link:hover. The output is ordinary CSS.

Nesting can also express a descendant:

~~~scss
.card {
  p {
    line-height: 1.6;
  }
}
~~~

This compiles to .card p, which matches every paragraph inside the card. That selector may become too broad if the component grows. I keep nesting shallow and check compiled selectors, especially when rules are inside loops or mixins.

Nesting media queries inside a selector can keep responsive changes near the rule they affect. Use it only when it improves navigation of the stylesheet.

## Questions to review

1. What does Sass do with nested selectors?
2. What does the ampersand represent?
3. How does &__title combine with .card?
4. What selector does a nested p create?
5. Why can deep nesting make CSS harder to maintain?
6. What does &:focus-visible target?
7. Why inspect the compiled selector?
8. When can a nested media query improve organization?

| [Previous: Variables and CSS custom properties](../chapters/02-variables-and-css-custom-properties.md) | [Notes index](../README.md) | [Next: Modules with @use and @forward](../chapters/04-modules-use-and-forward.md) |
|:--|:--:|--:|

