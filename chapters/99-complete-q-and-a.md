# 17. Complete questions and answers

[Back to notes index](../README.md)

| [Previous: All code samples](98-all-code-samples.md) | [Notes index](../README.md) | [Next: Notes index](../README.md) |
|:--|:--:|--:|

## 1. SCSS foundations and setup

**1. What is Sass?**

Sass is a stylesheet language with features that are transformed into CSS by a compiler.

**2. What does SCSS describe?**

SCSS is Sass's CSS-like syntax, written in files with the .scss extension.

**3. Can a browser run an SCSS file directly?**

No. A browser consumes CSS, so SCSS must be compiled first.

**4. What does the Sass compiler produce?**

The compiler produces CSS that a browser can load.

**5. What does the .scss extension identify?**

The extension identifies a source stylesheet written with SCSS syntax.

**6. Why install Sass as a development dependency?**

Sass is a build-time tool, so it belongs with development dependencies.

**7. What does the --watch option do?**

Watch mode recompiles the source when it changes and keeps running.

**8. Why inspect generated CSS when a style is unexpected?**

Generated CSS shows the exact selectors and values the browser receives.

## 2. Variables and CSS custom properties

**9. When is a Sass variable evaluated?**

A Sass variable is resolved during compilation.

**10. Where does a CSS custom property exist?**

A CSS custom property remains in the CSS output and is resolved by the browser.

**11. Which kind of variable can change through the CSS cascade at runtime?**

A CSS custom property can be changed through the cascade at runtime.

**12. What character begins a Sass variable name?**

A Sass variable begins with a dollar sign.

**13. When is var() evaluated?**

The browser evaluates var() when it computes styles.

**14. Why are custom properties useful for themes?**

Custom properties inherit and can be overridden by a theme selector.

**15. What does !default allow a module consumer to do?**

!default lets a module consumer supply a value before the module is loaded.

**16. Which variable type should I choose for a value changed by JavaScript?**

Use a CSS custom property for a value that must change in the browser.

## 3. Nesting and parent selectors

**17. What does Sass do with nested selectors?**

Sass combines nested selectors into selectors in the generated CSS.

**18. What does the ampersand represent?**

The ampersand stands for the complete parent selector.

**19. How does &__title combine with .card?**

Inside .card, &__title becomes .card__title.

**20. What selector does a nested p create?**

The nested p becomes a descendant selector such as .card p.

**21. Why can deep nesting make CSS harder to maintain?**

Deep nesting creates long, tightly coupled selectors that are harder to reuse and override.

**22. What does &:focus-visible target?**

:focus-visible targets controls when the browser shows keyboard-style focus.

**23. Why inspect the compiled selector?**

The compiled selector reveals the actual specificity and match scope.

**24. When can a nested media query improve organization?**

A nested media query can keep a component's responsive changes beside its base rule.

## 4. Modules with @use and @forward

**25. What does @use load?**

@use loads another Sass stylesheet as a module.

**26. Why does a namespace help readers?**

A namespace shows where a variable, mixin, or function came from.

**27. How many times does the Sass module system load a module?**

A module is loaded once even if multiple files use it.

**28. What does @forward make available?**

@forward exposes module members through a public entry point.

**29. Does a forwarded member become visible inside the forwarding file automatically?**

No. The forwarding file needs its own @use to refer to the member.

**30. Where should @use appear in a stylesheet?**

Place @use at the top of a stylesheet before style rules.

**31. How can a module choose a different namespace?**

Use the as clause to set a custom namespace.

**32. Which module rules should new Sass code prefer over Sass @import?**

New Sass code should use @use and @forward rather than the deprecated Sass @import rule.

## 5. Mixins and content blocks

**33. What does a mixin group?**

A mixin groups declarations or nested rules that can be included in several places.

**34. Which at-rule defines a mixin?**

@mixin defines a mixin.

**35. Which at-rule includes a mixin?**

@include inserts a mixin's output at the current location.

**36. Why can a mixin accept arguments?**

Arguments let one reusable pattern accept different values.

**37. What does a default argument provide?**

A default argument provides a value when a caller does not pass one.

**38. What does @content insert?**

@content inserts the block written by the mixin caller.

**39. When is a content block useful?**

A content block can wrap caller rules in a common media query.

**40. Why keep mixins small and focused?**

A focused mixin has predictable output and is easier to reuse.

## 6. Functions and calculations

**41. What does a Sass function return?**

A Sass function calculates and returns a value.

**42. What should a mixin do compared with a function?**

A mixin emits declarations; a function returns a value.

**43. Which directive returns a value from a Sass function?**

