# goteststemplates
Template files for gotests

This repository is a customized set of template files to be used with [gotests](https://github.com/cweill/gotests)' `-template_dir` parameter.

## Differences

1. Arguments to functions are no longer split out into an `args` `struct`
2. Use require instead of reflect for comparisons
3. Use `tc` instead of `tt` (test case)

### Example

Go code:

```golang
func tester(testing string) (blahblah string, blahblah2 string, blahblah3 string, err error) {
    return "", "", "", nil
}
```

Test code:

```golang
func Test_tester(t *testing.T) {
    tests := []struct {
        name          string
        testing       string
        wantBlahblah  string
        wantBlahblah2 string
        wantBlahblah3 string
        expectedErr   error
    }{
        // TODO: Add test cases.
    }
    for _, tc := range tests {
        t.Run(tc.name, func(t *testing.T) {
            gotBlahblah, gotBlahblah2, gotBlahblah3, err := tester(tc.testing)

            require.Equal(t, tc.expectedErr, err)
            require.Equal(t, tc.wantBlahblah, gotBlahblah)
            require.Equal(t, tc.wantBlahblah2, gotBlahblah2)
            require.Equal(t, tc.wantBlahblah3, gotBlahblah3)
        })
    }
}
```

## Vscode usage

Checkout this repo and add the following to your user settings:

```json
{
 "go.generateTestsFlags": [
        "-template_dir",
        "<path-to-folder>/dotlou/goteststemplates/templates"
    ],
}
```
