















Apart from UI,ArgoCD also has a CLI. The installation steps are shown below. [Source](https://argo-cd.readthedocs.io/en/stable/getting_started/)

Download the latest Argo CD version from https://github.com/argoproj/argo-cd/releases/latest. More detailed installation instructions can be found via the CLI installation documentation.

Also available in Mac, Linux and WSL Homebrew:

```bash
    brew install argocd
```

We can connect using:  `argocd login`

```bash
(⎈ |kind-argo-cluster:default)╭─victormartinez@mac-MacBook-Pro ~/labs/argocd
╰─$ argocd login localhost:8080                                                       
WARNING: server certificate had error: x509: “Argo CD” certificate is not trusted. Proceed insecurely (y/n)? y
Username: admin
Password:
'admin:login' logged in successfully
Context 'localhost:8080' updated
```

Try the following commands
- `argocd app list`
- `argocd app get demo`
- `argocd app history demo`

````bash
(⎈ |kind-argo-cluster:default)╭─victormartinez@mac-MacBook-Pro ~/labs/argocd
╰─$ argocd app list
NAME  CLUSTER                         NAMESPACE  PROJECT  STATUS  HEALTH   SYNCPOLICY  CONDITIONS  REPO                                       PATH          TARGET
demo  https://kubernetes.default.svc  default    default  Synced  Healthy  Auto        <none>      https://github.com/vthot4/Research-ArgoCD  ./labs/lab01  HEAD
````
```bash
(⎈ |kind-argo-cluster:default)╭─victormartinez@mac-MacBook-Pro ~/labs/argocd
╰─$ argocd app get demo
Name:               demo
Project:            default
Server:             https://kubernetes.default.svc
Namespace:          default
URL:                https://localhost:8080/applications/demo
Repo:               https://github.com/vthot4/Research-ArgoCD
Target:             HEAD
Path:               ./labs/lab01
SyncWindow:         Sync Allowed
Sync Policy:        Automated
Sync Status:        Synced to HEAD (a7c5ad6)
Health Status:      Healthy

GROUP  KIND        NAMESPACE  NAME               STATUS  HEALTH   HOOK  MESSAGE
       Service     default    simple-service     Synced  Healthy        service/simple-service unchanged
apps   Deployment  default    simple-deployment  Synced  Healthy        deployment.apps/simple-deployment configured
```

```bash
(⎈ |kind-argo-cluster:default)╭─victormartinez@mac-MacBook-Pro ~/labs/argocd
╰─$ argocd app history demo
ID  DATE                           REVISION
0   2023-01-18 22:33:19 +0100 CET  HEAD (02ceb24)
1   2023-01-18 22:37:19 +0100 CET  HEAD (02ceb24)
2   2023-01-18 22:40:57 +0100 CET  HEAD (b4b4d8c)
```

```shell
(⎈ |kind-argo-cluster:default)╭─victormartinez@mac-MacBook-Pro ~/labs/argocd
╰─$ argocd app delete demo
Are you sure you want to delete 'demo' and all its resources? [y/n]
y

(⎈ |kind-argo-cluster:default)╭─victormartinez@mac-MacBook-Pro ~/labs/argocd
╰─$ argocd app list
NAME  CLUSTER  NAMESPACE  PROJECT  STATUS  HEALTH  SYNCPOLICY  CONDITIONS  REPO  PATH  TARGET
```
