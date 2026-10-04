# 16. All code samples

[Back to notes index](../README.md)

| [Previous: Accessibility, performance, and migration](15-accessibility-performance-and-migration.md) | [Notes index](../README.md) | [Next: Complete questions and answers](99-complete-q-and-a.md) |
|:--|:--:|--:|

## 1. SCSS foundations and setup

~~~sh
npm init -y
npm install --save-dev sass
~~~

~~~sh
npx sass src/scss/main.scss public/css/main.css
~~~

~~~sh
npx sass --watch src/scss/main.scss:public/css/main.css
~~~

~~~html
<link rel="stylesheet" href="/css/main.css">
~~~

~~~scss
$brand: #b64024;

.page-title {
  color: $brand;
  font-size: 2rem;
}
~~~

~~~css
.page-title {
  color: #b64024;
  font-size: 2rem;
}
~~~

## 2. Variables and CSS custom properties

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

## 3. Nesting and parent selectors

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

~~~scss
.card {
  p {
    line-height: 1.6;
  }
}
~~~

## 4. Modules with @use and @forward

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

## 5. Mixins and content blocks

~~~scss
@mixin focus-ring($color: #2457c5) {
  &:focus-visible {
    outline: 3px solid $color;
    outline-offset: 3px;
  }
}

.button {
  border: 0;
  padding: 0.75rem 1rem;
  @include focus-ring;
}

.link-button {
  @include focus-ring(#8f2d18);
}
~~~

~~~scss
@mixin at-medium {
  @media (min-width: 48rem) {
    @content;
  }
}

.page {
  display: grid;

  @include at-medium {
    grid-template-columns: 16rem 1fr;
  }
}
~~~

## 6. Functions and calculations

~~~scss
@function spacing($step) {
  @return $step * 0.5rem;
}

.card {
  padding: spacing(4);
  gap: spacing(2);
}
~~~

~~~scss
.panel {
  width: calc(100% - 2rem);
  padding: clamp(1rem, 3vw, 2.5rem);
}
~~~

## 7. Lists, maps, and built-in modules

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

~~~scss
$space-scale: 0.25rem, 0.5rem, 1rem, 1.5rem;

.compact {
  padding: nth($space-scale, 2);
}
~~~

~~~scss
@use "sass:list";

.compact {
  padding: list.nth($space-scale, 2);
}
~~~

## 8. Placeholders and @extend

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

## 9. Interpolation and dynamic selectors

~~~scss
$variants: brand, quiet, danger;

@each $variant in $variants {
  .button--#{$variant} {
    border-color: var(--color-#{$variant});
  }
}
~~~

## 10. Conditionals and loops

~~~scss
$steps: (
  "sm": 0.5rem,
  "md": 1rem,
  "lg": 1.5rem
);

@each $name, $value in $steps {
  .gap-#{$name} {
    gap: $value;
  }
}
~~~

~~~scss
$mode: "dark";

@if $mode == "dark" {
  .surface {
    color: #ffffff;
    background: #202020;
  }
} @else {
  .surface {
    color: #202020;
    background: #ffffff;
  }
}
~~~

## 11. Responsive design and media queries

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

~~~scss
@media (prefers-reduced-motion: reduce) {
  .animated-card {
    transition-duration: 0.01ms;
    animation-duration: 0.01ms;
  }
}
~~~

## 12. Design tokens and themes

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

## 13. Stylesheet architecture

~~~text
src/scss/
├── main.scss
├── foundation/
│   ├── _tokens.scss
│   ├── _reset.scss
│   └── _typography.scss
├── components/
│   ├── _button.scss
│   └── _card.scss
└── tools/
    ├── _mixins.scss
    └── _index.scss
~~~

~~~scss
@use "foundation/reset";
@use "foundation/typography";
@use "components/button";
@use "components/card";
~~~

## 14. Compilation, source maps, and tooling

~~~json
{
  "scripts": {
    "sass:build": "sass src/scss/main.scss public/css/main.css",
    "sass:watch": "sass --watch src/scss/main.scss:public/css/main.css"
  },
  "devDependencies": {
    "sass": "use the version installed by npm"
  }
}
~~~

## 15. Accessibility, performance, and migration

~~~sh
npm install --save-dev sass-migrator
npx sass-migrator module --migrate-deps src/scss/main.scss
~~~

| [Previous: Accessibility, performance, and migration](15-accessibility-performance-and-migration.md) | [Notes index](../README.md) | [Next: Complete questions and answers](99-complete-q-and-a.md) |
|:--|:--:|--:|
