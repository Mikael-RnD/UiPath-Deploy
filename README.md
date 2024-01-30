# UiPath-Deploy
GitHub action for deploying all .nupkg packages in a provided path to UiPath Orchestrator using the [package deploy task from the UiPath CLI](https://docs.uipath.com/test-suite/automation-cloud/latest/user-guide/deploying-a-package-to-orchestrator).

## Example usage:

      # .nupkg packages are deployed to UiPath Orchestrator
      - name: UiPath Deploy
        uses: Mikael-RnD/UiPath-Deploy@v1
        with:
          # All inputs are required
          packagesPath: ${{ github.workspace }}
          orchestratorUrl: https://cloud.uipath.com/
          orchestratorTenant: # Name of tenant where packages are deployed
          orchestratorFolder: # Orchestrator Folder path where packages are deployed
          orchestratorApplicationId: # Id of External Application in Orchestrator
          orchestratorApplicationSecret: # Application Secret for External Application in Orchestrator
          orchestratorLogicalName: # Orchestrator logical name. Also known as organization id or account for app

## Inputs 
|Name|Description|Required|Example value|
|:--|:--|:--|:--|
|packagesPath|Path to a directory containing .nupkg packages for deployment to Orchestrator|True|./packages|
|orchestratorUrl|Base URL to Orchestrator instance|True|https://cloud.uipath.com/|
|orchestratorTenant|Name of the Orchestrator tenant|True|TestTenant|
|orchestratorLogicalName|Id of the UiPath organization|True|testorg|
|orchestratorFolder|The fully qualified name of the Orchestrator folder where processes are deployed to|True|Finance/SE|
|orchestratorApplicationId|Application ID for the CLI to authenticate with UiPath Orchestrator|True||
|orchestratorApplicationSecret|Application Secret for the CLI to authenticate with UiPath Orchestrator|True||
