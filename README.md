# Reusable Terraform Actions using Terraform Cloud

An action that can be used to deploy with Terraform Cloud.

Create a workflow from your repository that looks like this. 

``` yaml
jobs:
  terraform:
    runs-on: ubuntu-latest
    name: Terraform
    environment: env_example # if you want to use secrets tied to an environment, define an environment in your repository (e.g. 'env_example')
    steps:
      - uses: actions/checkout@v3
      - uses: javiercavlop/terraform-cloud-actions@v1.0.0
        with:
          tf-api-token: ${{ secrets.TF_API_TOKEN }}
          working-directory: '.' # or another file path like folder/another-folder
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          terraform-version: 1.3.7 # your version of Terraform
```

Make sure you add the following permissions in the GitHub workflow.

``` yaml
permissions:
  contents: read
  pull-requests: write
```

### Disclaimer
This project is based on a tutorial at [developer.hashicorp.com](https://www.developer.hashicorp.com) (and, therefore, includes code from it), available [here](https://developer.hashicorp.com/terraform/tutorials/automation/github-actions).