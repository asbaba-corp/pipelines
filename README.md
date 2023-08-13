# Overview

This repository contains centralized pipelines for all of our projects at Asbaba Corp. The pipelines are defined in YML files and are triggered by various events such as pull requests and releases.

## Pipelines

### Build Pipelines
- **Node.js Build (`build-nodejs.yml`):** Builds Node.js packages for production.
- **Python Build (`build-python.yml`):** Builds Python packages for production.

### Terraform Pipelines
- **Terraform Plan (`terraform-plan.yml`):** Generates a plan for deploying our infrastructure.
- **Terraform Apply (`terraform-apply.yml`):** Deploys our infrastructure.
- **Terraform Destroy (`terraform-destroy.yml`):** Destroys the specified infrastructure.

### Pull Request Checks
- **Node.js PR Check (`pr-check-nodejs.yml`):** Checks if the Node.js code is building correctly.
- **Python PR Check (`pr-check-python.yml`):** Checks if the Python code is building correctly and if there are no errors in the Terraform code.

### Release Pipelines
- **Development Release (`release-dev.yml`):** Deploys a new version of our application to the development environment.
- **Production Release (`release-prod.yml`):** Deploys a new version of our application to production.

## Usage

### Directory Structure

Pipelines are located in the following directory:

```
.github/workflows/<purpose>.yml
```

### Example Usage

Here's an example of how to use the Terraform plan pipeline:

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

## Custom Actions

This repository also includes custom actions for downloading and uploading artifacts:

- **Download Artifact (`download-artifact/action.yml`):** Downloads specified artifacts.
- **Upload Artifact (`upload-artifact/action.yml`):** Uploads specified artifacts.

