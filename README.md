# btq-sre

## Introduction

My solution to the SRE problem given by BTQ on 2023/08/31

## Assumptions

1. Kubernetes cluster is hosted on Google Kubernetes Engine (GKE)
2. There are no scheduling requirements on the default node pool
3. The default node pool is at least a node with 5 vCPU and 20 GiB
4. There are no requirements on data persistence (assuming this workload is fully stateless)
5. There are no secrets (API keys, crt files, etc.) that cannot be committed into a Git repository
6. The user (or service account) executing the deployment process has the necessary permissions to do so
7. CI/CD solution is Jenkins
8. The underlining Jenkins node and node image have all the required permissions preconfigured
9. The underlining Jenkins node and node image have all the necessary binary installed

## Installation

### via local machine
```bash
$ helm upgrade --install -f configs/values.yaml -f values.yaml btq-sre .
```

NOTE: try adding `--dry-run` to view the raw YAML files without actually deploying to the preconfigured Kubernetes cluster

### via Jenkins
Depending on the Jenkins configured, ...
