# 5. Mixins and content blocks

[Back to notes index](../README.md)

| [Previous: Modules with @use and @forward](../chapters/04-modules-use-and-forward.md) | [Notes index](../README.md) | [Next: Functions and calculations](../chapters/06-functions-and-calculations.md) |
|:--|:--:|--:|

## What I am learning here

A mixin groups declarations that I want to reuse. It can accept arguments, emit nested rules, and include a content block from the caller. A mixin is useful when several selectors need the same set of declarations or when it expresses a small styling pattern.

## Define and include a mixin

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

Arguments make a mixin adaptable without copying its body. Default values make common usage short. Include mixins in the scope where the emitted rules belong.

A content block lets the caller provide nested rules to a mixin:

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

Use content blocks for a clear wrapper pattern such as a media query. If each call emits a large set of declarations, the compiled CSS can grow. Prefer native CSS properties when they already express the same behavior, and keep mixins focused so their output is predictable.

## Questions to review

1. What does a mixin group?
2. Which at-rule defines a mixin?
3. Which at-rule includes a mixin?
4. Why can a mixin accept arguments?
5. What does a default argument provide?
6. What does @content insert?
7. When is a content block useful?
8. Why keep mixins small and focused?

| [Previous: Modules with @use and @forward](../chapters/04-modules-use-and-forward.md) | [Notes index](../README.md) | [Next: Functions and calculations](../chapters/06-functions-and-calculations.md) |
|:--|:--:|--:|

