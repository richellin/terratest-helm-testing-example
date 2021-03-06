# Helm Chart Testing Example using Terratest

This repository contains the example code from the blog post ["Automated Testing for Kubernetes and Helm Charts using Terratest"](https://blog.gruntwork.io/automated-testing-for-kubernetes-and-helm-charts-using-terratest-a4ddc4e67344).

The directory structure represents a typical helm chart repository containing various charts in the `charts` directory
and the tests for those charts under the `test` directory. The `test` folder contains the corresponding terratest code
for testing each of the charts in the `charts` directory.

## Quickstart

### Prerequisites

To run the tests, you will need a working go install. See [here](https://golang.org/doc/install) for instructions on
installing go on to your platform. Make sure to use a version >=1.13.

### Kubernetes cluster

Some of the tests (specifically the integration tests) require a Kubernetes cluster to run. The easiest way to get a
Kuberenetes cluster is to use [`minikube`](https://kubernetes.io/docs/setup/minikube/), which is a local single node
installation of Kubernetes. Follow the instructions in the link to install and setup `minikube`.

Once `minikube` is installed, you will also need to deploy Tiller to run the tests based on `helm install`. To deploy
Tiller, you will first need to install the helm client. Follow the [official
guide](https://helm.sh/docs/using_helm/#installing-helm) for instructions on installing `helm`.

Once `helm` is installed, you can setup Tiller on `minikube` using `helm init`:

```
helm init --wait
```

To verify Tiller deployed correctly, use `helm version`. If the deploy was successful, you should see both the client
and server versions:

```
$ helm version
Client: &version.Version{SemVer:"v2.11.0", GitCommit:"2e55dbe1fdb5fdb96b75ff144a339489417b146b", GitTreeState:"clean"}
Server: &version.Version{SemVer:"v2.11.0", GitCommit:"2e55dbe1fdb5fdb96b75ff144a339489417b146b", GitTreeState:"clean"}
```

### Running the tests

To run the tests, first change directory to the `test` folder of this repository, and then use `go test` to run the tests:

```
cd test
go test -v .
```
