# API Evolution Check Action

This GitHub Action checks for breaking changes in your API specifications by comparing the current branch's API specification file with the one in the main branch. It requires a file path to your OpenAPI specification file and an access token for the API Evolution Management Service.

## Inputs

| Name          | Description                                          | Required |
|---------------|------------------------------------------------------|----------|
| `file_path`   | Path to the API specification file you want to compare | Yes      |
| `access_token`| API Evolution Management Service access token         | Yes      |

## Example

This example demonstrates how to use the action in a workflow:

```yaml
name: API Evolution Check

on:
  push:
    branches:
      - main
      - '*' # This will match any branch

jobs:
  api_evolution_check:
    runs-on: ubuntu-latest

    steps:
    - name: Run API Evolution Check
      uses: fernandomrtnz/gh-action-test@v1.0.0-beta
      with:
        file_path: openapi.yml
        access_token: ${{ secrets.APIEMS_ACCESS_TOKEN }}
```