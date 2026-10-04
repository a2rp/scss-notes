# 2. Variables and CSS custom properties

[Back to notes index](../README.md)

| [Previous: SCSS foundations and setup](../chapters/01-scss-foundations-and-setup.md) | [Notes index](../README.md) | [Next: Nesting and parent selectors](../chapters/03-nesting-and-parent-selectors.md) |
|:--|:--:|--:|

## What I am learning here

A Sass variable stores a value during compilation. I use it for source-level values such as a spacing scale, font stack, or default color. A CSS custom property is written in the generated CSS and can change at runtime, including through the cascade, a class, or JavaScript.

These two kinds of variables solve related but different problems. Sass variables help organize the source. CSS custom properties help express values that need to vary in the browser.

## Set reusable values

~~~scss
$space-unit: 0.5rem;
$brand-color: #b64024;
$body-font: Arial, sans-serif;

.card {
  padding: $space-unit * 3;
  border-color: $brand-color;
  font-family: $body-font;
}
~~~

Sass variables begin with a dollar sign and are replaced during compilation. They follow Sass scope rules. A variable declared inside a selector is local to that scope unless reassigned with a special flag, so keep shared configuration near the top of a module.

## Use a runtime custom property

~~~scss
:root {
  --brand-color: #b64024;
  --page-gap: 1.5rem;
}

.button {
  background-color: var(--brand-color);
  padding-inline: var(--page-gap);
}

.theme-dark {
  --brand-color: #e98466;
}
~~~

The browser resolves var() and inherits custom properties through the DOM. This makes custom properties useful for themes and values that change without recompiling Sass. Sass can also create their declarations, but the final runtime behavior belongs to CSS.

A Sass variable marked !default can be configured by a consumer before the module is loaded. Use that pattern for a library setting, not as a substitute for browser-level theming.

## Questions to review

1. When is a Sass variable evaluated?
2. Where does a CSS custom property exist?
3. Which kind of variable can change through the CSS cascade at runtime?
4. What character begins a Sass variable name?
5. When is var() evaluated?
6. Why are custom properties useful for themes?
7. What does !default allow a module consumer to do?
8. Which variable type should I choose for a value changed by JavaScript?

| [Previous: SCSS foundations and setup](../chapters/01-scss-foundations-and-setup.md) | [Notes index](../README.md) | [Next: Nesting and parent selectors](../chapters/03-nesting-and-parent-selectors.md) |
|:--|:--:|--:|

