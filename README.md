# mega-linter-eslint-bug-example

This repo is a minimal example of how ESLint typescript plugins require relative paths to work properly with the
mega-linter. When running `npm run lint`, there should be three errors:

```shell
  1:1   warning  Unexpected console statement                   no-console
  1:13  error    Strings must use singlequote                   @typescript-eslint/quotes
  1:28  error    Newline required at end of file but not found  eol-last
```
