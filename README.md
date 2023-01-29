# SETUP ARGOCD

SETUP ARGOCD ON YOUR LOCAL CLUSTER

## LOGIN AND CHANGE PASSWORD

```bash
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d | xargs argocd login --port-forward --insecure --username admin --password
export PASSWORD=$(kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo)
export NEW_PASSWORD=<NEW PASSWORD>
argocd account update-password --port-forward --account admin --current-password=$PASSWORD --new-password=$NEW_PASSWORD
```
