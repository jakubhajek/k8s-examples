# Day 1 - Introduction to the basics

![N|Solid](https://www.stratoscale.com/wp-content/uploads/Kubernetes-logo.png)

Withing the first day of the workshop you will be working with Minikube on some very basic configurations running single-container pods, multi-container pods. You will be also configuring them in many different possible ways. 

### Task 0: Start the Minikube

<details><summary>Show me how to do it</summary>
<p>

```sh
minikube start
```

</p>
</details>

### Task 1: Starting the first pod

Help: https://v1-10.docs.kubernetes.io/docs/reference/generated/kubernetes-api/v1.10/#pod-v1-core

Run your very first nginx pod using kubectl

```sh
kubectl run --image=nginx nginx --port=80
```

Using kubectl try to find all of the nginx pods that are running in the cluster.

```sh
kubectl get pods
```

Is it really a pod or kubectl does it differently than we assumed?

```sh
kubectl get deployments
```

Delete the running pod.

```sh
kubectl delete deployment/nginx
```

Apply the pod from a static yaml file

```sh
kubectl apply -f nginx-pod.yaml
```

### Task 2: Configure your pods


### Task 3: Run multiple containers in a single pod


### Task 4: Run a job in Kubernetes


### Task 5: Working with the pods


### Task 6: Resolve the Nginx pod name to the IP address in the cluster
