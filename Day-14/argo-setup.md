# Commands to set up ArgoCD

Change the aks context to votingk8s
```
az aks get-credentials  --name votingk8s  --overwrite-existing  --resource-group votingappcicd
```

Check the pods in votingk8s
```
kubectl get pods
```

Configure argocd into votingk8s cluster
```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

Check the pods in argocd
```
kubectl get pods -n argocd 
```

```
kubectl get pods -n argocd 

kubectl get secrets -n argocd
```

copy the argocd-initial-admin-secret
```
kubectl edit secret argocd-initial-admin-secret -n argocd
```

copy the password and exit from edit mode  
c25rT3dzRVpKOElYdm9OdA==      , admin

decode the secret to base 64
```
echo paswordText | base64 —decode
```

copy the password somewhere snkOwsEZJ8IXvoNt  , username is admin
 
To access argocd on the UI,
Change the argocd server to NodePort mode from ClusterIP
```
kubectl get svc -n argocd 
```
```
kubectl edit svc argocd-server -n argocd
```

```
kubectl get svc -n argocd
```

copy the port number for http 31198 

to get the external ip of the argocd server
```
kubectl get nodes -o wide
```
copy the external IP  20.55.202.97

Go to azure, search for vmss

check the instances , check the network of the instance and inbound rules
add inbound rule, add destination port to the port copied earlier

now go to the browser and enter the external IP: port copied earlier and see argoCD UI  
20.55.202.97:31198

## Setup the argoCD to connect Azure repository
Go to settings and connect repo
https, get the repo url for https (the one for git clone)

Get access token from azure devops,
set up a new one and give read permission
copy the token 

configure the repository url as follows

https://tokenCopied@repo-url

it should be connected now