@return supplies a function result.

**44. When is a custom Sass function useful?**

A custom function is useful for a consistent calculation from named inputs.

**45. What is a benefit of CSS calc()?**

calc() lets the browser combine values that may only be known at runtime.

**46. What does clamp() help express?**

clamp() expresses a value with a minimum, preferred, and maximum.

**47. Why should function inputs have clear names?**

Clear parameter names make the calculation's purpose easier to understand.

**48. Where should Sass math functions come from?**

Use the sass:math module for namespaced Sass arithmetic helpers.

## 7. Lists, maps, and built-in modules

**49. What type of data does a Sass list store?**

A list stores ordered values.

**50. What does a map associate?**

A map associates keys with values.

**51. Why use built-in Sass modules?**

Namespaces group functions and make their source clear while avoiding global collisions.

**52. Which module contains map lookup functions?**

sass:map contains map lookup operations.

**53. Which namespaced function reads an item by position from a list?**

list.nth reads the item at a one-based position.

**54. Why prefer list.nth over the legacy global nth form?**

Namespaced list functions avoid deprecated global built-ins and make intent clear.

**55. Where should Sass division helpers come from?**

Sass math helpers are in sass:math.

**56. When is a simple variable better than a map?**

A plain variable is simpler when there is only one value to store.

## 8. Placeholders and @extend

**57. What does @extend change?**

@extend combines the extending selector with a selector that owns the shared rule.

**58. What character begins a placeholder selector?**

A percent sign begins a placeholder selector.

**59. Does an unused placeholder appear in the output CSS?**

An unused placeholder is not emitted into compiled CSS.

**60. How does a selector use placeholder declarations?**

An extending selector joins the placeholder's declaration rule.

**61. When is extending a placeholder appropriate?**

Extending a placeholder works when selectors are conceptually related.

**62. Why can extending unrelated selectors create surprising output?**

Extending unrelated selectors can create unexpected selector combinations.

**63. When can a mixin be clearer than @extend?**

A mixin is clearer when declarations should be copied into separate rule contexts.

**64. What should I inspect after adding an extend relationship?**

Inspect generated CSS to see the final grouped selectors.

## 9. Interpolation and dynamic selectors

**65. What does interpolation insert?**

Interpolation inserts a Sass value into syntax such as a selector or property name.

**66. How is interpolation written in SCSS?**

Write interpolation as #{value}.

**67. When is interpolation needed in a selector?**

Use it when a Sass value must become part of a generated selector name.

**68. What does the example loop generate?**

The loop generates a finite selector for each allowed variant name.

**69. Does Sass interpolation create runtime selectors?**

No. Sass resolves interpolation while compiling.

**70. Why should generated names come from controlled values?**

Controlled values keep generated names predictable and safe to maintain.

**71. When can writing selectors directly be clearer?**

Direct selectors are clearer for a short fixed list of states.

**72. Where else can interpolation be useful?**

Interpolation can also form property names and strings.

## 10. Conditionals and loops

**73. When does Sass evaluate flow-control rules?**

Sass evaluates flow control during compilation.

**74. What does @if select?**

@if chooses which Sass block to emit.

**75. Which rule repeats over each value in a collection?**

@each repeats a block for each item in a collection.

**76. Why keep a generated scale explicit in a map?**

An explicit map documents which generated values are supported.

**77. What is one cost of generating many utility classes?**

Generating many unused classes increases output size and makes CSS harder to maintain.

**78. Can Sass flow control respond to a user's browser preference at runtime?**

No. Sass conditions run before the browser; CSS media and container queries respond at runtime.

**79. When is a direct declaration clearer than a loop?**

Direct declarations are clearer for a small fixed set of rules.

**80. Why inspect CSS generated by a loop?**

Generated CSS shows the rules the condition or loop actually emitted.

## 11. Responsive design and media queries

**81. Who evaluates a media query?**

The browser evaluates media queries using viewport, container, or preference conditions.

**82. How should I choose a breakpoint?**

Choose breakpoints when the content or layout needs more room.

**83. Why start with a narrow layout?**

A narrow-first base rule works before enhancements at wider sizes apply.

**84. What does minmax(0, 1fr) help prevent?**

minmax(0, 1fr) allows a grid track to shrink below its min-content size.

**85. When is a container query useful?**

A container query adapts a component to its own available container width.

**86. Why are Sass variables useful for some media conditions?**

Sass variables can store compile-time breakpoint values used in media query syntax.

**87. What does prefers-reduced-motion represent?**

It reflects a person's operating-system or browser motion preference.

**88. Why test widths between chosen breakpoints?**

