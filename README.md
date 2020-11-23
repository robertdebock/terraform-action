# Terraform action

A GitHub action to run HashiCorp Terraform commands.

## Inputs

### `action`

The command to run, for example: `validate` (default), `init`, `plan` or `apply`. Have a look at `terraform --help` for details.

### `file`

The file (including optional path) to run the Terraform command against. This can be `./main.tf` (default), but a path can also be specified, like `examples/defaults/main.tf`.

## Example usage

Here is a default configuration that run `terraform validate`.

```yaml
---
on:
  - push

jobs:
  build:
    runs-on: ubuntu-2004
    steps:
      - name: checkout
        uses: actions/checkout@v2
      - name: terraform
        uses: robertdebock/terraform-action@1.0.1
        with:
          action: init
          file: ./path/to/main.tf
```

To use another `action` on a specific terraform file, change this example to you needs:

```yaml
---
on:
  - push

jobs:
  build:
    runs-on: ubuntu-2004
    steps:
      - name: checkout
        uses: actions/checkout@v2
      - name: terraform
        uses: robertdebock/terraform-action@1.0.1
        with:
          action: init
          file: ./path/to/main.tf
```
