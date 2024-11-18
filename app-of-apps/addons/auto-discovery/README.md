# Auto Discovery

These ApplicationSets are designed to automatically discover and deploy applications.

## Usage

- **addon**

  This ApplicationSet is responsible for ensuring that kustomize overlays from repositories suffixed with `-addon` are applied to their respective environments. The following labels **MUST** be added (easily via the Argo CD UI) to any cluster that you want apps deployed to:

  - kubernetes.io/environment

## Reference

The following documentation should be reviewed for more information:

- [ApplicationSet](https://argo-cd.readthedocs.io/en/latest/operator-manual/applicationset/)
- [Matrix Generator](https://argo-cd.readthedocs.io/en/latest/operator-manual/applicationset/Generators-Matrix/)
- [SCM Provider Generator](https://argo-cd.readthedocs.io/en/latest/operator-manual/applicationset/Generators-SCM-Provider/)
- [Git Generator](https://argo-cd.readthedocs.io/en/latest/operator-manual/applicationset/Generators-Git/)
- [Cluster Generator](https://argo-cd.readthedocs.io/en/latest/operator-manual/applicationset/Generators-Cluster/)
- [Go Template](https://argo-cd.readthedocs.io/en/latest/operator-manual/applicationset/GoTemplate/)
- [Sync Options](https://argo-cd.readthedocs.io/en/latest/user-guide/sync-options/)