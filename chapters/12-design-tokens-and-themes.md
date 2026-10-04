# 12. Design tokens and themes

[Back to notes index](../README.md)

| [Previous: Responsive design and media queries](../chapters/11-responsive-design-and-media-queries.md) | [Notes index](../README.md) | [Next: Stylesheet architecture](../chapters/13-stylesheet-architecture.md) |
|:--|:--:|--:|

## What I am learning here

Design tokens are named values for repeated decisions such as color, spacing, and corner radius. Sass variables can organize token values in source. CSS custom properties can expose tokens to the browser so a theme can change at runtime.

## Define browser-level tokens

~~~scss
:root {
  --color-page: #ffffff;
  --color-text: #202020;
  --color-accent: #9d321d;
  --space-card: 1.5rem;
  --radius-card: 0.75rem;
}

.card {
  color: var(--color-text);
  background: var(--color-page);
  padding: var(--space-card);
  border-radius: var(--radius-card);
}

[data-theme="dark"] {
  --color-page: #171717;
  --color-text: #f2f2f2;
  --color-accent: #ff987b;
}
~~~

The selector can be changed by application code or by a user preference handler. The browser recomputes the custom properties for descendants. Check color contrast for each theme, because a valid color value does not guarantee readable text.

Sass maps can keep compile-time values grouped when loops or functions need them. For runtime themes, output CSS custom properties rather than expecting Sass to change after compilation. Keep token names based on their role, such as color-text or space-card, instead of tying each name to one component's current color.

## Questions to review

1. What is a design token?
2. Which Sass value is resolved at compile time?
3. Why use CSS custom properties for runtime themes?
4. What does a descendant inherit from its theme selector?
5. How can application code select a theme?
6. Why test text contrast separately for each theme?
7. When is a Sass map useful for tokens?
8. Why name a token by purpose rather than its current color?

| [Previous: Responsive design and media queries](../chapters/11-responsive-design-and-media-queries.md) | [Notes index](../README.md) | [Next: Stylesheet architecture](../chapters/13-stylesheet-architecture.md) |
|:--|:--:|--:|

