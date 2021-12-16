Title: first pods, deployments and services
Date: 2020-05-28 10:00
Category: system administration 
Tags: kubernetes, docker 
Author: Vitor Carvalho 
Slug: first-pods-deployments-and-services
Status: draft
Summary: 

I suppose that you already have the `kubectl` tool, if you don't have it,
install following the official documentation [here](https://kubernetes.io/docs/tasks/tools/install-kubectl/).
If you use Archlinux like I do, install it with `pacman -S kubectl`.

So, the kubectl or kube control, allows you to manage your kubernetes cluster
by run commands against it. The very first command that we gonna do it's to get
the current version.

```
$ kubectl version
```

If all went well, the output should be the version of the client and server
(the kubernetes cluster), if you only see the client output, go back to my
previous post where I walk you trough the process of get a functional
kubernetes cluster with kind. 

Kubernetes are composed by several components every cluster has at least
one 

The next command that we gonna see is the `config` command.
