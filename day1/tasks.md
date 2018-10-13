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
kubectl apply -f solutions/nginx-pod.yaml
```

### Task 2: Configure your pods

Find in the documentation how to configure some env variables for containers defined in a pod.
There is a hint below but try to find it on your own.

Hint: https://v1-10.docs.kubernetes.io/docs/reference/generated/kubernetes-api/v1.10/#container-v1-core

Try to prepare a new yaml file nginx-pod-env.yaml that will have two env variables:
```sh
HELLO=WORLD
API=KEY
```

Discuss with other engineers the current approach. Do you think that such a solution is efficient and good enough?

Create the very first secret for the API env variable:
```sh
kubectl create secret generic api --from-literal=API=KEY
```

Create the very first ConfigMap for the HELLO env variable:
```sh
kubectl create configmap hello --from-literal=HELLO=WORLD
```

Find a kubectl command to find all secrets that are configured

Find a kubectl command to fild all configmaps that are configured

Prepare a yaml file that uses the created secret and configmap

Apply the yaml. Feel free to perform a dry-run for your command execution. (Hint: --dry-run)

Try to remove the configmap and secret. Check out what is happening with your container/pod.

Create the same configmaps and secrets but with some new values. Checkout what are the values in the running pod.

Restart the pod and checkout the value of the env variables.

### Task 3: Run multiple containers in a single pod


### Task 4: Run a job in Kubernetes


### Task 5: Working with the pods


### Task 6: Resolve the Nginx pod name to the IP address in the cluster
