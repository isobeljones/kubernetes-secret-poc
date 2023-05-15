# Kubernetes secret poc
This creates a simple web app where the name of the kubernetes serviceaccount is a secret from Azure Key Vault.

The ADO pipeline pulls a secret from Azure Key Vault and injects that secret into a values.yaml file which is passed to helm to create the simple web app. The values.yaml file only exists inside the 1ES agent VM for the duration of the pipeline.

## prerequisites 
- A Key vault containing a secret
- A Kubernetes cluster with helm installed 
- 1ES agents with permissions to access the Key Vault secret
- ADO Service Connection


## Instructions to run
1. Inside the `azure-pipelines.yaml` file, configure the variables (line 12-15) to match the environment you wish to deploy too.
2. Create and run ADO pipeline
3. Check the the kubernetes service account which has been deployed contains the secret name
`kubectl get serviceaccount -n hello-world`
4. Clean up resources
`helm delete ahoy -n hello-world`


