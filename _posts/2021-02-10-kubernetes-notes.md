---
title: Kubernetes
date: 2021-02-10 21:29:08
categories:
  - Data Science

tags:
  - docker
  - kubenetes

published: false
---

This post introduces basic kubernetes concepts.

---

## Pod

Pods are the atomic unit of deployment in Kubernetes. A Pod is an abstraction of one or many co-located containers that share the same kernel namespace. Each pod gets an IP address assigned by Kubernetes that is unique in the whole Kubernetes cluster. Requests from other pods or nodes can use the pod's IP address combined with the corresponding port numberto access the individual container.

- `CMD` & `ENTRYPOINT`: define what the start process is and how to start the process.

## Reference links

1. [docker for beginners](https://docker-curriculum.com/#playing-with-busybox)