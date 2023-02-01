# kubectl CheatSheet

## Create, delete, and manage pod

Run the nginx:alpine container in a Pod:
```
kubectl run demopod --image=nginx:alpine
```

Create a pod with a YAML file. Apply can be used for both create & update:
```
kubectl create/apply <yml-file>
```

List only pods:
```
kubectl get pods
```

List all resources:
```
kubectl get all
```

Enable pod container to be called externally (by default only accessible within k8s cluster (`external port:internal port`):
```
kubectl port-forward demopod 8080:80
```

Will cause pod to be re-created:
```
kubectl delete pod demopod
```

Delete deployment that managed the pod:
```
kubectl delete deployment demo-pod
```

Get information about pod (e.g. ip, container-image, etc.):
```
kubectl describe pod demopod
```

Jump into container of the pod:
```
kubectl exec demopod -it sh
```

---
## Create, delete, and manage ReplicaSet
Create/apply a replicaset:
```
kubectl create/apply -f myreplicaset.yml
```

Delete a replicaset:
```
kubectl get replicaset
```

Update a replicaset file:
```
kubectl replace -f myreplicaset.yml
```

Scale replicaset (without modifying the .yml file!):
```
kubectl scale -replicas=6 -f myreplicaset.yml
```

---
## Create, delete, and manage ReplicaSet
Create/apply a deployment:
```
kubectl apply -f file.deployment.yml
```

List all deployments:
```
kubectl get deployments 
```

Show all deployments and their labels:
```
kubectl get deployment --show-labels
```

List all deployments and their labels:
```
kubectl get deployment --show-labels
```

Get all deployments with a specific label:
```
kubectl get deployment -l app-nginx
```

Delete a deployment with it's name or file name with all associated pods/containers:
```
kubectl delete deployment <deployment-name> | -f file.deployment.yml
```

Scale the deployment pods to 5, either with deployment name or YAML file:
```
kubectl scale deployment <deployment-name> | -f file.deployment.yml --replicas=5
```

Get information about deployment:
```
kubectl describe deployment simple-nginx
```