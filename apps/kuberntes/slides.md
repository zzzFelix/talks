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

# How to Blow Up a Kuberntes Cluster

## Resource management for application developers

---
layout: fact
---

# Hello 👋

My name is Felix Hoffmann

I'm a software engineer @iteratec

CKAD

---

# What are resource requests and resource limits?

- Request: Amount of memory and CPU that is guaranteed for your pod. 
- Limit: Amount of memory and CPU that your pod cannot exceed.

---

# Quality of Service

- BestEffort = No resource requests and no limits
- Burstable = Resource limit is greater than resource request
- Guaranteed = Resource limit is equal to resource request

---

# Scheduling

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
layout: two-cols
---

# Watch out for namespace limits

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
<h1> </h1>

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
- no CPU limit

---

# Don't take my word for it

https://twitter.com/thockin/status/1134193838841401345