# Install Google CLI

```
https://cloud.google.com/sdk/docs/install-sdk

# Linux
curl -O https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-cli-419.0.0-linux-x86_64.tar.gz
tar -xf google-cloud-cli-419.0.0-linux-x86_64.tar.gz
./google-cloud-sdk/install.sh
```

**Confige Google CLI**

```
./google-cloud-sdk/bin/gcloud init
```

**Kompose**

```
kompose convert -f docker-compose.yml -o kube.yml
kubectl apply -f kube.yml

# Get pods
kubectl get pods

kubectl exec mongo1-xxxxx -- mongo --eval 'rs.initiate( {
    _id : "rs0",
    members: [
        { _id: 0, host: "mongo1:xxxx" },
        { _id: 1, host: "mongo2:xxxx" },
        { _id: 2, host: "mongo3:xxxx" }
    ]
})'
```

**Install Helm**

```
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh

## Add the Jetstack Helm repository
helm repo add jetstack https://charts.jetstack.io
helm repo update

## Install the cert-manager helm chart
helm install cert-manager jetstack/cert-manager \
--namespace cert-manager \
--create-namespace \
--version v1.11.0 \
--set installCRD=true
```

**Apply deployment**

```
kubectl apply -f clusterissuer.yaml
kubectl describe clusterissuer
kubectl get ingress
```