# Overview

This repository contains centralized pipelines for all of our projects. The pipelines are defined in YML files and are triggered by events such as pull requests and releases.

## Pipelines

The following pipelines are defined in this repository:

* **Build:** This pipeline builds packages for production.
* **Terraform plan:** This pipeline generates a plan for deploying our infrastructure.
* **Terraform apply:** This pipeline deploys our infrastructure.
* **PR check:** This pipeline checks if the code is building correctly and if there's no errors to the terraform code.
* **Release-dev:** This pipeline deploys a new version of our application to dev.
* **Release-prod:** This pipeline deploys a new version of our application to production.

## Usage
Directory structure:

`.github/workflows/<purpose>.yml`

Example:

```yaml
name: "Terraform plan"

on:
  push:
    branches:
      - main
  pull_request:

jobs:
  terraform:
      uses: "asbaba-corp/pipelines/.github/workflows/terraform-plan.yml@main"
      with:
        os_version: "ubuntu-20.04"
        working_directory: "./terraform"
```
