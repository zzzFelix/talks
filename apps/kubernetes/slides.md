---
theme: spezi
background: https://source.unsplash.com/collection/94734566/1920x1080
class: text-center
highlighter: shiki
lineNumbers: false
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
drawings:
  persist: false
transition: slide-left
css: unocss
title: How to Blow Up a Kubernetes Cluster
---

# How to Blow Up a Kubernetes Cluster

## Resource management for application developers

---
layout: fact
---

# Hello 👋

My name is Felix

Software engineer @iteratec

---

# Requests and limits 

- Request: Amount of memory/CPU that is guaranteed for your container. 
- Limit: Amount of memory/CPU that your container cannot exceed.

---

# Requests and limits 

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: frontend
spec:
  containers:
  - name: app
    image: images.my-company.example/app:v4
    resources:
      requests:
        memory: "64Mi"
        cpu: "250m"
      limits:
        memory: "128Mi"
        cpu: "500m"
```

---

# How Pods with resource requests are scheduled 

- When you create a Pod, the Kubernetes scheduler selects a node for the Pod to run on
- The scheduler ensures that, for each resource type, the sum of the resource requests of the scheduled containers is less than the capacity of the node
- Note that although actual memory or CPU resource usage on nodes is very low, the scheduler still refuses to place a Pod on a node if the capacity check fails

---

# How to Blow Up a Kubernetes Cluster

- Ingridients: a couple of microservices, Kafka, barely enough memory

---

# Request/Limit = Lower/Upper bound?

- Kind of. But also: no
- Misconception

--- 

# What's the request for?

- Scheduling
- k8s only schedules a pod if a node has the amount of resources that the pods requests--limits don't matter
- Your pod may get exactly X amount of a requested resource but not a bit/cpu cycle more than that
---

# What do we gain from setting limits?

- Other pods get more resources
- ???

---

# What happens when a pod exceeds its resource limit?

- CPU: Throttling (even if the node has plenty of CPU cycles)
- Memory: OOMKill (even if the node has plenty of memory)

---

# What happens when a node runs out resources?

- CPU: Throttling of pods that exceed their CPU REQUEST
- Memory: OOMKill of pods that exceed their memory REQUEST
- Limits don't matter
- Who loses? Pods with low requests and high limits

---

# CPU throttling is agressive

- Slows down pods way before they reach their limits
- because of cgroups

---

# Quality of Service

- BestEffort = No resource requests and no limits
- Burstable = Resource limit is greater than resource request
- Guaranteed = Resource limit is equal to resource request

--- 

# Know your resources

The amount of resources available to Pods is less than the node capacity because system daemons use a portion of the available resources. Within the Kubernetes API, each Node has a .status.allocatable field (see NodeStatus for details).

---

# Nodes use more memory than allowed

Total limits may be over 100 percent, i.e., overcommitted.

---

# Watch out for namespace limits

Note: A LimitRange does not check the consistency of the default values it applies. This means that a default value for the limit that is set by LimitRange may be less than the request value specified for the container in the spec that a client submits to the API server. If that happens, the final Pod will not be scheduleable. See Constraints on resource limits and requests for more details.

---
layout: two-cols-header
---

::header::

# Watch out for namespace limits

::left::

```yaml
apiVersion: v1
kind: LimitRange
metadata:
  name: cpu-resource-constraint
spec:
  limits:
  - default:
      cpu: 500m
    type: Container
```

::right::

<v-click>

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: example-conflict-with-limitrange-cpu
spec:
  containers:
  - name: demo
    image: registry.k8s.io/pause:2.0
    resources:
      requests:
        cpu: 700m
```
</v-click>

---

# Recommendations

- memory request = memory limit
- no CPU limits
- rules can be enforced in an organization
- don't overcommit on memory

---

# Don't take my word for it

https://twitter.com/thockin/status/1134193838841401345
