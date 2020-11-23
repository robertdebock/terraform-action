# Terraform action

A GitHub action to run HashiCorp Terraform commands.

## Inputs

### `action`

The command to run, for example: `validate` (default), `init`, `plan` or `apply`. Have a look at `terraform --help` for details.

### `directory`

The directory where the Terraform files can be found. This defaults to `./`, but can be set to i.e. `./example`.

## Example usage

Here is a default configuration that run only `terraform init`.

```yaml
---
on:
  - push

jobs:
  build:
    runs-on: ubuntu-20.04
    steps:
      - name: checkout
        uses: actions/checkout@v2
      - name: terraform
        uses: robertdebock/terraform-action@1.0.2
```

To use another `action` on a specific terraform directory, change this example to you needs:

```yaml
---
on:
  - push

jobs:
  build:
    runs-on: ubuntu-20.04
    steps:
      - name: checkout
        uses: actions/checkout@v2
      - name: terraform
        uses: robertdebock/terraform-action@1.0.2
        with:
          action: init
          directory: ./example
```
