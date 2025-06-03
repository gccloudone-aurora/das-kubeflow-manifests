## Kubeflow Manifests for DAS

The Kubeflow installation manifests for Data Analytics Services (DAS).

## Prerequisites

- **[K3D][k3d-install]** (local testing)
- **[kubectl][kubectl-install]**
- **[Taskfile][taskfile-install]**

## Commands

Generate and save the rendered manifests to a local directory for debugging:

```sh
# kubectl kustomize stacks/das
task stack:das:preview
```

Deploy Kubeflow on top of the Aurora Platform (AUR):

```sh
# kubectl apply --kustomize stacks/das
task stack:das
```

## Documentation

This kustomize folder exactly matches the upstream Kubeflow Manifests repository in its naming and folder hierarchy.

- **[Kubeflow Manifests][kubeflow-manifests]**

While the upstream location is organized under three (3) main directories we have added an additional one for `stacks`.

| Directory | Purpose                                                                                               |
| --------- | ----------------------------------------------------------------------------------------------------- |
| `apps`    | Kubeflow's official components, as maintained by the respective Kubeflow WGs                          |
| `common`  | Common services, as maintained by the Manifests WG                                                    |
| `contrib` | 3rd party contributed applications, which are maintained externally and are not part of a Kubeflow WG |
| `stacks`  | Different type of configurations for Kubeflow and its dependencies (`das`, `argo`, `upstream`)        |

## Stacks

Different type of configurations for Kubeflow and its dependencies.

| Directory  | Purpose                                                                                        |
| ---------- | ---------------------------------------------------------------------------------------------- |
| `das`      | Installs Kubeflow on top of Aurora Platform (AUR)                                              |
| `argo`     | Provides ArgoCD Application Metadata for the `das` stack                                       |
| `local`    | Necessary adjustments for running the `das` stack on a local, dev, and CI environment          |
| `upstream` | Installs Kubeflow upstream along with the DAS kustomizations without the Cloud Native Platform |

### DAS

The `das` stack expects to be installed on top of the Aurora Platform which already provides some of the base dependencies.

<!-- Links Referenced -->

[k3d-install]:             https://k3d.io/v5.2.2/#installation
[kubeflow-manifests]:      https://github.com/kubeflow/manifests
[kubectl-install]:         https://kubernetes.io/docs/tasks/tools/#kubectl
[taskfile-install]:        https://taskfile.dev/#/installation
