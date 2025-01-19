# Argo CD Configuration

[Argo CD](https://argo-cd.readthedocs.io/en/stable/) is a declarative, GitOps continuous delivery tool for Kubernetes. This repository contains the configuration for Argo, as [apps of apps](https://argo-cd.readthedocs.io/en/stable/operator-manual/cluster-bootstrapping/), so that we can bootstrap the Argo CD installation to manage itself.

## Usage

<https://argo-cd.readthedocs.io/en/stable/understand_the_basics/>

### Bootstrap

The [argo](./argo/) directory contains the installation files for Argo CD.

<https://argo-cd.readthedocs.io/en/stable/getting_started/#1-install-argo-cd>

```sh
# Install ArgoCD. This same kustomization will be used for ArgoCD to manage itself.
kubectl apply -k argo/overlays/local

# Give ArgoCD a root application to manage the rest of the applications via AoA
kubectl apply -f ./app-of-apps/application.yaml
```

<http://argo.localhost> will provide the Argo CD UI!

### Configuration

The [argo](./argo/) directory also contains the configuration for Argo CD, itself.

Argo CD applications, projects and settings can be defined declaratively using Kubernetes manifests.

<https://argo-cd.readthedocs.io/en/stable/operator-manual/declarative-setup/>

We'll be relying on the secrets generated by Argo to help us install addons. GitOps is tricky, since the cluster secrets are created ad hoc. We'll need to make some changes to the secrets per the [documentation](https://argo-cd.readthedocs.io/en/latest/operator-manual/applicationset/Generators-Cluster/#deploying-to-the-local-cluster).

- Rename the in-cluster cluster to in-cluster-hub (or whatever works for your organization) via the UI.
- Add labels to clusters via the UI. The following labels **MUST** be added **all** clusters:
  - kubernetes.io/environment = [sandbox/production]

### Applications

The [app-of-apps](./app-of-apps/) directory contains the configuration for the Argo CD AoA that manages the rest of the applications.

See [addons](./app-of-apps/addons/) to enable additional functionality for Kubernetes clusters. All clusters managed by Argo CD will have these addons installed.

See [apps](./app-of-apps/apps/) to deploy User-space applications to Kubernetes clusters.
