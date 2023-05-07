# API Evolution Check Action

This GitHub Action checks for breaking changes in your API specifications by comparing the current branch's API specification file with the one in the main branch. It requires a file path to your OpenAPI specification file and an access token for the API Evolution Management Service.

## Usage

Add the following workflow configuration (e.g., `.github/workflows/api_check.yml`) to your repository:

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
      uses: <your-github-username>/gh-action-test-tostones@<tag-or-branch>
      with:
        file_path: path/to/api/specification/file.yaml
        access_token: ${{ secrets.API_EVOLUTION_ACCESS_TOKEN }}
```

Replace `<your-github-username>` with the actual GitHub username and `<tag-or-branch>` with the desired version (e.g., `v1` or `main`) of the action. Also, replace `path/to/api/specification/file.yaml` with the path to your OpenAPI specification file.

For the `access_token` input, use the `secrets` context to store and retrieve the API Evolution Management Service access token securely. Create a secret in your repository (e.g., named `API_EVOLUTION_ACCESS_TOKEN`) and store the access token there.

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
      uses: <your-github-username>/gh-action-test-tostones@v1
      with:
        file_path: api/openapi.yaml
        access_token: ${{ secrets.API_EVOLUTION_ACCESS_TOKEN }}
```

Replace `<your-github-username>` with the actual GitHub username and `v1` with the desired version of the action.