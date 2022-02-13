# UiPath-Deploy
GitHub action for deploying nuget packages to UiPath Orchestrator. 

Example usage:

      # .nupkg packages are deployed to UiPath Orchestrator
      - name: UiPath Deploy
        uses: Mikael-RnD/UiPath-Deploy@main
        with:
          # All inputs are required
          orchestratorUrl: # Link to UiPath Orchestrator instance
          orchestratorTenant: # Name of tenant where packages are deployed
          orchestratorFolder: # Orchestrator Folder path where packages are deployed
          orchestratorUsername: # Account for deploying with
          orchestratorPassword: # Password for basic authentication