Intermediate widths can expose wrapping, overflow, and awkward gaps between two tested sizes.

## 12. Design tokens and themes

**89. What is a design token?**

A design token is a named value for a repeated design decision.

**90. Which Sass value is resolved at compile time?**

Sass values are compiled before the browser loads the CSS.

**91. Why use CSS custom properties for runtime themes?**

CSS custom properties can be overridden at runtime for themes.

**92. What does a descendant inherit from its theme selector?**

Descendants inherit the custom property values from the selected theme scope.

**93. How can application code select a theme?**

Application code can set an attribute or class that selects a theme.

**94. Why test text contrast separately for each theme?**

Contrast must be checked for each foreground and background combination.

**95. When is a Sass map useful for tokens?**

A Sass map is useful when code must iterate over related token values.

**96. Why name a token by purpose rather than its current color?**

Purpose-based names describe the role even if the exact color changes.

## 13. Stylesheet architecture

**97. What should stylesheet architecture help a reader do?**

Architecture should help a reader locate rules and understand their dependencies.

**98. What is a Sass partial?**

A partial is a Sass source file commonly prefixed with an underscore and loaded as a module.

**99. Why are partial URLs written without the underscore?**

The underscore indicates a partial but is omitted from the module URL.

**100. What belongs in a foundation module?**

Foundation modules contain shared setup such as tokens, reset, and typography.

**101. What belongs in a component module?**

Component modules hold rules for a particular interface component.

**102. What does a BEM-style name communicate?**

A BEM-style name communicates a component and its element or modifier relationship.

**103. When should a module index use @forward?**

@forward is useful when a module intentionally provides one public entry point.

**104. Why should a small project avoid unnecessary folders?**

A small project should add folders only when they make related rules easier to find.

## 14. Compilation, source maps, and tooling

**105. What does Sass compilation produce?**

Compilation transforms SCSS source into browser-readable CSS.

**106. What does watch mode do?**

Watch mode waits for source edits and recompiles them.

**107. Where does npm record the installed Sass version?**

npm and its lockfile record the installed Sass version.

**108. What does a source map connect?**

A source map links generated CSS positions back to source SCSS locations.

**109. Why is expanded output useful during development?**

Expanded output is easier to inspect while developing.

**110. Why might compressed output be used for release?**

Compressed output reduces whitespace and file size for delivery.

**111. What should I inspect first after a compiler error?**

Start with the file and line reported, then inspect syntax, module paths, and units nearby.

**112. Why keep the build command repeatable?**

Repeatable commands give local work and automated builds the same steps.

## 15. Accessibility, performance, and migration

**113. Which visual cue should remain available to keyboard users?**

Keep a visible focus indicator for people navigating by keyboard.

**114. Why test text contrast?**

Contrast helps make text and controls readable against their backgrounds.

**115. How can excessive nesting harm output?**

Deep nesting can create long selectors and surprising specificity.

**116. What should I inspect after changing a loop?**

Inspect the compiled output to see every selector and declaration the loop emitted.

**117. When may plain CSS be enough without Sass?**

Plain CSS is sufficient when the stylesheet needs only a few ordinary declarations.

**118. Which module rules should new code use?**

Use @use and @forward for new Sass modules.

**119. What should I review after running a migration tool?**

Review namespace changes, emitted CSS, warnings, and library behavior after migration.

**120. Which browser checks help confirm accessible styling?**

Check keyboard focus, contrast, zoom, motion preferences, and several viewport sizes.

## Cross-topic review

**121. Why should SCSS be compiled before deployment?**

Browsers load the generated CSS, while the SCSS source is processed by the build tool.

**122. What is the main difference between @use and @forward?**

@use makes a module available to the current stylesheet; @forward re-exports its public members.

**123. Why avoid importing Sass members into one global namespace?**

Global names can collide and make each variable or mixin's source hard to identify.

**124. When should I choose a mixin over @extend?**

Choose a mixin when a set of declarations should be included in separate selector contexts.

**125. Why is a runtime CSS custom property better for a switchable theme?**

The browser can change its value through the cascade without recompiling SCSS.

**126. Can a Sass loop respond to the current viewport width?**

No. It runs during compilation; use CSS media or container queries for browser conditions.

**127. What does a source map help me do?**

It helps browser developer tools point from generated CSS back to the SCSS source.

**128. What should I verify after changing Sass architecture?**

Compile the project and review module paths, generated CSS, accessibility, and visual behavior.

| [Previous: All code samples](98-all-code-samples.md) | [Notes index](../README.md) | [Next: Notes index](../README.md) |
|:--|:--:|--:|
