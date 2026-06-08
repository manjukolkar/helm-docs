# helm-docs

# Why Helm?
Imagine deploying an application:

deployment.yaml
service.yaml
ingress.yaml
configmap.yaml
secret.yaml
hpa.yaml

For every environment:

Dev
QA
UAT
Prod

You maintain multiple copies.

# Solution
Helm = Package Manager for Kubernetes

Just like:
apt → Ubuntu
yum → RHEL
pip → Python
npm → NodeJS

Helm manages Kubernetes applications.

                +----------------+
                | Helm Client    |
                +----------------+
                       |
                       |
              helm install
                       |
                       v
                +----------------+
                | Kubernetes     |
                | Cluster        |
                +----------------+


# For Microk8s

Check weather kubeconfig exist:

echo $KUBECONFIG
ls -la ~/.kube
mkdir -p ~/.kube
microk8s config > ~/.kube/config

# Install Helm:
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 

confirm helm installation:
helm version

# Chart

A Chart is a package containing Kubernetes manifests.

Example:

deployment.yaml
service.yaml
ingress.yaml

# Add Helm Repository
helm repo add bitnami https://charts.bitnami.com/bitnami

Verify:
helm repo list


# Helm Commands Cheat Sheet

## Verify Helm Installation

Check Helm version:

```bash
helm version
```

Use Case:

* Verify Helm installation.
* Check installed Helm version.

---

# Repository Management

## Add Repository

```bash
helm repo add bitnami https://charts.bitnami.com/bitnami
```

Use Case:

* Add a Helm chart repository.

---

## List Repositories

```bash
helm repo list
```

Use Case:

* View configured repositories.

---

## Update Repositories

```bash
helm repo update
```

Use Case:

* Download the latest chart information.

---

## Remove Repository

```bash
helm repo remove bitnami
```

Use Case:

* Remove a configured repository.

---

# Search Charts

## Search Repository

```bash
helm search repo nginx
```

Use Case:

* Search available charts in added repositories.

---

## Search All Versions

```bash
helm search repo nginx --versions
```

Use Case:

* View all available chart versions.

---

# Installing Charts

## Install Chart

```bash
helm install nginx bitnami/nginx
```

Use Case:

* Deploy a Helm chart.

---

## Install with Custom Release Name

```bash
helm install my-nginx bitnami/nginx
```

Use Case:

* Create a custom release name.

---

## Install with Values File

```bash
helm install nginx bitnami/nginx -f values.yaml
```

Use Case:

* Override default chart values.

---

## Install in Specific Namespace

```bash
helm install nginx bitnami/nginx -n dev
```

Use Case:

* Deploy into a namespace.

---

## Create Namespace During Installation

```bash
helm install nginx bitnami/nginx \
-n dev \
--create-namespace
```

Use Case:

* Create namespace automatically.

---

# Release Management

## List Releases

```bash
helm list
```

Use Case:

* View deployed releases.

---

## List All Namespaces

```bash
helm list -A
```

Use Case:

* View releases across the cluster.

---

## Get Release Status

```bash
helm status nginx
```

Use Case:

* Check deployment status.

---

## View Release History

```bash
helm history nginx
```

Use Case:

* View release revisions.

---

# Upgrade Releases

## Upgrade Existing Release

```bash
helm upgrade nginx bitnami/nginx
```

Use Case:

* Apply chart changes.

---

## Upgrade Using Values File

```bash
helm upgrade nginx bitnami/nginx -f values-prod.yaml
```

Use Case:

* Deploy updated configuration.

---

## Install If Not Exists

```bash
helm upgrade --install nginx bitnami/nginx
```

Use Case:

* Commonly used in CI/CD pipelines.

---

# Rollback

## Rollback to Previous Revision

```bash
helm rollback nginx 1
```

Use Case:

* Revert failed deployments.

---

## View Revision History

```bash
helm history nginx
```

Use Case:

* Find revision number before rollback.

---

# Uninstall

## Delete Release

```bash
helm uninstall nginx
```

Use Case:

* Remove application deployment.

---

## Delete from Namespace

```bash
helm uninstall nginx -n dev
```

Use Case:

* Remove deployment from specific namespace.

---

# Working with Values

## Show Default Values

```bash
helm show values bitnami/nginx
```

Use Case:

* View configurable parameters.

---

## Save Default Values

```bash
helm show values bitnami/nginx > values.yaml
```

Use Case:

* Create custom values file.

---

# Creating Charts

## Create New Chart

```bash
helm create myapp
```

Use Case:

* Generate chart template structure.

---

## Chart Structure

```text
myapp/

├── Chart.yaml
├── values.yaml
├── charts/
└── templates/
```

---

# Template Rendering

## Render Templates Locally

```bash
helm template myapp .
```

Use Case:

* Generate Kubernetes YAML without deploying.

---

## Render with Values File

```bash
helm template myapp . -f values.yaml
```

Use Case:

* Verify rendered manifests.

---

# Validation

## Lint Chart

```bash
helm lint .
```

Use Case:

* Validate chart syntax.

---

## Dry Run Installation

```bash
helm install myapp . --dry-run
```

Use Case:

* Simulate deployment.

---

## Dry Run with Debug

```bash
helm install myapp . \
--dry-run \
--debug
```

Use Case:

* Troubleshoot chart issues.

---

# Packaging Charts

## Package Chart

```bash
helm package myapp
```

Use Case:

* Create distributable chart archive.

Output:

```text
myapp-0.1.0.tgz
```

---

## Install Packaged Chart

```bash
helm install myapp myapp-0.1.0.tgz
```

Use Case:

* Deploy packaged chart.

---

# Dependency Management

## Download Dependencies

```bash
helm dependency update
```

Use Case:

* Download subcharts.

---

## Build Dependencies

```bash
helm dependency build
```

Use Case:

* Rebuild dependencies.

---

# Inspect Charts

## Show Chart Information

```bash
helm show chart bitnami/nginx
```

Use Case:

* View chart metadata.

---

## Show README

```bash
helm show readme bitnami/nginx
```

Use Case:

* View chart documentation.

---

## Show Templates

```bash
helm show all bitnami/nginx
```

Use Case:

* View complete chart details.

---

# Troubleshooting

## Get Manifest

```bash
helm get manifest nginx
```

Use Case:

* View deployed manifests.

---

## Get Values

```bash
helm get values nginx
```

Use Case:

* View user-supplied values.

---

## Get All Values

```bash
helm get values nginx --all
```

Use Case:

* View merged values.

---

## Get Notes

```bash
helm get notes nginx
```

Use Case:

* View post-install instructions.

---

# Common Production Commands

## CI/CD Deployment

```bash
helm upgrade --install app . \
-f values-prod.yaml \
-n production \
--create-namespace
```

Use Case:

* Standard production deployment.

---

## Validate Before Deployment

```bash
helm lint .
helm template .
```

Use Case:

* Pre-deployment verification.

---

## Emergency Rollback

```bash
helm history app
helm rollback app 2
```

Use Case:

* Recover from failed deployment.

---

# Helm Interview Commands

```bash
helm version
helm repo add
helm repo update
helm search repo
helm install
helm upgrade
helm rollback
helm uninstall
helm list
helm history
helm create
helm template
helm lint
helm package
helm dependency update
helm get values
helm get manifest
```

These commands cover approximately 90% of Helm usage in real-world projects and DevOps interviews.




