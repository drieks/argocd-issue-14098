# argocd-issue-14098

Minimal reproduction example for [argoproj/argo-cd#14098](https://github.com/argoproj/argo-cd/issues/14098).

## Install

```bash
kubectl apply --server-side -f https://raw.githubusercontent.com/drieks/argocd-issue-14098/main/example.yaml
```

1. Open the app `argocd-issue-14098` in the ArgoCD UI
2. Everything should be green (Synced / Healthy)
3. Click on Sync
4. Everything should still be green

## Reproduce

```bash
kubectl apply --server-side -f https://raw.githubusercontent.com/drieks/argocd-issue-14098/main/test/error.yaml --subresource=status
```

1. Click on Sync again
2. A sync error should appear

## Uninstall

```bash
kubectl delete -f https://raw.githubusercontent.com/drieks/argocd-issue-14098/main/example.yaml
kubectl delete crd errors.example.com
```
