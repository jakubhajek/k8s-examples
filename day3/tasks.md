# Day 3 - More abstraction

![N|Solid](https://www.stratoscale.com/wp-content/uploads/Kubernetes-logo.png)

The tasks will be mainly focused on advanced scheduling, testing of your Kubernetes cluster and apps running there. 

### Task 0: Start the Minikube

<details><summary>Show me how to do it</summary>
<p>

```sh
minikube start
```

</p>
</details>

### Task 1 

- Find a way to set a label for your minikube node: disktype: ssd

- When it is done write a Pod definition with an nginx server (Day 1 definition can be reused) and try to schedule it. Does it work? Why?

- When it is done update your pod spec to choose a node with a label disktype: hdd and try to schedule your Pod. Does it work? Why?

- Update your current Pod definition to be scheduled but use nodeSelector attribute for your spec.

### Task 2

- Use the Pod spec from the Task 1 and rewrite it to benefit from nodeAffinity

- Choose one key for NodeSelectorTerms and schedule your Pod using them

- Play with required and preffered scheduling. Understand the differences and discuss it with your mentor.

### Task 3

- 3.1 Taint your node with a key: superservice, value: no, and effect NoSchedule
- 3.2 Reuse the Pod spec from Task 1 and add tolerations for this Pod to be executed on the minikube node
- 3.3 Play with other effects for your Pod and discuss them

### Task 4

- Reuse the Pod spec you have and use podAffinity that expects to be scheduled next to the Pod with a label where key: service, value: S1
- Write another spec with a Pod that has such a label as definied above
- Apply the first pod (check if it is scheduled)
- Apply the second and check if both are scheduled
- Delete all pods and apply only the second one (that doesn't have the affinity rules defined)
- Play with different podAffinity mechanisms
