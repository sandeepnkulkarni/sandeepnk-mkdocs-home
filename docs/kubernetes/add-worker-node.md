---
title: 'Add worker node to Kubernetes Cluster'
---

In this tutorial, we will learn about how to add worker node to an existing Kubernetes Cluster. To learn more about how to create a single node Kubernetes cluster, please refer to section [Create single node Kubernetes cluster on Ubuntu using kubeadm on Google Cloud Platform (GCP)](single-node-k8s-ubuntu-gcp-kubeadm.md). Same steps which are mentioned below could be also performed on any Kubernetes cluster created on Ubuntu whether they are hosted on Google Cloud Platform (GCP) or not.

## Get discovery token

In case you want to initializes a Kubernetes worker node and join it to an existing Kubernetes cluster, you can use `kubeadm join` command like below:

```bash
kubeadm join 10.240.0.10:6443 --token qime8q.8mpf97fdxxxxxxxx \
    --discovery-token-ca-cert-hash sha256:8f61ee1955f194f6cc7a6888baf37447b29a86a93b214205154a8abdxxxxxxxx
```

When you configure a fresh Kubernetes cluster using `kubeadm init`, you will get the token information as part of the output itself. 

`kubeadm init` creates an initial token with a 24-hour TTL. So in case you need to generate new token to join worker node, use below command:

```bash
kubeadm token create --print-join-command
```

As we have given `--print-join-command` option, instead of printing only the token, it prints the full `kubeadm join` flag needed to join the cluster using the token.

## Run kubeadm join 

Once you have a valid token, you can run the `kubeadm join` command.

Sample output:

```text
$ sudo kubeadm join 10.240.0.10:6443 --token qime8q.8mpf97fdxxxxxxxx \
    --discovery-token-ca-cert-hash sha256:8f61ee1955f194f6cc7a6888baf37447b29a86a93b214205154a8abdxxxxxxxx
W0529 07:12:00.016796    4465 join.go:346] [preflight] WARNING: JoinControlPane.controlPlane settings will be ignored when control-plane flag is not set.
[preflight] Running pre-flight checks
[preflight] Reading configuration from the cluster...
[preflight] FYI: You can look at this config file with 'kubectl -n kube-system get cm kubeadm-config -oyaml'
[kubelet-start] Downloading configuration for the kubelet from the "kubelet-config-1.18" ConfigMap in the kube-system namespace
[kubelet-start] Writing kubelet configuration to file "/var/lib/kubelet/config.yaml"
[kubelet-start] Writing kubelet environment file with flags to file "/var/lib/kubelet/kubeadm-flags.env"
[kubelet-start] Starting the kubelet
[kubelet-start] Waiting for the kubelet to perform the TLS Bootstrap...

This node has joined the cluster:
* Certificate signing request was sent to apiserver and a response was received.
* The Kubelet was informed of the new secure connection details.

Run 'kubectl get nodes' on the control-plane to see this node join the cluster.
```
