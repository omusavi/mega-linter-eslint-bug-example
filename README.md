# mega-linter-eslint-bug-example

This repo is a minimal example of how ESLint typescript plugins require relative paths to work properly with the
mega-linter. When running `npm run lint`, there should be three errors:

```shell
  1:1   warning  Unexpected console statement                   no-console
  1:13  error    Strings must use singlequote                   @typescript-eslint/quotes
  1:28  error    Newline required at end of file but not found  eol-last
```

Running with the latest mega-linter version returns the following against this repo:

```shell
[eslint] command: ['eslint', '--no-ignore', '-c', '/tmp/lint/.eslintrc.json', '--no-eslintrc', '/tmp/lint/index.ts']
[eslint] CWD: /
[eslint] result: 1 
/tmp/lint/index.ts
  0:0  error  Parsing error: Cannot read file '/tsconfig.json'

✖ 1 problem (1 error, 0 warnings
```

The error is that CWD is set to `/` for eslint, however many processes within ESLint depend on the eslint run being
relative to the package.json and other files within the root of the repository.