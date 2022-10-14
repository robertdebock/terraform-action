# Terraform action

A GitHub action to run HashiCorp Terraform commands.

## Inputs

### `action`

The command to run, for example: `validate`, `init` (default), `plan` or `apply`. Have a look at `terraform --help` for details.

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
        uses: robertdebock/terraform-action@1.1.4
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
      - name: terraform init
        uses: robertdebock/terraform-action@1.1.4
        with:
          action: init
          directory: ./example
      - name: terraform validate
        uses: robertdebock/terraform-action@1.1.4
        with:
          action: validate
          directory: ./example
      - name: terraform plan
        uses: robertdebock/terraform-action@1.1.4
        with:
          action: plan
          directory: ./example
      - name: terraform apply
        uses: robertdebock/terraform-action@1.1.4
        with:
          action: apply
          directory: ./example
        env:
          TF_CLI_ARGS: "-input=false -auto-approve"
```
