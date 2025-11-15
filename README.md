# Home Lab

My home lab configuration consumed by Flux

## Overview

This repository contains the Kubernetes manifests for my home lab, managed declaratively with GitOps using [Flux](https://fluxcd.io/).

### Architecture

The diagram below illustrates the GitOps workflow for this cluster. Flux monitors this repository and automatically applies any changes to the Kubernetes cluster. Applications are organized by namespace within the `kubernetes/apps` directory.

```mermaid
graph TD
    subgraph "Git Repository (home-lab)"
        A[kubernetes/apps/*]
    end

    subgraph "Kubernetes Cluster"
        B(FluxCD)
        subgraph "Namespaces"
            C[pihole]
            D[...]
        end
    end

    A -- "watches" --> B
    B -- "applies kustomizations" --> C
    B -- "applies kustomizations" --> D
```
