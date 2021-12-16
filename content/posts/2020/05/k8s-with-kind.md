Title: kubernetes with kind
Date: 2020-05-08 17:30
Category: system administration 
Tags: kubernetes, docker 
Author: Vitor Carvalho 
Slug: kubernetes-with-kind
Summary: Kubernetes, at first sight may look overwhelming, but, trust me, it should help you get the things done very quickly once you are used to it.

To those who doesn't know Kubernetes yet, it helps operational and developers
teams to keep every thing related to containerized applications up to date and
running smoothly in your infrastructure with minimal manually intervention.

Kubernetes, at first sight may look overwhelming, but, trust me, it should
help you get the things done very quickly once you are used to it.

To start, you could look at several places at Internet. Look at this list:

* [Kubernetes docs](https://kubernetes.io/docs/home/)
* [Kubernetes the hard way](https://github.com/kelseyhightower/kubernetes-the-hard-way)
* [Kubernetes Up and Running - Dive into the future of infrastructure](https://www.amazon.com/Kubernetes-Running-Dive-Future-Infrastructure-ebook/dp/B07YP1XSZ9/ref=pd_sbsd_14_1/137-9475426-0694937?_encoding=UTF8&pd_rd_i=B07YP1XSZ9&pd_rd_r=e067f55a-8432-4ec2-a567-5716a7f33e06&pd_rd_w=LnVM9&pd_rd_wg=W7D5v&pf_rd_p=2c2d0d3b-b3c5-4110-93fa-2c1270309ac1&pf_rd_r=AH49WE30Y4BM0PXJTWQP&psc=1&refRID=AH49WE30Y4BM0PXJTWQP)

I start with the official documentation and was a great starting point, then I pass to
kubernetes the hard way and finally this awesome book listed above.

Almost every tutorial or even the official documentation propose the use of
[minikube](https://kubernetes.io/docs/tasks/tools/install-minikube/), a tool
that creates a VM (using some hypervisor as VirtualBox) and install
kubernetes in it. It is a simple way, but too heavy in my opinion.

The way I like to study was using `kind` or [kubernetes in
docker](https://kind.sigs.k8s.io/).  Who use Archlinux could install it from
AUR. At the official page, you can find instructions to install in macOS/Linux
or Windows. You must have installed in your system other tools like Docker and
kubectl (the last one isn't a dependency for kind, but you must have it to
manage the cluster created by *kind*).

## Starting using kind

After the installation you can starting creating your kubernetes cluster.
First, create a file into your $HOME named `kind-config.yaml` that holds the
kind configuration. Like every thing in the kubernetes environment, you can
create a yaml file to hold the configs.

```
# four nodes (three workers) cluster config
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
  - role: control-plane
  - role: worker
  - role: worker
  - role: worker
```

Then, run the following command

```
$ kind create cluster --config kind-config.yaml
```

The file tells the kind that we want a object of the kind Cluster and we want
to use the apiVersion v1alpha4. We also specify the number of nodes that we
want to setup in our cluster. We could also specify a image to each one of the
nodes.

After this, kind will download the base images from its docker hub and run the
images in your local environment. Check if the cluster is up by getting the
nodes available with `kind get nodes`. You must see a list of nodes created
by the kind create command.

Another important command it is the `kind get kubeconfig`, it outputs in the
current terminal the kubeconfig file, necessary to use the `kubectl` tool.

```
$ kind get kubeconfig > ~/.kube/config
```

### Next steps..

The next step we gonna see is how to interact with the new cluster. We must use
the `kubectl` tool. This is a content to another post. 

