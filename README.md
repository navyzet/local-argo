### ArgoCD local stage

```bash
minikube start --cache-images=true --cpus='4' --memory='4g' --kubernetes-version='v1.19.16'
```

```bash
# set password admin
helm upgrade -i --create-namespace --namespace kube-argocd argocd ./charts/argo-cd --set configs.secret.argocdServerAdminPassword='$2y$10$oOy6rIuhcvRl8E8MARUEq.3UMcNA0MO0ymCUNH7yOySTWfFS8YM2a'
```

```shell
kubectl port-forward service/argocd-server -n kube-argocd 8080:443
```

```shell
helm install -n kube-argocd argocd-apps argo/argocd-apps --version 1.2.0 --values ./values/argocd-apps.yaml 
```
