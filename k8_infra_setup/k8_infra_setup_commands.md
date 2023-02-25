# Create Resource Group
az group create --name Yog25Feb2023 --location eastus

# Create AKS Cluster 
az aks create -g Yog25Feb2023 -n dev-lab --enable-managed-identity --node-count 1 --generate-ssh-keys
(this would take close to 5 mins)

# Install kubectl ( Incase not installed)
az aks install-cli

# Configure kubectl to connect to Kubernetes cluster
az aks get-credentials -g Yog25Feb2023 -n dev-lab 

# Create a namespace 
kubectl create namespace jenkins-agent
kubectl get namespace

# Create a Service Account
kubectl create -f service-account.yaml -n jenkins-agent

# Create a long-lived API token for Service Account
kubectl create -f secrets.yaml -n jenkins-agent

# Create Role binding to Service Account ( Role type = clusterrole admin)
kubectl create rolebinding jenkins-admin-binding --clusterrole=admin --serviceaccount=jenkins-agent:jenkins-svc -n jenkins-agent

# Get the Secret Token 
kubectl describe secret jenkins-svc-secret -n jenkins-agent

# Get Cluster URL 
kubectl config view



