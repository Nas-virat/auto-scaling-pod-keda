# Auto scaling pod using KEDA

This repo shows sample Autoscaling pod using Kuberenetes Even Driven Autoscaling (KEDA) 
We will use nginx-deployment as image for this deployment and scaling pod base on cron 


## What is Kuberenetes Even Driven Autoscaling (KEDA)

Kuberenete Even Driven Autoscaling (KEDA) is a open source project that 
help your scaling workload base on event that trigger such as CPU, Memory, Kafka,
Promtheus metric and etc. 
for more information about KEDA, please visit [KEDA](https://keda.sh/)

## Tools

- minikube
- kubectl

## Tutorial 

### 1. Start Kubernetes Cluster using Minikube

```
minikube start
```

### 2. Install KEDA

```
kubectl apply --server-side -f https://github.com/kedacore/keda/releases/download/v2.13.0/keda-2.13.0.yaml
```

verify the KEDA has been installed

```
kubectl get pods -n keda
```

### 3. Deploy Nginx Deployment

```
kubectl apply -f nginx-deployment.yaml
```

To check the deployment has been created, run the following command

```
kubectl get deployment
```

Let check the pod has been created

```
kubectl get pod
```

### 4. Deploy ScaledObject

ScaledObject is a custom resource that is used to define the scaling rules for a deployment.


```
kubectl apply -f scaledobject.yaml
```

To check the ScaledObject has been created, run the following command

```

kubectl get scaledobject
```


