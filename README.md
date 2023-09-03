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
10. Redeploying all pods on the cluster is not restricted (workload should be configured to a rolling update)
11. Prometheus is installed and configured to automatically scrape data from Kubernetes services

## Installation

### via local machine
```bash
$ helm upgrade --install -f configs/values.yaml -f values.yaml btq-sre .
```

NOTE: try adding `--dry-run` to view the raw YAML files without actually deploying to the preconfigured Kubernetes cluster

### via Jenkins
Depending on the Jenkins configured, ...

## Configuration

### How to modify geth eth network
1. Check and find the network ID of the network you want
2. Using the network ID, modify **NetworkId** in helm/configs/values.yaml (under *[Eth]*)
3. Redeploy the helm deployment

## List of Metrics to Monitor

### System (VM) related
1. CPU
2. Memory
3. Disk space
4. Disk IOPs
5. File descriptor
6. Network throughput

### Application related
1. Rate of transactions
2. Transaction duration
3. Rate of chain executions
4. Rate of chain validations
5. Rate of chain writes
6. Rate of chain account reads/writes/updates/hashes/commits
7. Rate of chain storage reads/writes/updates/hashes/commits
