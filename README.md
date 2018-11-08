# Azure_Container_Registry
How to create an ACR and push up an image

- az account set --subscription "My Demos"
- az acr create --resource-group Epick8s --name epicacr --sku Basic
- az acr list --resource-group Epick8s --query "[].{acrLoginServer:loginServer}" --output table
- docker tag buildmystartup/basicnodeapp epicacr.azurecr.io/basicnodeapp
- az ad sp create-for-rbac --scopes /subscriptions/yoursubscriptionnumber/resourceGroups/Epick8s/providers/Microsoft.ContainerRegistry/registries/epicacr --role Contributor --name epicpushacr
- docker login epicacr.azurecr.io -u ff33780d-f27e-46a4-8a21-6bf54ddf685d
- docker push epicacr.azurecr.io/basicnodeapp
