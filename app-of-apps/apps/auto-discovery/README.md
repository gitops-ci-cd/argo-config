# Auto Discovery

These ApplicationSets are designed to automatically discover and deploy applications.

## Usage

- **deployment**

  This ApplicationSet is responsible for ensuring that kustomize overlays from repositories suffixed with `-deployment` are applied to their respective environments. The following labels **MUST** be added (easily via the Argo CD UI) to any cluster that you want apps deployed to:

  - kubernetes.io/environment

- **pull-requests**

  This ApplicationSet is responsible for deploying PR-specific environments. If a pull request is labeled with <https://github.com/gitops-ci-cd/argo-config/labels/preview>, a preview environment will be created, and a GitHub Deployment tracked.

## Reference

The following documentation should be reviewed for more information:

- [ApplicationSet](https://argo-cd.readthedocs.io/en/latest/operator-manual/applicationset/)
- [Matrix Generator](https://argo-cd.readthedocs.io/en/latest/operator-manual/applicationset/Generators-Matrix/)
- [SCM Provider Generator](https://argo-cd.readthedocs.io/en/latest/operator-manual/applicationset/Generators-SCM-Provider/)
- [Git Generator](https://argo-cd.readthedocs.io/en/latest/operator-manual/applicationset/Generators-Git/)
- [Pull Request Generator](https://argo-cd.readthedocs.io/en/latest/operator-manual/applicationset/Generators-Pull-Request/)
- [Cluster Generator](https://argo-cd.readthedocs.io/en/latest/operator-manual/applicationset/Generators-Cluster/)
- [Kustomize](https://argo-cd.readthedocs.io/en/latest/user-guide/kustomize/)
- [Go Template](https://argo-cd.readthedocs.io/en/latest/operator-manual/applicationset/GoTemplate/)
- [Sync Options](https://argo-cd.readthedocs.io/en/latest/user-guide/sync-options/)