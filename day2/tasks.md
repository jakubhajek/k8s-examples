# Day 2 - More abstraction

![N|Solid](https://www.stratoscale.com/wp-content/uploads/Kubernetes-logo.png)

The second day of the workshop addresses the problems related to advanced pods scheduling and more sophisticated solutions for scheduling. You will learn how to run pods on every node, how to run more than one copy of your pod. The goal of this training is also to share informations about exposing your services to the outside world. Basics of manual and automated scaling will be covered. 

During the second part of the day we will go through namespaces and some best practices on splitting up your cluster scenarios. We will attach some policies to the namespaces and discuss some possible setups for your projects.

The last part of the day will be focus on stateful services. We will configure some services to use filesystem on the nodes and use them as a cache for the Pods. The topic of Stateful sets will covered and some of the gotchas will be shared.  

### Task 0: Start the Minikube

<details><summary>Show me how to do it</summary>
<p>

```sh
minikube start
```

</p>
</details>

### Task 1: Prepare a Replication Controller definition for 2 nginx pods.


### Task 2: Rewrite the Replication Controller definition from the Task 1 and prepare a ReplicaSet that does exactly the same thing for you.


### Task 3: Look for Kubernetes processes and try to understand how they are executed and why it can be like that. Discuss it with your mentor.

<details><summary>Show me how to do it</summary>
<p>

Hint:

```sh
kubectl get all --all-namespaces
```

</p>
</details>

### Task 4: Let's create a job that calculates a pi value to recap.


### Task 5: Create a cron job that calculates a pi value every 5 minutes.


### Task 6: Create a DaemonSet that runs on all nodes. Also on master.


### Task 7: Create a Deployment with ReplicaSet of 2 Nginx Pods


### Task 8: Search for one of the Nginx Docker image tags (on Docker Hub) and upgrade your Deployment.


### Task 9: Perform a rollback of the last deployment operation


### Task 10: Different deployment strategies

Read more about different deployment strategies. Change it for your Nginx Deployment.

Perform different deployments where you are chaning the version of Nginx image and observe how the rollout works. (Hint: You can use watch command in a differet shell)

### Task 11: Expose the running deployment.

After every expose operation remove the created service when the service setup is tested. Please discuss it with your mentor.

- 11.1 Expose your deployment (imperative) and use ClusterIP method.
- 11.2 Expose your deployment (imperative) and use NodePort method.
- 11.3 Expose your deployment (imperative) and use Loadbalancer method.

Remove the services and the deployments that were created.

### Task 12: Configure Ingress

- 12.0 Enable ingress addon in Minikube
- 12.1 Configure 3 different backends of Nginx services - service1 and service2 and the default service.
- 12.2 Configure Ingress routing:
     - first.test/ -> service1
     - second.test/service1 -> service1
     - second.test/service2 -> service2
     - * -> default

Discuss the Ingress configuration with your mentor. When everything is clear remove them and proceed with the training.

### Task 13: Configure Horizontal Pod Autoscaler

- 13.1 Enable heapster addon
- 13.2 Create a deployment with 2 Nginx Pods.
- 13.3 Configure HPA (imperative) 
- 13.4 Go through API reference and discuss how to configure HPA.

### Task 14: Namespaces

- 14.1 Create a new namespace with a name app-ns
- 14.2 Configure kubeconfig to use the new namespace. Prepare multiple contexts
- 14.3 Attach some quotas for the namespace. (i.e. request.cpu 1, requests.memory 1GB, limits.cpu 2, limits.memory 2GB)
- 14.4 Attach LimitRage for the namespace
- 14.5 Discuss some possible setups for your projects with mentor.

### Task 15: Volumes

- 15.1 Create an EmptyDir to cache some data on the node and use it for a Nginx Pod. What could be some use cases for such a setup? Where is the data stored then?
- 15.2 Use HostPath and mount some a /tmp/data directory to a Pod

### Task 16: StatefulSets

- 16.1 Apply 16.pv.yaml, 16.yaml and discuss it with your mentor.
- 16.2 Try to scale out your statefulset to 3 replicas.
