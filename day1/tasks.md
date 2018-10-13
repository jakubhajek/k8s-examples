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

  - Run the very first container running Nginx on port 80
  - Describe such a pod configuration in a yaml file
  - Modify the pod definition and apply the changes

Run your very first nginx pod using kubectl

<details><summary>Show me how to run a pod</summary>
<p>

```sh
kubectl run --image=nginx nginx --port=80
```

</p>
</details>

Using kubectl try to find all of the nginx pods that are running in the cluster.

<details><summary>Show me how to search for pods</summary>
<p>

```sh
kubectl get pods
```

</p>
</details>

Is it really a pod or kubectl does it differently than we assumed?

<details><summary>Show me some hints</summary>
<p>

```sh
kubectl get deployments
```

</p>
</details>

Delete the running pod.

<details><summary>How to delete it? Hints</summary>
<p>

```sh
kubectl delete deployment/nginx
```

</p>
</details>

<details><summary>Show me how to apply the pod from file</summary>
<p>

```sh
kubectl apply -f nginx-pod.yaml
```

</p>
</details>

### Task 2: Configure your pods


### Task 3: Run multiple containers in a single pod


### Task 4: Run a job in Kubernetes


### Task 5: Working with the pods


### Task 6: Resolve the Nginx pod name to the IP address in the cluster
