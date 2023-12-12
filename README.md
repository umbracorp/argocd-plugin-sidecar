# Install ArgoCD Plugin
On a Kubernetes cluster with ArgoCD installed:
```bash
kubectl apply -f manifests/1.argo-cm-update.yaml
kubectl get cm -n argocd cmp-plugin -o yaml
kubectl -n argocd patch deployments/argocd-repo-server --patch-file manifests/2.argocd-repo-server-patch.yaml
kubectl get pods -n argocd  # argo-repo-server has restarted
kubectl apply -f manifests/3.argocd-sample-app.yaml
```