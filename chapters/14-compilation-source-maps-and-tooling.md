# 14. Compilation, source maps, and tooling

[Back to notes index](../README.md)

| [Previous: Stylesheet architecture](../chapters/13-stylesheet-architecture.md) | [Notes index](../README.md) | [Next: Accessibility, performance, and migration](../chapters/15-accessibility-performance-and-migration.md) |
|:--|:--:|--:|

## What I am learning here

Compilation turns SCSS source into CSS. A build can run Sass once, watch files during development, or invoke Sass as part of a larger tool. Source maps connect generated CSS back to the original SCSS when browser developer tools inspect a rule.

## Add repeatable project scripts

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

After installing Sass, npm records its concrete version in package.json or the lockfile. Run npm run sass:build for a one-time build and npm run sass:watch while editing. Keep generated CSS in the path your HTML or application actually loads.

The Sass CLI supports readable expanded output and smaller compressed output. Source maps are useful during development because a browser can show the original SCSS location. A release build may use different source-map settings depending on the deployment and debugging needs.

When compilation fails, read the file and line in the error first. Check missing braces, misspelled module paths, undefined variables, and unit mismatches. Keep the command repeatable so the same build can run locally and in automation.

## Questions to review

1. What does Sass compilation produce?
2. What does watch mode do?
3. Where does npm record the installed Sass version?
4. What does a source map connect?
5. Why is expanded output useful during development?
6. Why might compressed output be used for release?
7. What should I inspect first after a compiler error?
8. Why keep the build command repeatable?

| [Previous: Stylesheet architecture](../chapters/13-stylesheet-architecture.md) | [Notes index](../README.md) | [Next: Accessibility, performance, and migration](../chapters/15-accessibility-performance-and-migration.md) |
|:--|:--:|--:|

