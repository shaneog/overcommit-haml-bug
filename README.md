### Bug Reproduction

For https://github.com/brigade/overcommit/issues/483

To reproduce:

 - Install Gems

```sh
bundle install
```

Sign overcommit configuration:
```sh
bundle exec overcommit --sign
```

Run `haml-lint`:
```sh
bundle exec haml-lint main.html.haml
```

See that no issues are reported, because it honors the `exclude` in the
configuration file for the `ConsecutiveComments` linter.

Run `overcommit` as if in CI (works on commit also):
```sh
bundle exec overcommit --run
```

Output: **fail**

```
Running pre-commit hooks
Analyze with haml-lint.....................................[HamlLint] FAILED
Unexpected output: unable to determine line number or type of error/warning for output:

1 file inspected, 1 lint detected

✗ One or more pre-commit hooks failed

```
