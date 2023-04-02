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

# Types of compute resources

- CPU
- Memory
- Ephemeral storage
- PID limiting
- ...

---

# Requests and limits 

- Request: Amount of memory/CPU that is guaranteed for your container. 
- Limit: Amount of memory/CPU that your container cannot exceed.

---

# Resource units

- 1 CPU unit = 1 core (physical or virtual)
  - Fractions (0.5)
  - Millicpu (100m)
  - 1000m = 1 CPU unit

<br>

- E, P, T, G, M, k
- Ei, Pi, Ti, Gi, Mi, Ki

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

<!--
- Das ist fast schon alles, was dazu in der Doku steht
- Ganz unten gibt es noch eine "Troubleshooting" Section
- Da steht z.B. was der Grund ist, wenn ein Pod nicht ge-scheduled wird
-->

---

# How Pods are scheduled 

- When you create a Pod, the scheduler selects a node for the Pod to run on
- Sum of containers' resource requests must be less than the capacity of the node
- Limits don't matter
- Node's actual resource consumption doesn't matter

<!--
- When you create a Pod, the Kubernetes scheduler selects a node for the Pod to run on
- The scheduler ensures that, for each resource type, the sum of the resource requests of the scheduled containers is less than the capacity of the node
- Note that although actual memory or CPU resource usage on nodes is very low, the scheduler still refuses to place a Pod on a node if the capacity check fails
-->

---

# What happens when a container exceeds its memory limit

- Out of memory kill (OOMKilled)

<!--
- Request/Limit = Lower/Upper bound?
- Misconception
-->
---

# How to Blow Up a Kubernetes Cluster

- Ingridients: 
	- a couple of microservices
    - Kafka
    - barely enough memory

<!--
- Funktionierte so lange gut, bis das gesamte Cluster kein Speicher mehr hatte
-->

---

# What happens when a node runs out of memory?

- Kubernetes terminates pods that exceed their memory request
- Limits don't matter

<br>

- Our Kafka pods where using ~2.8 GiB memory
	- request: 3 GiB
  - limit: 8 GiB

---

# About Kafka
- distributed event streaming
- keeps state in memory

---

# The incident

- Cluster/nodes ran out of memory
- Kafka pod was terminated (OOMKilled)
- Fewer Kafka pods had to handle more messages --> increased memory usage
- Eventually all Kafka pods were gone / constantly restarting
- Applications couldn't send messages --> increased memory usage due to backpressure
- Applications crashed due to improper error handling
- Kafka pods couldn't be scheduled anymore

---

# Lesson learned

- Do not overcommit on memory
- Memory request == memory limit
- Memory is an incompressible resource

---

# What about CPU?

- CPU is a compressible resource
- Resource management is completly different to memory

---

# What happens when a Pod exceeds its CPU limit?

- Throttling
- No termination

---
layout: quote
quote: "The Container has no upper bound on the CPU resources it can use. The Container could use all of the CPU resources available on the Node where it is running."
author: "Kubernetes Documentation"
cite: "https://kubernetes.io/docs/tasks/configure-pod-container/assign-cpu-resource/#if-you-do-not-specify-a-cpu-limit"
---

::header::
# About containers without CPU limits:

<!--
Technically true
- we don't want to be noisy neighbors
BUT
- only if other containers haven't set requests -->

---

# Requests determine CPU share

- Node: 4 CPU
- Container A: 500m
- Container B: 1000m

<br>

- Container A: 1.33 CPU
- Container B: 2.66 CPU

<!--
Wenn Container A ein Limit von 1 CPU hätte, würde er auch nur 1 CPU bekommen -->

---
layout: image-right
image: '/cpu-limits.png'
---

# Latency problems

<!--
- Completly fair scheduler
- Linux kernel
- CFS quota
- Aggressive limiting
- was gewinnen wir also von limits? Nicht viel
-->

---

# Quality of Service

- 3 classes

---

# Lesson learned

- Do not set CPU limits
- (if possible: --cpu-fs-quota=false)

<!--
- not possible for managed kubernetes
- Additional stuff to take into consideration
-->

---

# Know your resources

The amount of resources available to Pods is less than the node capacity because system daemons use a portion of the available resources. Within the Kubernetes API, each Node has a .status.allocatable field (see NodeStatus for details).

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

# Summary

- memory request == memory limit
- no CPU limits
- CFS quota can be reduced/turned off

---

# Exceptions

- Set CPU limits when you need repeatable results (e.g. performance testing)
- Not overcommiting on memory is out of budget

<!-- I have no credentials: Here's someone you want to believe -->

---

<div class="grid justify-center w-full">
<Tweet id="1134193838841401345" class="w-96" />
</div>

---
layout: fact
---

# Thank you