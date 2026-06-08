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



