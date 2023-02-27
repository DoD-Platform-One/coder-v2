# coder

Coder moves developer workspaces to your cloud and centralizes their creation and management.

## Upstream References
* <https://coder.com>

* <https://github.com/coder/coder/tree/main/helm>

## Learn More
* [Application Overview](docs/overview.md)
* [Other Documentation](docs/)

## Pre-Requisites

* Kubernetes Cluster deployed
* Kubernetes config installed in `~/.kube/config`
* Helm installed

Kubernetes: `>= 1.19.0-0`

Install Helm

https://helm.sh/docs/intro/install/

## Deployment

* Clone down the repository
* cd into directory
```bash
helm install coder chart/
```