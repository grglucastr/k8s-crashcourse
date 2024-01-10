# k8s-crashcourse
Learning the basics of Kubernetes

## Requirements
In order to deploy this application locally, it must have:

* [minikube](https://minikube.sigs.k8s.io/docs/start/) _this app enables your local PC to be a cluster_
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/) _this manages the pods inside a cluster, whether local or in the cloud_

### Basic commands

``` kubectl --help ``` 


## Deploying the services

First deploy the services that webapp is going to need, in this case: *mongodb*

### Deploy the config file
``` kubectl apply -f mongo-config.yaml ```

### Deploy the secret file
``` kubectl apply -f mongo-secret.yaml ```

### Deploy the database
``` kubectl apply -f mongo.yaml ```

## Deploy the web application
``` kubectl apply -f webapp.yaml ```


## Check all the pods and the components created in the Cluster

* To list all the services in the cluster
``` kubectl get all ``` 

* To list config map
``` kubectl get configmap ``` 

* To list secret
``` kubectl get secret ``` 

* To get details of a service
``` kubectl describe service webapp-service ``` 

* To get details of a pod
``` kubectl describe pod <<NAME OF THE POD>>``` 

* Check the logs within the pod
``` kubectl logs <<NAME OF THE POD>> ``` 

## Check if the application is accessible from the browser

* List all the services. Get the *port* of the service type *NodePort*
```kubectl get svc```

* Get the minikube ip
```minikube ip```

* Get the ip of the node
``` kubectl get node ```

* Get the ip of the node WIDE
``` kubectl get node -o wide```

Access through the web browser using the *minikube ip* and with the port from the *NodePort*