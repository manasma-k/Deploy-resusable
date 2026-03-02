# Resources

Reusable deployment workflows for Azure resources.

## Reusable workflow

This repository exposes a reusable GitHub Actions workflow to deploy Terraform root modules from `manasma-k/landingzone`.

Workflow path:

- `.github/workflows/deploy-landingzone-root-module.yml`

### Required caller secrets

- `AZURE_CLIENT_ID`
- `AZURE_TENANT_ID`
- `AZURE_SUBSCRIPTION_ID`

### Example caller workflow

```yaml
name: Deploy Landing Zone Module

on:
	workflow_dispatch:

jobs:
	deploy-foundation-dev:
		uses: manasma-k/Deploy-resusable/.github/workflows/deploy-landingzone-root-module.yml@main
		with:
			environment: dev
			module_path: environments/dev/foundation
			tfvars_file: environments/dev/foundation/dev.tfvars
			apply: true
		secrets: inherit
```