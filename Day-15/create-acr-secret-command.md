# Command to create ACR ImagePullSecret

```
kubectl create secret docker-registry <secret-name> \
    --namespace <namespace> \
    --docker-server=<container-registry-name>.azurecr.io \
    --docker-username=<service-principal-ID> \
    --docker-password=<service-principal-password> 
```

```
kubectl create secret docker-registry acr-secret \
    --namespace default \
    --docker-server=votingappcontainerx.azurecr.io \
    --docker-username=votingappcontainerx \
    --docker-password=mCJayjsdjkfnenjloaulhenrajdgfhjasda90 
```
