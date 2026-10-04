# 13. Stylesheet architecture

[Back to notes index](../README.md)

| [Previous: Design tokens and themes](../chapters/12-design-tokens-and-themes.md) | [Notes index](../README.md) | [Next: Compilation, source maps, and tooling](../chapters/14-compilation-source-maps-and-tooling.md) |
|:--|:--:|--:|

## What I am learning here

A stylesheet structure should help me find a rule and understand where its values come from. Small modules with clear responsibilities are easier to change than one large file with unrelated global rules.

## Organize files by responsibility

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

The entry point loads modules and defines the global order:

~~~scss
@use "foundation/reset";
@use "foundation/typography";
@use "components/button";
@use "components/card";
~~~

Sass partial filenames start with an underscore and are loaded through module URLs without the underscore. Keep tokens and reusable helpers separate from component rules. Use @forward in a module index when a public entry point is genuinely helpful.

Component classes should have predictable names and limited scope. A BEM-style name such as card__title communicates a relationship without relying on deep descendant selectors. Avoid creating a partial for every tiny selector; files should represent units that can be found and maintained independently.

The structure is a tool, not a goal. A small page may need only an entry point and a few component files. Add directories as the project grows.

## Questions to review

1. What should stylesheet architecture help a reader do?
2. What is a Sass partial?
3. Why are partial URLs written without the underscore?
4. What belongs in a foundation module?
5. What belongs in a component module?
6. What does a BEM-style name communicate?
7. When should a module index use @forward?
8. Why should a small project avoid unnecessary folders?

| [Previous: Design tokens and themes](../chapters/12-design-tokens-and-themes.md) | [Notes index](../README.md) | [Next: Compilation, source maps, and tooling](../chapters/14-compilation-source-maps-and-tooling.md) |
|:--|:--:|--:|

