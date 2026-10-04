# 1. SCSS foundations and setup

[Back to notes index](../README.md)

| [Previous: Notes index](../README.md) | [Notes index](../README.md) | [Next: Variables and CSS custom properties](02-variables-and-css-custom-properties.md) |
|:--|:--:|--:|

## What I am learning here

Sass is a stylesheet language with a compiler. SCSS is its CSS-like syntax, stored in files that end in .scss. Existing CSS declarations are valid SCSS, with extra features such as variables, nesting, mixins, and modules available when I need them. A browser does not execute SCSS directly. The compiler turns SCSS into CSS that the browser can read.

This separation is useful: I write organized source files, run the compiler as part of a build, and serve the generated CSS to the browser. The generated file can be inspected when a style does not behave as expected.

## Install and run Dart Sass

For a small Node project, install Sass as a development dependency:

~~~sh
npm init -y
npm install --save-dev sass
~~~

Create src/scss/main.scss and public/css/main.css, then compile once:

~~~sh
npx sass src/scss/main.scss public/css/main.css
~~~

To recompile whenever the source changes, use watch mode:

~~~sh
npx sass --watch src/scss/main.scss:public/css/main.css
~~~

The watch command keeps running in the terminal. Link the generated CSS from the HTML document:

~~~html
<link rel="stylesheet" href="/css/main.css">
~~~

## Write a first SCSS rule

~~~scss
$brand: #b64024;

.page-title {
  color: $brand;
  font-size: 2rem;
}
~~~

Sass substitutes the variable while compiling. The output is regular CSS:

~~~css
.page-title {
  color: #b64024;
  font-size: 2rem;
}
~~~

The .scss file is the source I edit. The .css file is the browser-facing result. In a project with a build tool, Sass can be integrated into that build instead of running the CLI command manually.

## Questions to review

1. What is Sass?
2. What does SCSS describe?
3. Can a browser run an SCSS file directly?
4. What does the Sass compiler produce?
5. What does the .scss extension identify?
6. Why install Sass as a development dependency?
7. What does the --watch option do?
8. Why inspect generated CSS when a style is unexpected?

| [Previous: Notes index](../README.md) | [Notes index](../README.md) | [Next: Variables and CSS custom properties](02-variables-and-css-custom-properties.md) |
|:--|:--:|--:|

