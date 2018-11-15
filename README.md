# goteststemplates
Template files for gotests

This repository is a customized set of template files to be used with [gotests](https://github.com/cweill/gotests)' `-template_dir` parameter.

## Differences

1. Arguments to functions are no longer split out into an `args` `struct`
2. Use require instead of reflect for comparisons
3. Use `tc` instead of `tt` (test case)
