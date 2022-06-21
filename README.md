# Pre-commit action

This Github action installs and runs [pre-commit](https://pre-commit.com/),
you can use it with the [trilom/file-changes-action](https://github.com/trilom/file-changes-action)
step to check only the changed files in a PR like this:

```yaml
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-python@v3
      - id: file_changes
        uses: trilom/file-changes-action@v1.2.4
        with:
          output: ' '
      - name: self test the pre-commit action
        uses: blockchaintp/pre-commit-action@v1.0.0
        with:
          extra_args: --files ${{ steps.file_changes.outputs.files}}
```
