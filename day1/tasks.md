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

Try to run two containers in the same Pod:
  - Nginx, port 80
  - Nginx, port 880

Set different env variables for both containers. Confirm that it is working as expected.

Configure one configmap and one secret. Let your containers use both of them.

Checkout how to connect from one container to another.

Propose some of the use cases for such a setup and discuss it with your mentor.

Kill the pod and check what is the status of the containers.

### Task 4: Run a job in Kubernetes

Hint: https://v1-10.docs.kubernetes.io/docs/reference/generated/kubernetes-api/v1.10/#job-v1-batch

Create a job that calculates pi to 2000 decimal points using the container with the image named perl and the following entry point to the container:

```sh
["perl",  "-Mbignum=bpi", "-wle", "print bpi(2000)"]
```

Read more about parallelism and check how it works. Discuss it with your mentor.

### Task 5: Working with the pods

List all of the pods

Get all of the details describing a multi-container pod

List all of the containers of the multi-container pod

Try to enter the shell of each container of the multi-container pod

Get logs of particular containers from the multi-container pod

Try to change the image for a running single pod with nginx by specifying a wrong value (not existing image), applying it.
Check out what happened. How many containers are running? What is their configuration? Get the details about the pod.

### Task 6: Playing with Pod Limits and Requests

```sh
minikube addons enable metrics-server
```

Add resources definition to the nginx-pod declaration with 64MB of RAM and 0.25 of CPU and deploy it to Minikube.

Install siege in the running container and try to consume more RAM than the limit defines. Check what happens.

Discuss the limits and requests with your mentor.

Try to set a very high requests value in your definition and check what happens. (higher than amount of memory in your VM)

### Task 7: Readiness and Liveness probes

Please configure a pod with command for readiness and liveness checks.
