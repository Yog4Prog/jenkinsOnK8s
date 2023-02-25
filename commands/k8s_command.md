# Setup / Link AZ subscription account
az account set --subscription 2132314234-72asda-dasa-9sad-2322003

# Get Credential into your context
## dev_lab1 -> is a cluster name
az aks get-credentials --resource-group YogFeb09_AKS --name dev_lab1

# Sample commands
# Create a namespace 
kubectl create namespace <namespace_name>

# Get all pods from a name space called jenkins
kubectl get pods -n jenkins

# List all deployments in all namespaces
kubectl get deployments --all-namespaces=true

# List all deployments in a specific namespace
# Format :kubectl get deployments --namespace <namespace-name>
kubectl get deployments --namespace kube-system

# List details about a specific deployment
# Format :kubectl describe deployment <deployment-name> --namespace <namespace-name>
kubectl describe deployment my-dep --namespace kube-system

# List pods using a specific label
# Format :kubectl get pods -l <label-key>=<label-value> --all-namespaces=true
kubectl get pods -l app=nginx --all-namespaces=true

# Get logs for all pods with a specific label
# Format :kubectl logs -l <label-key>=<label-value>
kubectl logs -l app=nginx --namespace kube-system

# ####### K8 Cluster Role Deployment ########

# Create a cluster role named "pod-reader" that allows user to perform "get", "watch" and "list" on pods
kubectl create clusterrole pod-reader --verb=get,list,watch --resource=pods

# Create a cluster role named "pod-reader" with ResourceName specified
kubectl create clusterrole pod-reader --verb=get --resource=pods --resource-name=readablepod --resource-name=anotherpod

# Create a cluster role named "foo" with API Group specified
kubectl create clusterrole foo --verb=get,list,watch --resource=rs.apps

# Create a cluster role named "foo" with SubResource specified
kubectl create clusterrole foo --verb=get,list,watch --resource=pods,pods/status

# Create a cluster role name "foo" with NonResourceURL specified
kubectl create clusterrole "foo" --verb=get --non-resource-url=/logs/*


# ###### K8 Create Deployments #######


# Create a deployment named my-dep that runs the busybox image
kubectl create deployment my-dep --image=busybox

# Create a deployment with a command
kubectl create deployment my-dep --image=busybox -- date

# Create a deployment named my-dep that runs the nginx image with 3 replicas
kubectl create deployment my-dep --image=nginx --replicas=3

# Create a deployment named my-dep that runs the busybox image and expose port 5701
kubectl create deployment my-dep --image=busybox --port=5701


# More command can be found here
https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#-strong-getting-started-strong-
