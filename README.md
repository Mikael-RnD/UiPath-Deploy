# UiPath-Deploy

GitHub action for deploying all .nupkg packages in a provided path to UiPath Orchestrator using the [package deploy task from the UiPath CLI](https://docs.uipath.com/automation-ops/automation-cloud/latest/user-guide/executing-tasks-cli#deploying-a-package-to-orchestrator).

**Note:** The current version of this action is only compatible with Windows runners

## Setup

This action requires the following items to be configured:

- UiPath CLI installed on GitHub Actions Runner. This can be done by running the [setup-uipath action](https://github.com/Mikael-RnD/setup-uipath) before this action
- [An external application created in Orchestrator](https://docs.uipath.com/automation-cloud/automation-cloud/latest/admin-guide/managing-external-applications) with the access scopes specified in the [UiPath CLI documentation](https://docs.uipath.com/automation-ops/automation-cloud/latest/user-guide/executing-tasks-cli#api-access-application-scopes). With the credentials passed to this actions input from GitHub Secrets (or other safe credential stores)

## Example usage

### Required inputs only

```yml
      # .nupkg packages are deployed to UiPath Orchestrator
      - name: UiPath Deploy
        uses: Mikael-RnD/UiPath-Deploy@v1
        with:
          packagesPath: ${{ github.workspace }}
          orchestratorTenant: MyTenant
          orchestratorFolder: "MyFolder/Test" 
          orchestratorApplicationId: ${{ secrets.ORCHESTRATOR_APP_ID }}
          orchestratorApplicationSecret: ${{ secrets.ORCHESTRATOR_APP_SECRET }}
          orchestratorLogicalName: myorg
```

### All inputs used

```yml
      # .nupkg packages are deployed to UiPath Orchestrator
      - name: UiPath Deploy
        uses: Mikael-RnD/UiPath-Deploy@v1
        with:
          packagesPath: ${{ github.workspace }}
          orchestratorUrl: https://mycompany.orchestrator.com/
          orchestratorTenant: MyTenant
          orchestratorFolder: "MyFolder/Test" 
          orchestratorApplicationId: ${{ secrets.ORCHESTRATOR_APP_ID }}
          orchestratorApplicationSecret: ${{ secrets.ORCHESTRATOR_APP_SECRET }}
          orchestratorLogicalName: myorg
          orchestratorApplicationScope: "OR.Assets OR.BackgroundTasks OR.Execution OR.Folders OR.Jobs OR.Machines.Read OR.Monitoring OR.Robots.Read OR.Settings.Read OR.TestSets OR.TestSetExecutions OR.TestSetSchedules OR.Users.Read"
```

## Inputs

|Name|Description|Required|Default value|
|:--|:--|:--|:--|
|**packagesPath**|Path to a directory containing .nupkg packages for deployment to Orchestrator|False|`${{ github.workspace }}`|
|**orchestratorUrl**|Base URL to Orchestrator instance|False|<https://cloud.uipath.com/>|
|**orchestratorTenant**|Name of the Orchestrator tenant|True||
|**orchestratorLogicalName**|Id of the UiPath organization|True||
|**orchestratorFolder**|The fully qualified name of the Orchestrator folder where processes are deployed to|True||
|**orchestratorApplicationId**|Application ID for the CLI to authenticate with UiPath Orchestrator|True||
|**orchestratorApplicationSecret**|Application Secret for the CLI to authenticate with UiPath Orchestrator|True||
|**orchestratorApplicationScope**|The accesss scope setup for the external application|False|"OR.Assets OR.BackgroundTasks OR.Execution OR.Folders OR.Jobs OR.Machines.Read OR.Monitoring OR.Robots.Read OR.Settings.Read OR.TestSets OR.TestSetExecutions OR.TestSetSchedules OR.Users.Read"|
