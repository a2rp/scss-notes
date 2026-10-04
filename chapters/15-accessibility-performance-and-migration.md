# 15. Accessibility, performance, and migration

[Back to notes index](../README.md)

| [Previous: Compilation, source maps, and tooling](../chapters/14-compilation-source-maps-and-tooling.md) | [Notes index](../README.md) | [Next: All code samples](../chapters/98-all-code-samples.md) |
|:--|:--:|--:|

## What I am learning here

Styles affect whether people can read and use an interface. Keep visible focus indicators, sufficient text contrast, and readable spacing. Test with keyboard input, zoom, and different viewport sizes. A style that looks correct in one screenshot can still hide focus or clip text at another size.

## Keep output useful

Nesting and loops can make SCSS shorter while generating very large selectors or many rules. Check the compiled CSS when a source change creates unexpected output. Remove generated utilities that are not used, keep selectors specific enough to understand, and avoid repeated rules that the cascade has to resolve.

Use modern CSS when it already solves the problem. Sass is most useful for source organization, reusable patterns, and compile-time data. Do not add Sass just to write a few lines of plain CSS.

## Move legacy imports to modules

The Sass @import rule is deprecated in Dart Sass. New files should use @use and @forward. Existing projects can migrate in steps, then compile and review the resulting CSS.

~~~sh
npm install --save-dev sass-migrator
npx sass-migrator module --migrate-deps src/scss/main.scss
~~~

A migration tool can update common patterns, but I still review the diff. Check module namespaces, CSS output, duplicate selectors, and any library-specific behavior before relying on the converted files.

Accessibility and output size need browser checks as well as source review. Test focus, motion preferences, contrast, and the generated production CSS after significant changes.

## Questions to review

1. Which visual cue should remain available to keyboard users?
2. Why test text contrast?
3. How can excessive nesting harm output?
4. What should I inspect after changing a loop?
5. When may plain CSS be enough without Sass?
6. Which module rules should new code use?
7. What should I review after running a migration tool?
8. Which browser checks help confirm accessible styling?

| [Previous: Compilation, source maps, and tooling](../chapters/14-compilation-source-maps-and-tooling.md) | [Notes index](../README.md) | [Next: All code samples](../chapters/98-all-code-samples.md) |
|:--|:--:|--:|

